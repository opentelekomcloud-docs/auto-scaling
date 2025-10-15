:original_name: en-us_topic_0110252700.html

.. _en-us_topic_0110252700:

Creating an AS Configuration
============================

Scenario
--------

An AS configuration specifies the specifications of the ECSs to be added to an AS group, including the ECS specifications, images, and disks. You can create an AS configuration using an existing ECS or create a new AS configuration.

Precautions
-----------

-  If you use a token for authentication, you must call the IAM API to obtain the user's token and add **X-Auth-Token** to the request message header of ECS API you call.
-  The validity period of the token obtained from the IAM service is 24 hours. If you want to use a token for authentication, you can cache it to avoid frequently calling the IAM API.

Involved APIs
-------------

-  IAM API used to obtain the token

-  API used to query specifications and expansion details about ECSs

-  API used to query images

-  API used to query SSH key pairs

-  API used to create an AS configuration

Procedure
---------

#. For details about token authentication, see `Token Authentication <https://docs.otc.t-systems.com/en-us/api/apiug/apig-en-api-180328003.html>`__.

#. Send **GET https://**\ *ECS endpoint*\ **/v1/{tenant_id}/cloudservers/flavors** to obtain the ECS specifications. For details about the response parameters of the API used to query ECS specifications, see section :ref:`Response Parameters for Querying ECSs <en-us_topic_0110252691>`.

#. Send **GET https://**\ *ECS endpoint*\ **/v2/{tenant_id}/os-keypairs** to obtain the SSH key pair. For details about the response parameters of the API used to query SSH key pairs, see section :ref:`Response Parameters for Querying SSH Key Pairs <en-us_topic_0110252690>`.

#. Send **GET https://**\ *IMS endpoint*\ **/v2/cloudimages** to obtain images. For details about the response parameters of the API used to query images, see section :ref:`Response Parameters for Querying Images <en-us_topic_0110252689>`.

#. Send **POST https://**\ *AS endpoint*\ **/autoscaling-api/v1/{tenant_id}/scaling_configuration** to create an AS configuration. For detailed parameters, see section "Creating an AS Configuration" in the *Auto Scaling API Reference*.

   Specify the following parameters in the request body:

   .. code-block::

      {
          "scaling_configuration_name": "as-config-test",
          "instance_config": {
              "flavorRef": "103", //ECS flavor ID
              "imageRef": "627a1223-2ca3-46a7-8d5f-7aef22c74ee6", //Image ID
              "disk": [
                  {
                      "size": 40,
                      "volume_type": "SATA",
                      "disk_type": "SYS"
                  }
              ],
              "key_name": "as-keypair-test" //SSH key pair
      }
      }

   **scaling_configuration_id** is returned if the request is successful.
