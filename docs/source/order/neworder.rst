.. _api-place-order-label:

下单
==========

SDK 定义
-----------------------

.. note::
    下单接口需要生成一个订单ID，请参考 :ref:`note-order-id-label`

.. code-block:: python

    @abc.abstractmethod
    def place_order(self, order_id: str, security_type: SecurityType, symbol: str, exchange: str,
                    side: OrderSide, currency: Currency, quantity: int, price: float = 0,
                    order_type: OrderType = OrderType.LIMIT, tif: TimeInForce = TimeInForce.DAY,
                    force_only_rth: bool = True, stop_price: float = 0, parent: str = None, order_id_type: OrderIdType = OrderIdType.CLIENT):
        """下单
        :param order_id: 订单 ID
        :param security_type: 证券类型，参见数据字典：SecurityType
        :param symbol: 证券代码
        :param exchange: 交易所代码
        :param side: 交易方向，参见：数据字典OrderSide
        :param currency: 币种，参见：数据字典Currency
        :param quantity: 交易数量 ，最小为1
        :param price: 限价下单必传，市价下单传任何均为0
        :param order_type: 订单类型，参见：数据字典OrderType
        :param tif: 订单有效期，参见：数据字典TimeInForce
        :param force_only_rth: 是否仅限盘中交易
        :param stop_price: 触发价
        :param parent: 父订单 ID
        :param order_id_type: 订单 ID 类型, CLIENT 默认值/代表API订单ID，SNB代表雪盈订单ID
        :return:
            {
              "msg": null,
              "result_code": "60000",
              "result_data": {
                "id": "123123123",
                "memo": "",
                "snb_order_id": "5587483178948816",
                "status": "REPORTED"
              }
            }
        """
        pass

**请求参数**

==================== ==================== ================================================================================ ==================== ====================
参数名                  类型                  描述                                                                            是否必须                默认值
==================== ==================== ================================================================================ ==================== ====================
id                   string                订单 ID，数字字母组合，1-20 位 :ref:`note-order-id-label`                            是                   无
account_id           string                账户 ID                                                                           是                   无
security_type        enum                  证券类型 :ref:`enum-security-type-label`                                           是                   无
symbol               string                证券代码                                                                           否                   空
exchange             string                市场，（使用空字符串，将自动选择最优交易所）                                             是                   无
order_type           enum                  订单类型 :ref:`enum-order-type-label`                                              是                   无
side                 enum                  买卖方向 :ref:`enum-order-side-label`                                              是                   无
currency             enum                  币种 :ref:`enum-currency-label`                                                   是                   无
quantity             int                   委托数量                                                                           是                   无
price                double                委托价格，不传默认为 0                                                               否                    0
tif                  enum                  订单有效期 :ref:`enum-time-in-force-label`                                         否                   DAY
rth                  boolean               仅限盘中交易                                                                       否                   false
order_id_type        enum                  订单 ID 类型 :ref:`enum-order-id-type-label`                                       否                   NONE
trading_hours        enum                  指定交易时段 :ref:`enum-trading-hours-label`                                       否                   NONE
==================== ==================== ================================================================================ ==================== ====================

**返回值**

==================== ==================== ================================================================================ ==================== ====================
参数名                  类型                  描述                                                                            是否必须                默认值
==================== ==================== ================================================================================ ==================== ====================
id                    string                订单 ID                                                                           是                   无
memo                  string                备注                                                                              否                   空
status                enum                  订单状态 :ref:`enum-order-status-label`                                            是                   无
snb_order_id          string                第三方订单 ID                                                                      否                   空
==================== ==================== ================================================================================ ==================== ====================

.. note::
    可以为主订单附加1或2个子订单

.. note::
    当主订单成交后，子订单会被激活对应数量,主订单与子订单数量需要一致

.. note::
    子订单成交时，同组的其他子订单会被撤销，即同一个主订单的两个子订单会互斥

.. note::
    当主订单被撤后，子订单也会被撤销

.. note::
    当使用 trading_hours 参数时，rth参数将失效。

示例
-----------------------

-  :ref:`example-place-order-1-label`
-  :ref:`example-place-order-2-label`
-  :ref:`example-place-order-3-label`