.. _example-cancel-order-label:

撤单
===========

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
        order_id = "123456"
        cancel_order =client.cancel_order(gen_order_id(), order_id)
        self.assertIsNotNone(cancel_order)
        self.assertTrue(cancel_order.succeed())