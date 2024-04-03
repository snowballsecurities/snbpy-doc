.. _api-get-balance-label:

资金管理
====================

.. code-block:: python

   @abc.abstractmethod
   def get_balance(self) -> HttpResponse:
        """
        资产查询
        :return:
            {
                "msg": null,
                "result_code": "60000",
                "result_data": {
                    "balance_detail_items": [
                    {
                        "cash": 0.0,
                        "currency": "HKD"
                    },
                    {
                        "cash": 1.011730236E7,
                        "currency": "AUD"
                    },
                    {
                        "cash": -417.8,
                        "currency": "SGD"
                    },
                    {
                        "cash": -122502.0,
                        "currency": "JPY"
                    },
                    {
                        "cash": -7655.33,
                        "currency": "MXN"
                    },
                    {
                        "cash": 3.157244242E7,
                        "currency": "USD"
                    },
                    {
                        "cash": 0.0,
                        "currency": "CNH"
                    }
                    ],
                    "cash": 3.81326952E7,
                    "currency": "USD",
                    "current_available_funds": 7.594677383E7,
                    "current_excess_liquidity": 7.783810665E7,
                    "current_initial_margin": 1.983666017E7,
                    "current_maintenance_margin": 1.794532735E7,
                    "equity_with_loan_value": 9.513816911E7,
                    "leverage": 0.61,
                    "net_liquidation_value": 9.593486421E7,
                    "previous_day_equity_with_loan_value": 9.503638136E7,
                    "securities_gross_position_value": 5.765125305E7,
                    "sma": 0.0
                }
            }
        """
        pass


**返回值**

======================================== ==================== ================================================================================ ==================== ====================
参数名                                     类型                  描述                                                                             是否必须                默认值
======================================== ==================== ================================================================================ ==================== ====================
cash                                      float                 现金                                                                              是                   无
currency                                  string                货币                                                                                   是                   无
current_available_funds                   float                 当前可用资金                                                                            是                   无
current_excess_liquidity                  float                 当前超额流动性                                                                          是                   无
current_initial_margin                    float                 当前初始保证金                                                                         是                   无
current_maintenance_margin                float                 当前维持保证金                                                                         是                   无
equity_with_loan_value                    float                 贷款价值                                                                               是                   无
leverage                                  float                 杠杆                                                                                   是                   无
net_liquidation_value                     float                 净清算价值                                                                             是                   无
previous_day_equity_with_loan_value       float                 昨日贷款价值                                                                           是                   无
securities_gross_position_value           float                 证券总头寸价值                                                                         是                   无
sma                                       float                 SMA                                                                                   是                   无
balance_detail_items                      list                  资金明细                                                                               是                   无
balance_detail_items.cash                 float                 资金明细金额                                                                           是                   无
balance_detail_items.currency             string                资金明细货币                                                                           是                   无
======================================== ==================== ================================================================================ ==================== ====================

示例
-----------------------

-  :ref:`example-get-balance-label`