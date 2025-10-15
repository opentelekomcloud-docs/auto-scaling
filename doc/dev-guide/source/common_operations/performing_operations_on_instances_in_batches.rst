:original_name: en-us_topic_0110252684.html

.. _en-us_topic_0110252684:

Performing Operations on Instances in Batches
=============================================

Scenario
--------

-  An instance is an ECS in an AS group.
-  Adding Instances to or Removing Instances from an AS Group

Precautions
-----------

-  If you use a token for authentication, you must call the IAM API to obtain the user's token and add **X-Auth-Token** to the request message header of ECS API you call.
-  The validity period of the token obtained from the IAM service is 24 hours. If you want to use a token for authentication, you can cache it to avoid frequently calling the IAM API.
-  The number of instances after the removal must be greater than or equal to the minimum number of instances allowed.
-  The number of instances after the adding must be less than or equal to the maximum number of instances allowed.
-  Instances can be added to an AS group only when the AS group is in the **INSERVICE** state and has no scaling action in progress.
-  You can remove instances from an AS group only when no scaling action is in progress.
-  The instances are removable only when they are in **INSERVICE** state.
-  To add instances to an AS group, ensure that the AZ of the instances must be within the AZ of the AS group and that the instances are in the same VPC as the AS group.

Involved APIs
-------------

-  IAM API used to obtain the token
-  API used to query AS groups
-  API used to query instances in an AS group
-  API used to query ECSs (native OpenStack API)
-  API used to perform operations on instances in batches

Procedure
---------

#. For details about token authentication, see `Token Authentication <https://docs.otc.t-systems.com/en-us/api/apiug/apig-en-api-180328003.html>`__.

2. Send **GET https://**\ *AS endpoint*\ **/autoscaling-api/v1/{tenant_id}/scaling_group** to obtain AS groups. Use the ID of one of the AS groups as the URI parameter **scaling_group_id** for querying instances in an AS group. For the response parameters of the API used to query AS groups, see section :ref:`Response Parameters for Querying AS Groups <en-us_topic_0110252693>`.

3. Send **GET https://**\ *AS endpoint*\ **/autoscaling-api/v1/{tenant_id}/scaling_group_instance/{scaling_group_id}/list** to obtain instances of a specified AS group, such as **instance_id_1** and **instance_id_2**. For the response parameters of the API used to query instances of an AS group, see section :ref:`Response Parameters for Querying Instances in an AS Group <en-us_topic_0110252696>`.

4. Send **POST https://**\ *AS endpoint*\ **/autoscaling-api/v1/{tenant_id}/scaling_group_instance/{scaling_group_id}/action** to remove instances from an AS group in batches. For detailed parameters, see section "Performing Operations on Instances in Batches" in the *Auto Scaling API Reference*.

   Specify the following parameters in the request body:

   .. code-block::

      {
          "action": "REMOVE",
          "instances_id": [
              "instance_id_1",
              "instance_id_2"
          ],
          "instance_delete": "yes"
      }
