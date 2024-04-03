最佳实践
===================

.. _note-order-id-label:

订单 ID 的介绍
--------------------

订单 ID 有两种，一种是系统生成的 order_id，一种是用户自定义的 order_id。系统生成的 order_id 由系统自动分配，用户自定义的 order_id 由用户自己指定。 :ref:`enum-order-id-type-label` 可以通过 order_id_type 来指定订单 ID 的类型, 来操作APP的订单。

下单/撤单时需要使用 order_id 作为本次操作的唯一标识，order_id 是一个数字字母组合，长度为 1-20 位。对于一个账户来说，order_id 是唯一的，即不同的订单具有不同的 order_id。

对于有高并发/分布式需求的用户，建议使用如 snowflake 等算法生成 order_id，以避免重复。

.. note::
    如果有重置订单 ID 的需求，可以通过 APP 联系在线客服进行申请。

这里是一种简单的 orderId 生成方法 :ref:`example-order-id-label`。

订单管理
--------------------

需要在本地建立订单数据库，用于存储订单信息。订单数据库的设计可以参考下面的表结构：

==================== ==================== ====================
字段                   类型                 备注
==================== ==================== ====================
id                    string               订单 ID
snb_order_id          string               雪盈 APP 订单 ID
order_id_type         string               订单 ID 类型
symbol                string               证券
price                 double               下单价格
quantity              double               下单数量
avg_price             double               平均成交价格
cum_quantity          double               累计成交数量
side                  string               买卖方向
order_type            string               订单类型
time_in_force         string               有效期
rth                   boolean              是否只在常规交易时间有效
status                string               订单状态
created_at            datetime             下单时间
updated_at            datetime             更新时间
==================== ==================== ====================

下单前写入DB，然后根据下单结果更新DB，推荐使用 :ref:`api-get-order-by-id-label` 接口来更新订单状态。