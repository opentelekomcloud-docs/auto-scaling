:original_name: en-us_topic_0110252703.html

.. _en-us_topic_0110252703:

Creating an AS Policy
=====================

Scenario
--------

An AS policy specifies a condition for triggering a scaling action. When the trigger condition is met, a scaling action occurs.

Precautions
-----------

-  If you use a token for authentication, you must call the IAM API to obtain the user's token and add **X-Auth-Token** to the request message header of ECS API you call.
-  The validity period of the token obtained from the IAM service is 24 hours. If you want to use a token for authentication, you can cache it to avoid frequently calling the IAM API.

Involved APIs
-------------

-  IAM API used to obtain the token
-  API used to query AS groups
-  API used to create an AS policy

Procedure
---------

#. For details about token authentication, see `Token Authentication <https://docs.otc.t-systems.com/en-us/api/apiug/apig-en-api-180328003.html>`__.

#. Send **GET https://**\ *AS endpoint*\ **/autoscaling-api/v1/{tenant_id}/scaling_group** to obtain AS groups. Use the ID of one of the AS groups as parameter **scaling_group_id** for creating an AS policy. For the response parameters of the API used to query AS groups, see section :ref:`Response Parameters for Querying AS Groups <en-us_topic_0110252693>`.

#. Send **POST https://**\ *AS endpoint*\ **/autoscaling-api/v1/{tenant_id}/scaling_policy** to create an AS policy, such as a periodic policy which is executed on Sunday, Tuesday, and Thursday. For detailed parameters, see section "Creating an AS Policy" in the *Auto Scaling API Reference*.

   Specify the following parameters in the request body:

   .. code-block::

      {
          "scaling_policy_name": "as-policy-test",
          "scaling_policy_action": {
              "operation": "ADD",
              "instance_number": 1
          },
          "cool_down_time": 900,
          "scheduled_policy": {
              "launch_time": "16:00",
              "recurrence_type": "Weekly",
              "recurrence_value": "1,3,5",
              "start_time": "2018-05-04T03:34Z",
              "end_time": "2018-12-27T03:34Z"
          },
          "scaling_policy_type": "RECURRENCE",
          "scaling_group_id": "5bc3aa02-b83e-454c-aba1-4d2095c68f8b"
      }

   **scaling_policy_id** is returned if the request is successful.
