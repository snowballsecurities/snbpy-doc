.. _enum-const-label:

常量定义
====================

.. _enum-currency-label:

Currency
------------

=================== ===================
Enum                 Description
=================== ===================
BASE                 基础货币
USX                  美分
CNY                  人民币
CNH                  离岸人民币
USD                  美元
SEK                  瑞典克朗
SGD                  新加坡币
TRY                  土耳其里拉
ZAR                  南非兰特
JPY                  日元
AUD                  澳元
CAD                  加币
CHF                  瑞士法郎
CNH                  人民币
HKD                  港币
NZD                  新西兰币
CZK                  捷克克朗
DKK                  丹麦克朗
HUF                  匈牙利福林
NOK                  挪威克朗
PLN                  波兰兹罗提
EUR                  欧元
GBP                  英镑
ILS                  以色列谢克尔
MXN                  墨西哥比索
RUB                  卢布
KRW                  韩元
=================== ===================


.. _enum-security-type-label:

SecurityType
-----------------

=================== ===================
Enum                 Description
=================== ===================
STK                  股票
CS                   股票(废弃)
FUT                  期货
OPT                  期权
FOP                  期货期权
WAR                  涡轮
MLEG                 期权组合
CASH                 外汇
CFD                  差价合约
CMDTY                大宗商品
FUND                 基金
IOPT                 牛熊证
BOND                 债券
BILL                 短期国债 T-Bill
ALL                  全部类型(查询条件)
=================== ===================

.. _enum-order-type-label:

OrderType
-----------------

=================== ===================
Enum                 Description
=================== ===================
LIMIT                限价单
MARKET               市价单
STOP                 止损单
STOP_LIMIT           限价止损单
TRAIL                追踪单
TRAIL_LIMIT          限价追踪单
LIMIT_ON_OPENING     开市限价单
MARKET_ON_OPENING    开市市价单
LIMIT_ON_CLOSE       闭市限价单
MARKET_ON_CLOSE      闭市市价单
LIMIT_IF_TOUCHED     触及限价单
MARKET_IF_TOUCHED    触及市价单
=================== ===================

.. _enum-order-side-label:

OrderSide
-----------------

=================== ===================
Enum                 Description
=================== ===================
BUY                  买入
SELL                 卖出
=================== ===================



.. _enum-order-status-label:

OrderStatus
-----------------

=================== =================== =================== ===================
Enum                 Description          是否终态            是否可撤单
=================== =================== =================== ===================
NO_REPORT            未报                   否                   否
WAIT_REPORT          待报                   否                   否
REPORTED             已报                   否                   是
WAIT_WITHDRAW        已报待撤                否                   否
PART_WAIT_WITHDRAW   部成待撤                否                   否
PART_WITHDRAW        部撤                   是                   否
WITHDRAWED           已撤                   是                   否
PART_CONCLUDED       部成                   否                   是
CONCLUDED            已成                   是                   否
INVALID              废单                   是                   否
EXPIRED              过期                   是                   否
=================== =================== =================== ===================

.. _enum-order-status-query-label:

OrderStatus(查询条件)
----------------------

=================== =================== 
Enum                 Description        
=================== =================== 
REPORTED            已报                  
CONCLUDED           已成                  
WITHDRAWED          已撤                  
ALL                 全部                  
=================== =================== 



.. _enum-time-in-force-label:

TimeInForce
-----------------

=================== ===================
Enum                 Description
=================== ===================
DAY                  当日有效
GTC                  撤单前有效
=================== ===================


.. _enum-order-id-type-label:

OrderIdType
-----------------

=================== ===================
Enum                 Description
=================== ===================
CLIENT               客户订单号
SNB                  雪盈单号
=================== ===================