:original_name: as_06_0405.html

.. _as_06_0405:

Querying AS Policies Bound to an AS Group
=========================================

Function
--------

This API is used to query AS policies based on search criteria. The results are displayed by page.

-  Search criteria can be the AS policy name, policy type, policy ID, start line number, and number of records.
-  If no search criteria are specified, a maximum of 20 AS policies for a specified AS group can be queried for a tenant by default.

URI
---

GET /autoscaling-api/v1/{project_id}/scaling_policy/{scaling_group_id}/list

.. note::

   You can type the question mark (?) and ampersand (&) at the end of the URI to define multiple search criteria. AS policies can be searched by all optional parameters in the following table. For details, see the example request.

.. table:: **Table 1** Parameter description

   +---------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------+
   | Parameter           | Mandatory       | Type            | Description                                                                                         |
   +=====================+=================+=================+=====================================================================================================+
   | project_id          | Yes             | String          | Specifies the project ID.                                                                           |
   +---------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------+
   | scaling_group_id    | Yes             | String          | Specifies the AS group ID.                                                                          |
   +---------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------+
   | scaling_policy_name | No              | String          | Specifies the AS policy name.                                                                       |
   |                     |                 |                 |                                                                                                     |
   |                     |                 |                 | Supports fuzzy search.                                                                              |
   +---------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------+
   | scaling_policy_type | No              | String          | Specifies the AS policy type.                                                                       |
   |                     |                 |                 |                                                                                                     |
   |                     |                 |                 | -  **ALARM**: alarm policy                                                                          |
   |                     |                 |                 | -  **SCHEDULED**: scheduled policy                                                                  |
   |                     |                 |                 | -  **RECURRENCE**: periodic policy                                                                  |
   +---------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------+
   | scaling_policy_id   | No              | String          | Specifies the AS policy ID.                                                                         |
   +---------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------+
   | start_number        | No              | Integer         | Specifies the start line number. The default value is **0**. The minimum parameter value is **0**.  |
   +---------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------+
   | limit               | No              | Integer         | Specifies the number of query records. The default value is **20**. The value ranges from 0 to 100. |
   +---------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------+

Request Message
---------------

-  Request parameters

   None

-  Example request

   This example shows how to query scheduled AS policies named **as-policy-test** in the AS group with ID **e5d27f5c-dd76-4a61-b4bc-a67c5686719a**.

   .. code-block:: text

      GET https://{Endpoint}/autoscaling-api/v1/{project_id}/scaling_policy/e5d27f5c-dd76-4a61-b4bc-a67c5686719a/list?scaling_policy_name=as-policy-test&scaling_policy_type=SCHEDULED

Response Message
----------------

-  Response parameters

   .. table:: **Table 2** Response parameters

      +------------------+--------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
      | Parameter        | Type                                                                                             | Description                                                                                                          |
      +==================+==================================================================================================+======================================================================================================================+
      | total_number     | Integer                                                                                          | Specifies the total number of query records.                                                                         |
      +------------------+--------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
      | start_number     | Integer                                                                                          | Specifies the start line number.                                                                                     |
      +------------------+--------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
      | limit            | Integer                                                                                          | Specifies the maximum number of resources to be queried.                                                             |
      +------------------+--------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
      | scaling_policies | Array of :ref:`scaling_policies <as_06_0405__en-us_topic_0130755740_table5036780310489>` objects | Specifies scaling policies. For details, see :ref:`Table 3 <as_06_0405__en-us_topic_0130755740_table5036780310489>`. |
      +------------------+--------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+

   .. _as_06_0405__en-us_topic_0130755740_table5036780310489:

   .. table:: **Table 3** **scaling_policies** field description

      +-----------------------+------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                                                                                                       | Description                                                                                                                                                                                                                                           |
      +=======================+============================================================================================================+=======================================================================================================================================================================================================================================================+
      | scaling_group_id      | String                                                                                                     | Specifies the AS group ID.                                                                                                                                                                                                                            |
      +-----------------------+------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | scaling_policy_name   | String                                                                                                     | Specifies the AS policy name.                                                                                                                                                                                                                         |
      +-----------------------+------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | scaling_policy_id     | String                                                                                                     | Specifies the AS policy ID.                                                                                                                                                                                                                           |
      +-----------------------+------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | policy_status         | String                                                                                                     | Specifies the AS policy status.                                                                                                                                                                                                                       |
      |                       |                                                                                                            |                                                                                                                                                                                                                                                       |
      |                       |                                                                                                            | -  **INSERVICE**: The AS policy is enabled.                                                                                                                                                                                                           |
      |                       |                                                                                                            | -  **PAUSED**: The AS policy is disabled.                                                                                                                                                                                                             |
      |                       |                                                                                                            | -  **EXECUTING**: The AS policy is being executed.                                                                                                                                                                                                    |
      +-----------------------+------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | scaling_policy_type   | String                                                                                                     | Specifies the AS policy type.                                                                                                                                                                                                                         |
      |                       |                                                                                                            |                                                                                                                                                                                                                                                       |
      |                       |                                                                                                            | -  **ALARM**: indicates that the scaling action is triggered by an alarm. A value is returned for **alarm_id**, and no value is returned for **scheduled_policy**.                                                                                    |
      |                       |                                                                                                            | -  **SCHEDULED**: indicates that the scaling action is triggered as scheduled. A value is returned for **scheduled_policy**, and no value is returned for **alarm_id**, **recurrence_type**, **recurrence_value**, **start_time**, or **end_time**.   |
      |                       |                                                                                                            | -  **RECURRENCE**: indicates that the scaling action is triggered periodically. Values are returned for **scheduled_policy**, **recurrence_type**, **recurrence_value**, **start_time**, and **end_time**, and no value is returned for **alarm_id**. |
      +-----------------------+------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | alarm_id              | String                                                                                                     | Specifies the alarm ID.                                                                                                                                                                                                                               |
      +-----------------------+------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | scheduled_policy      | :ref:`scheduled_policy <as_06_0405__en-us_topic_0130755740_t759e6d15d244474e8f286185ede143fb>` object      | Specifies the periodic or scheduled AS policy. For details, see :ref:`Table 4 <as_06_0405__en-us_topic_0130755740_t759e6d15d244474e8f286185ede143fb>`.                                                                                                |
      +-----------------------+------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | scaling_policy_action | :ref:`scaling_policy_action <as_06_0405__en-us_topic_0130755740_t34390832ab524bcc8123c0f9a056064f>` object | Specifies the scaling action of the AS policy. For details, see :ref:`Table 5 <as_06_0405__en-us_topic_0130755740_t34390832ab524bcc8123c0f9a056064f>`.                                                                                                |
      +-----------------------+------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | cool_down_time        | Integer                                                                                                    | Specifies the cooldown period (s).                                                                                                                                                                                                                    |
      +-----------------------+------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | create_time           | String                                                                                                     | Specifies the time when an AS policy was created. The time format complies with UTC.                                                                                                                                                                  |
      +-----------------------+------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _as_06_0405__en-us_topic_0130755740_t759e6d15d244474e8f286185ede143fb:

   .. table:: **Table 4** **scheduled_policy** field description

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                                                                                                   |
      +=======================+=======================+===============================================================================================================================================================================================+
      | launch_time           | String                | Specifies the time when the scaling action is triggered. The time format complies with UTC.                                                                                                   |
      |                       |                       |                                                                                                                                                                                               |
      |                       |                       | -  If **scaling_policy_type** is set to **SCHEDULED**, the time format is **YYYY-MM-DDThh:mmZ**.                                                                                              |
      |                       |                       | -  If **scaling_policy_type** is set to **RECURRENCE**, the time format is **hh:mm**.                                                                                                         |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | recurrence_type       | String                | Specifies the type of a periodically triggered scaling action.                                                                                                                                |
      |                       |                       |                                                                                                                                                                                               |
      |                       |                       | -  **Daily**: indicates that the scaling action is triggered once a day.                                                                                                                      |
      |                       |                       | -  **Weekly**: indicates that the scaling action is triggered once a week.                                                                                                                    |
      |                       |                       | -  **Monthly**: indicates that the scaling action is triggered once a month.                                                                                                                  |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | recurrence_value      | String                | Specifies the frequency at which scaling actions are triggered.                                                                                                                               |
      |                       |                       |                                                                                                                                                                                               |
      |                       |                       | -  If **recurrence_type** is set to **Daily**, the value is **null**, indicating that the scaling action is triggered once a day.                                                             |
      |                       |                       | -  If **recurrence_type** is set to **Weekly**, the value ranges from **1** (Sunday) to **7** (Saturday). The digits refer to dates in each week and separated by a comma, such as **1,3,5**. |
      |                       |                       | -  If **recurrence_type** is set to **Monthly**, the value ranges from **1** to **31**. The digits refer to the dates in each month and separated by a comma, such as **1,10,13,28**.         |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | start_time            | String                | Specifies the start time of the scaling action triggered periodically. The time format complies with UTC.                                                                                     |
      |                       |                       |                                                                                                                                                                                               |
      |                       |                       | The time format is **YYYY-MM-DDThh:mmZ**.                                                                                                                                                     |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | end_time              | String                | Specifies the end time of the scaling action triggered periodically. The time format complies with UTC.                                                                                       |
      |                       |                       |                                                                                                                                                                                               |
      |                       |                       | The time format is **YYYY-MM-DDThh:mmZ**.                                                                                                                                                     |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _as_06_0405__en-us_topic_0130755740_t34390832ab524bcc8123c0f9a056064f:

   .. table:: **Table 5** **scaling_policy_action** field description

      +-----------------------+-----------------------+-------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                             |
      +=======================+=======================+=========================================================================+
      | operation             | String                | Specifies the scaling action.                                           |
      |                       |                       |                                                                         |
      |                       |                       | -  **ADD**: adds specified number of instances to the AS group.         |
      |                       |                       | -  **REMOVE**: removes specified number of instances from the AS group. |
      |                       |                       | -  **SET**: sets the number of instances in the AS group.               |
      +-----------------------+-----------------------+-------------------------------------------------------------------------+
      | instance_number       | Integer               | Specifies the number of instances to be operated.                       |
      +-----------------------+-----------------------+-------------------------------------------------------------------------+
      | instance_percentage   | Integer               | Specifies the percentage of instances to be operated.                   |
      +-----------------------+-----------------------+-------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "limit": 20,
          "total_number": 1,
          "start_number": 0,
          "scaling_policies": [
              {
                  "scaling_policy_id": "fd7d63ce-8f5c-443e-b9a0-bef9386b23b3",
                  "scaling_group_id": "e5d27f5c-dd76-4a61-b4bc-a67c5686719a",
                  "scaling_policy_name": "as-policy-test",
                  "scaling_policy_type": "SCHEDULED",
                  "scheduled_policy": {
                      "launch_time": "2015-07-24T01:21Z"
                  },
                  "cool_down_time": 300,
                  "scaling_policy_action": {
                      "operation": "REMOVE",
                      "instance_number": 1
                  },
                  "policy_status": "INSERVICE",
                  "create_time": "2015-07-24T01:09:30Z"
              }
          ]
      }

Returned Value
--------------

-  Normal

   200

-  Abnormal

   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | Returned Value                    | Description                                                                                |
   +===================================+============================================================================================+
   | 400 Bad Request                   | The server failed to process the request.                                                  |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 401 Unauthorized                  | You must enter the username and password to access the requested page.                     |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 403 Forbidden                     | You are forbidden to access the requested page.                                            |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 404 Not Found                     | The server could not find the requested page.                                              |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 405 Method Not Allowed            | You are not allowed to use the method specified in the request.                            |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 406 Not Acceptable                | The response generated by the server could not be accepted by the client.                  |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 407 Proxy Authentication Required | You must use the proxy server for authentication to process the request.                   |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 408 Request Timeout               | The request timed out.                                                                     |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 409 Conflict                      | The request could not be processed due to a conflict.                                      |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 500 Internal Server Error         | Failed to complete the request because of an internal service error.                       |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 501 Not Implemented               | Failed to complete the request because the server does not support the requested function. |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 502 Bad Gateway                   | Failed to complete the request because the request is invalid.                             |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 503 Service Unavailable           | Failed to complete the request because the system is unavailable.                          |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 504 Gateway Timeout               | A gateway timeout error occurred.                                                          |
   +-----------------------------------+--------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <as_07_0102>`.
