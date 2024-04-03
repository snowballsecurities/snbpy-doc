.. _example-get-transaction-label:

查询成交订单
=========================

.. code-block:: python

    from snbpy.common.domain.snb_config import SnbConfig
    from snbpy.snb_api_client import SnbHttpClient
    if __name__ == '__main__':
        config = SnbConfig()
        config.account = "DU1234567"
        config.key = '123456'
        config.sign_type = 'None'
        config.snb_server ='sandbox.snbsecurities.com'
        config.snb_port = '443'
        config.timeout = 1000
        config.schema = 'https'
    
        client = SnbHttpClient(config)
        client.login()
        transaction_response = client.get_transaction_list()
