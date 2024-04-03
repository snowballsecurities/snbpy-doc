API 介绍
====================

请参照 :ref:`account-label` 准备账户和 :ref:`install-label` 安装 SDK

更多详情请使用 help(TradeInterface) 方法获取文档

.. code-block:: python

    from snbpy.snb_api_client import TradeInterface
    help(TradeInterface)

方法列表
-----------------

============================================ ============================================== ================================================
方法名                                         描述                                            文档连接
============================================ ============================================== ================================================
login                                         访问API生成一个新 token，不会使用缓存               :ref:`api-login-label`
place_order                                   下单                                            :ref:`api-place-order-label`
get_order_by_id                               订单查询，单条                                    :ref:`api-get-order-by-id-label`
get_order_list                                订单查询，批量                                    :ref:`api-get-order-list-label`
cancel_order                                  撤销订单                                         :ref:`api-cancel-order-label`
get_transaction_list                          成交查询                                         :ref:`api-get-transaction-label`
get_balance                                   资产查询                                         :ref:`api-get-balance-label`
get_position_list                             持仓查询                                         :ref:`api-get-position-label`
============================================ ============================================== ================================================


常量订单参考 :ref:`enum-const-label`