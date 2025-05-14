.. _example-place-order-1-label:

下单 场景 证券类型
====================================================================================

美股/港股/涡轮/牛熊证/美股期权/期货/外汇/CFD/现货


准备
------------------------------------------------------------------------------------

.. code-block:: python

    import time
    from threading import RLock
    
    from snbpy.common.constant.snb_constant import SecurityType, OrderSide, Currency, OrderType, TimeInForce
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

    if __name__ == '__main__':
        agent = SnbAgent()
        order_id = agent.gen_order_id()
        order_result = agent.client.place_order(order_id, SecurityType.STK, "AAPL", "", OrderSide.BUY, Currency.USD, 1, 180, OrderType.LIMIT, TimeInForce.DAY, True)
        print(order_result.result_str)
        if order_result.succeed():
            print("place order succeed")
            cancel_result = agent.client.cancel_order(agent.gen_order_id(), order_id)
            print(cancel_result.result_str)
        else:
            print("place order failed")

美股
------------------------------------------------------------------------------------

.. code-block:: python

    order_result = agent.client.place_order(order_id, SecurityType.STK, "AAPL", "", OrderSide.BUY, Currency.USD, 1, 180, OrderType.LIMIT, TimeInForce.DAY, True)


港股
------------------------------------------------------------------------------------

.. code-block:: python

    order_result = agent.client.place_order(order_id, SecurityType.STK, "00700", "", OrderSide.BUY, Currency.USD, 100, 180, OrderType.LIMIT, TimeInForce.DAY, True)

涡轮
------------------------------------------------------------------------------------

.. code-block:: python

    order_result = agent.client.place_order(order_id, SecurityType.WAR, "23929", "", OrderSide.BUY, Currency.HKD, 10000, 0.10, OrderType.LIMIT, TimeInForce.DAY, True)

牛熊证
------------------------------------------------------------------------------------

.. code-block:: python

    order_result = agent.client.place_order(order_id, SecurityType.IOPT, "52237", "", OrderSide.BUY, Currency.HKD, 10000, 0.040, OrderType.LIMIT, TimeInForce.DAY, True)

美股期权
------------------------------------------------------------------------------------

.. code-block:: python

    order_result = agent.client.place_order(order_id, SecurityType.OPT, "AAPL240405C00170000", "", OrderSide.BUY, Currency.USD, 1, 0.9, OrderType.LIMIT, TimeInForce.DAY, True)

期货
------------------------------------------------------------------------------------

.. code-block:: python

    order_result = agent.client.place_order(order_id, SecurityType.FUT, "6J2406", "CME", OrderSide.BUY, Currency.USD, 1, 0.006, OrderType.LIMIT, TimeInForce.DAY, True)

CFD
------------------------------------------------------------------------------------

.. code-block:: python

    order_result = agent.client.place_order(order_id, SecurityType.CFD, "USD.HKD", "", OrderSide.BUY, Currency.USD, 1, 7, OrderType.LIMIT, TimeInForce.DAY, True)

现货黄金
------------------------------------------------------------------------------------

.. code-block:: python

    order_result = agent.client.place_order(order_id, SecurityType.CMDTY, "XAUUSD", "", OrderSide.BUY, Currency.USD, 1, 1800, OrderType.LIMIT, TimeInForce.DAY, True)


CME:FOP
------------------------------------------------------------------------------------

.. code-block:: python

    order_result =  self.client.place_order(order_id, SecurityType.FOP , "NQ    250919P20000000", "GLOBEX", OrderSide.BUY, Currency.USD, qty, price, OrderType.LIMIT, TimeInForce.DAY, True)

    