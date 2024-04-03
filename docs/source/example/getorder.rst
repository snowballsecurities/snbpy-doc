.. _example-get-order-by-id-label:

订单查询(单条)
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
        order_response = client.get_order_by_id("12312312321")

.. _example-get-order-list-label:

订单查询
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
        order_response = client.get_order_list(security_type='STK', status='ALL')
