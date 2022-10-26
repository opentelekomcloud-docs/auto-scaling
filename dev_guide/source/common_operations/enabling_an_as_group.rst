:original_name: en-us_topic_0110252702.html

.. _en-us_topic_0110252702:

Enabling an AS Group
====================

Scenario
--------

-  An AS group consists of a collection of instances that apply to the same scenario. It is the basis for enabling or disabling AS policies and performing scaling actions.
-  Only enabled AS groups support scaling actions.

Precautions
-----------

-  If you use a token for authentication, you must call the IAM API to obtain the user's token and add **X-Auth-Token** to the request message header of ECS API you call.
-  The validity period of the token obtained from the IAM service is 24 hours. If you want to use a token for authentication, you can cache it to avoid frequently calling the IAM API.

Involved APIs
-------------

-  IAM API used to obtain the token
-  API used to query AS groups
-  API used to enable or disable an AS group

Procedure
---------

#. For details about token authentication, see `Token Authentication <https://docs.otc.t-systems.com/en-us/api/apiug/apig-en-api-180328003.html>`__.

#. Send **GET https://**\ *AS endpoint*\ **/autoscaling-api/v1/{tenant_id}/scaling_group** to obtain AS groups. Use the ID of one of the AS groups as the URI parameter **scaling_group_id** for enabling an AS group. For the response parameters of the API used to query AS groups, see section :ref:`Response Parameters for Querying AS Groups <en-us_topic_0110252693>`.

#. Send **POST https://**\ *AS endpoint*\ **/autoscaling-api/v1/{tenant_id}/scaling_group/{scaling_group_id}/action** to enable the AS group. For detailed parameters, see section "Enabling or Disabling an AS Group" in the *Auto Scaling API Reference*.

   Specify the following parameters in the request body:

   .. code-block::

      {
          "action": "resume"
      }
