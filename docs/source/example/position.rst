.. _example-get-position-label:

持仓查询
==========

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
        balance_response = client.get_position_list("STK,OPT,WAR,FUT")
