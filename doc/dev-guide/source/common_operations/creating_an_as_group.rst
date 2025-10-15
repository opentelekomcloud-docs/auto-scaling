:original_name: en-us_topic_0110252701.html

.. _en-us_topic_0110252701:

Creating an AS Group
====================

Scenario
--------

An AS group consists of a collection of instances that apply to the same scenario. It is the basis for enabling or disabling AS policies and performing scaling actions.

Precautions
-----------

-  If you use a token for authentication, you must call the IAM API to obtain the user's token and add **X-Auth-Token** to the request message header of ECS API you call.

-  The validity period of the token obtained from the IAM service is 24 hours. If you want to use a token for authentication, you can cache it to avoid frequently calling the IAM API.

Involved APIs
-------------

-  IAM API used to obtain the token
-  API used to query VPCs
-  API used to query subnets
-  API used to query security groups
-  API used to query AS configurations
-  API used to create an AS group

Procedure
---------

#. For details about token authentication, see `Token Authentication <https://docs.otc.t-systems.com/en-us/api/apiug/apig-en-api-180328003.html>`__.

#. Send **GET https://**\ *VPC endpoint*\ **/v1/{tenant_id}/vpcs** to obtain VPCs. Use the ID of one of the obtained VPCs as parameter **vpc_id** for creating an AS group, such as **a8327883-6b07-4497-9c61-68d03ee193**. For the response parameters of the API used to query VPCs, see section :ref:`Response Parameters for Querying VPCs <en-us_topic_0110252686>`.

#. Send **GET https://**\ *VPC endpoint* **/v1/{tenant_id}/security-groups** to obtain security groups. Use one of the obtained security groups as parameter **security_groups** for creating an AS group. For the response parameters of the API used to query security groups, see section :ref:`Response Parameters for Querying Security Groups <en-us_topic_0110252688>`.

#. Send **GET https://**\ *VPC endpoint* **/v1/{tenant_id}/subnets?vpc_id=a8327883-6b07-4497-9c61-68d03ee193a** to obtain subnets in a specified VPC. For the response parameters of the API used to query subnets, see section :ref:`Response Parameters for Querying Subnets <en-us_topic_0110252687>`.

#. Send **GET https://**\ *AS endpoint*\ **/autoscaling-api/v1/{tenant_id}/scaling_configuration** to obtain AS configurations. Use the ID of one of the obtained AS configurations as parameter **scaling_configuration_id** for creating an AS group. For the response parameters of the API used to query AS configurations, see section :ref:`Response Parameters for Querying AS Configurations <en-us_topic_0110252695>`.

#. Send **POST https://**\ *AS endpoint*\ **/autoscaling-api/v1/{tenant_id}/scaling_group** to create an AS group. For detailed parameters, see section "Creating an AS Group" in the *Auto Scaling API Reference*.

   Specify the following parameters in the request body:

   .. code-block::

      {
          "scaling_group_name": "as-group-test",
          "scaling_configuration_id": "47683a91-93ee-462a-a7d7-484c006f4440",
          "desire_instance_number": 0,
          "min_instance_number": 0,
          "max_instance_number": 10,
          "cool_down_time": 300,
          "health_periodic_audit_method": "NOVA_AUDIT",
          "health_periodic_audit_time": 5,
          "instance_terminate_policy": "OLD_CONFIG_OLD_INSTANCE",
          "vpc_id": "a8327883-6b07-4497-9c61-68d03ee193a",
          "networks": [
              {
                  "id": "3cd35bca-5a10-416f-8994-f79169559870"
              }
          ],
          "security_groups": [
              {
                  "id": "23b7b999-0a30-4b48-ae8f-ee201a88a6ab"
              }
          ]
      }

   **scaling_group_id** is returned if the request is successful.
