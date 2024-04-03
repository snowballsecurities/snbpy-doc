.. _api-get-transaction-label:

历史成交
====================

.. code-block:: python

   @abc.abstractmethod

    @abc.abstractmethod
    def get_transaction_list(self, page=1, size=10, side=None, order_time_min=None, order_time_max=None):
        """
        :param page: 页码
        :param size: 每页大小
        :param side: 交易方向
        :param order_time_min: 最小下单时间 毫秒时间戳
        :param order_time_max: 最大下单时间 毫秒时间戳
        :return:
            {
                "msg": null,
                "result_code": "60000",
                "result_data": {
                    "count": 155,
                    "items": [
                    {
                        "account_id": "DU123456",
                        "currency": "USD",
                        "exchange": "USEX",
                        "id": "",
                        "order_price": 18547.75,
                        "order_quantity": 1.0,
                        "order_time": 1711432599000,
                        "order_type": "LIMIT",
                        "price": 18547.75,
                        "quantity": 1.0,
                        "rth": false,
                        "security_type": "FUT",
                        "side": "BUY",
                        "status": "CONCLUDED",
                        "symbol": "MNQ2406",
                        "tif": "DAY",
                        "trade_time": 1711432771000
                    },
                    {
                        "account_id": "DU123456",
                        "currency": "USD",
                        "exchange": "USEX",
                        "id": "",
                        "order_price": 0.0066,
                        "order_quantity": 1.0,
                        "order_time": 1711331475000,
                        "order_type": "LIMIT",
                        "price": 0.0066,
                        "quantity": 1.0,
                        "rth": false,
                        "security_type": "FUT",
                        "side": "BUY",
                        "status": "CONCLUDED",
                        "symbol": "6J2404",
                        "tif": "DAY",
                        "trade_time": 1711331530000
                    }
                    ],
                    "page": 1,
                    "size": 2
                }
            }
        """
        pass

**请求参数**

==================== ==================== ================================================================================ ==================== ====================
参数名                  类型                  描述                                                                            是否必须                默认值
==================== ==================== ================================================================================ ==================== ====================
page                 int                   页码                                                                              否                     1
size                 int                   每页大小                                                                           否                     10
side                 str                   交易方向                                                                           否                     None
order_time_min       int                   最小下单时间 毫秒时间戳                                                              否                     None
order_time_max       int                   最大下单时间 毫秒时间戳                                                              否                     None
==================== ==================== ================================================================================ ==================== ====================

**返回值**

======================================== ==================== ================================================================================ ==================== ====================
参数名                                     类型                  描述                                                                             是否必须                默认值
======================================== ==================== ================================================================================ ==================== ====================
account_id                                string                账户ID                                                                          是
currency                                  string                货币类型  :ref:`enum-currency-label`                                            是
exchange                                  string                交易所                                                                           是
id                                        string                订单ID                                                                           是
order_price                               float                 下单价格                                                                         是
order_quantity                            int                   下单数量                                                                         是
order_time                                int                   下单时间戳                                                                       是
order_type                                string                订单类型 :ref:`enum-order-type-label`                                           是
price                                     float                 价格                                                                            是
quantity                                  int                   数量                                                                            是
rth                                       bool                  是否只在交易时间内有效                                                            是
security_type                             string                证券类型  :ref:`enum-security-type-label`                                            是
side                                      string                买卖方向 :ref:`enum-order-side-label`                                           是
status                                    string                订单状态  :ref:`enum-order-status-label`                                          是
symbol                                    string                证券代码                                                                        是
tif                                       string                订单有效期   :ref:`enum-time-in-force-label`                                        是
trade_time                                int                   成交时间戳                                                                       是
======================================== ==================== ================================================================================ ==================== ====================

示例
-----------------------

-  :ref:`example-get-transaction-label`