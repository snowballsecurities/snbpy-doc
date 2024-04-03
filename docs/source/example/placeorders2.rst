.. _example-place-order-2-label:

下单 场景 订单类型
====================================================================================

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

限价单
------------------------------------------------------------------------------------

.. code-block:: python

    order_result = agent.client.place_order(order_id, SecurityType.STK, "AAPL", "", OrderSide.BUY, Currency.USD, 1, 180, OrderType.LIMIT, TimeInForce.DAY, True)

市价单
------------------------------------------------------------------------------------

.. code-block:: python

    order_result = agent.client.place_order(order_id, SecurityType.STK, "AAPL", "", OrderSide.BUY, Currency.USD, 1, 0, OrderType.MARKET, TimeInForce.DAY, True)

止损单
------------------------------------------------------------------------------------
    
.. code-block:: python

    order_result = agent.client.place_order(order_id, SecurityType.STK, "AAPL", "", OrderSide.SELL, Currency.USD,1,0, OrderType.STOP, TimeInForce.DAY, True, stop_price=180)

止损限价单
------------------------------------------------------------------------------------

.. code-block:: python

    order_result = agent.client.place_order(order_id, SecurityType.STK, "AAPL", "", OrderSide.SELL, Currency.USD,1,179, OrderType.STOP, TimeInForce.DAY, True, stop_price=180)
    
止盈单
------------------------------------------------------------------------------------

.. code-block:: python

    order_result = agent.client.place_order(order_id, SecurityType.STK, "AAPL", "", OrderSide.SELL, Currency.USD,1,0, OrderType.MARKET_IF_TOUCHED, TimeInForce.DAY, True, stop_price=200)

止盈限价单
------------------------------------------------------------------------------------

.. code-block:: python

    order_result = agent.client.place_order(order_id, SecurityType.STK, "AAPL", "", OrderSide.SELL, Currency.USD,1,199, OrderType.LIMIT_IF_TOUCHED, TimeInForce.DAY, True, stop_price=200)