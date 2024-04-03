.. _api-get-order-list-label:

订单查询（列表）
====================

.. code-block:: python


    @abc.abstractmethod
    def get_order_list(self, page: int = 1, size: int = 10, status: str = None,
                       security_type: str = "STK,OPT,WAR,IOPT,FUT") -> HttpResponse:
        """
        :param page: 页码
        :param size: 每页大小
        :param status: 订单状态
        :param security_type: 证券类型，多个类型用逗号分隔，参见数据字典：SecurityType
        :return:
            {
                "msg": null,
                "result_code": "60000",
                "result_data": {
                    "count": 3,
                    "items": [
                    {
                        "account_id": "DU123456",
                        "average_price": 0.0,
                        "children": null,
                        "currency": "HKD",
                        "exchange": "HKEX",
                        "filled_quantity": 0,
                        "group_id": null,
                        "id": "",
                        "memo": "",
                        "order_time": 1711419658000,
                        "order_type": "STOP_LIMIT",
                        "parent": null,
                        "price": 100.0,
                        "quantity": 100,
                        "rth": true,
                        "secondary_order_id": "004c4d6b.000130f7.66010d09.0002",
                        "security_type": "STK",
                        "side": "BUY",
                        "snb_order_id": "5588468353849584",
                        "status": "WITHDRAWED",
                        "stop_price": null,
                        "symbol": "00700",
                        "tif": "DAY"
                    },
                    {
                        "account_id": "DU123456",
                        "average_price": 0.0,
                        "children": null,
                        "currency": "HKD",
                        "exchange": "HKEX",
                        "filled_quantity": 0,
                        "group_id": null,
                        "id": "1711419657579",
                        "memo": "",
                        "order_time": 1711419658000,
                        "order_type": "STOP_LIMIT",
                        "parent": null,
                        "price": 100.0,
                        "quantity": 100,
                        "rth": true,
                        "secondary_order_id": "004c4d6b.000130f7.66010d09.0002",
                        "security_type": "STK",
                        "side": "BUY",
                        "snb_order_id": "5588456391694560",
                        "status": "WITHDRAWED",
                        "stop_price": null,
                        "symbol": "00700",
                        "tif": "DAY"
                    },
                    {
                        "account_id": "DU123456",
                        "average_price": 0.0,
                        "children": null,
                        "currency": "HKD",
                        "exchange": "HKEX",
                        "filled_quantity": 0,
                        "group_id": null,
                        "id": "1711361650250",
                        "memo": "委托单已过期",
                        "order_time": 1711361650000,
                        "order_type": "STOP_LIMIT",
                        "parent": null,
                        "price": 100.0,
                        "quantity": 100,
                        "rth": true,
                        "secondary_order_id": "004c4d6b.000130f7.6600fbf3.0001",
                        "security_type": "STK",
                        "side": "BUY",
                        "snb_order_id": "5587483178948816",
                        "status": "EXPIRED",
                        "stop_price": null,
                        "symbol": "00700",
                        "tif": "DAY"
                    }
                    ],
                    "page": 1,
                    "size": 10
                }
            }
        """
        pass


**请求参数**

==================== ==================== ================================================================================ ==================== ========================================
参数名                  类型                  描述                                                                            是否必须                默认值
==================== ==================== ================================================================================ ==================== ========================================
page                  int                   页码                                                                            否                    1
size                  int                   每页大小                                                                         否                    10
status                string                订单状态 :ref:`enum-order-status-query-label`                                    否
security_type         string                证券类型，多个类型用逗号分隔，参见数据字典：:ref:`enum-security-type-label`            否                    STK,OPT,WAR,IOPT,FUT
==================== ==================== ================================================================================ ==================== ========================================

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

-  :ref:`example-get-order-list-label`