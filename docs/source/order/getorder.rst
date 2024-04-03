.. _api-get-order-by-id-label:

订单查询（单条）
====================

.. code-block:: python

    @abc.abstractmethod
    def get_order_by_id(self, order_id: str):
        """
        :param order_id: 订单 ID
        :return:
            {
                "msg": null,
                "result_code": "60000",
                "result_data": {
                    "account_id": "DU1234567",
                    "average_price": 0.0,
                    "children": null,
                    "currency": "HKD",
                    "exchange": "HKEX",
                    "filled_quantity": 0,
                    "group_id": null,
                    "id": "1757579",
                    "memo": "",
                    "order_time": 1611419658000,
                    "order_type": "STOP_LIMIT",
                    "parent": null,
                    "price": 100.0,
                    "quantity": 100,
                    "rth": true,
                    "secondary_order_id": "004c4dab.000130a7.6601ad09.0002",
                    "security_type": "STK",
                    "side": "BUY",
                    "snb_order_id": "1234567",
                    "status": "WITHDRAWED",
                    "stop_price": null,
                    "symbol": "00700",
                    "tif": "DAY"
                }
            }
        """
        pass


**请求参数**

==================== ==================== ================================================================================ ==================== ====================
参数名                  类型                  描述                                                                            是否必须                默认值
==================== ==================== ================================================================================ ==================== ====================
order_id               string              订单ID                                                                           是
==================== ==================== ================================================================================ ==================== ====================

**返回值**

======================================== ==================== ================================================================================ ==================== ====================
参数名                                     类型                  描述                                                                             是否必须                默认值
======================================== ==================== ================================================================================ ==================== ====================
account_id                                string                账户ID                                                                          是
average_price                             float                 平均价格                                                                         是
children                                  list                  子订单列表                                                                       否
currency                                  string                货币类型  :ref:`enum-currency-label`                                            是
exchange                                  string                交易所                                                                           是
filled_quantity                           int                   已成交数量                                                                        是
group_id                                  string                组ID                                                                             否
id                                        string                订单ID                                                                           是
memo                                      string                异常信息                                                                          否
order_time                                int                   下单时间戳                                                                         是
order_type                                string                订单类型 :ref:`enum-order-type-label`                                              是
parent                                    string                父订单ID                                                                           是
price                                     float                 价格                                                                              是
quantity                                  int                   数量                                                                              是
rth                                       bool                  是否只在交易时间内有效                                                               是
secondary_order_id                        string                第三方订单ID                                                                       是
security_type                             string                证券类型  :ref:`enum-security-type-label`                                               是
side                                      string                买卖方向 :ref:`enum-order-side-label`                                              是
snb_order_id                              string                第三方订单ID                                                                       是
status                                    string                订单状态  :ref:`enum-order-status-label`                                           是
stop_price                                float                 触发价格                                                                           是
symbol                                    string                证券代码                                                                           是
tif                                       string                订单有效期   :ref:`enum-time-in-force-label`                                         是
======================================== ==================== ================================================================================ ==================== ====================

示例
-----------------------

-  :ref:`example-get-order-by-id-label`