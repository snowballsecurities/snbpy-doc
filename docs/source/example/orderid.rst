.. _example-order-id-label:

一种简单的 orderId 生成策略
==================================================

以下是一种简单的 order id 生成策略，可以满足单机秒级峰值并发量小于 1000 的情况。

.. code-block:: python

    import time
    from threading import RLock
    from snbpy.common.domain.snb_config import SnbConfig
    from snbpy.snb_api_client import SnbHttpClient

    class SnbAgent():
        def __init__(self):
            self.config = SnbConfig()
            # 替换掉这里
            self.config.account = "DU1234567"
            # 替换掉这里
            self.config.key = "1234567"
            self.config.sign_type = 'None'
            self.config.snb_server = 'sandbox.snbsecurities.com'
            self.config.snb_port = '443'
            self.config.timeout = 1000
            self.config.schema = 'https'
            self.client = SnbHttpClient(self.config)
            self.last_ts = 0
            self.sq = 0
            self.lock = RLock()
            self.client.login()
    
        def gen_order_id(self):
            with self.lock:
                t = int(time.time())
                if self.last_ts == t:
                    if self.sq == 999:
                        raise Exception("too many request in one second")
                    else:
                        self.sq += 1
                else:
                    self.last_ts = t
                    self.sq = 0
                return "{}{:03}".format(self.last_ts, self.sq)
    
    