:original_name: as_06_0409.html

.. _as_06_0409:

Querying an AS Policy (V2)
==========================

Function
--------

This API is used to query details about a specified AS policy by policy ID.

The difference between the V2 and V1 APIs for querying details of an AS policy is that V2 contains scaling resource types in response messages.

URI
---

GET /autoscaling-api/v2/{project_id}/scaling_policy/{scaling_policy_id}

.. table:: **Table 1** Parameter description

   ================= ========= ====== ===========================
   Parameter         Mandatory Type   Description
   ================= ========= ====== ===========================
   project_id        Yes       String Specifies the project ID.
   scaling_policy_id Yes       String Specifies the AS policy ID.
   ================= ========= ====== ===========================

Request Message
---------------

-  Request parameters

   None

-  Example request

   This example shows how to query details about the AS policy with ID **906f73ff-56e8-41b2-a005-8157d0c60361**.

   .. code-block:: text

      GET https://{Endpoint}/autoscaling-api/v2/{project_id}/scaling_policy/906f73ff-56e8-41b2-a005-8157d0c60361

Response Message
----------------

-  Response parameters

   .. table:: **Table 2** Response parameters

      +----------------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------+
      | Parameter      | Type                                                           | Description                                                                                               |
      +================+================================================================+===========================================================================================================+
      | scaling_policy | :ref:`scaling_policy <as_06_0409__table10729655182210>` object | Specifies details about the AS policy. For details, see :ref:`Table 3 <as_06_0409__table10729655182210>`. |
      +----------------+----------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------+

   .. _as_06_0409__table10729655182210:

   .. table:: **Table 3** **scaling_policy** field description

      +-----------------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                                                                | Description                                                                                                                                                                                                                                           |
      +=======================+=====================================================================+=======================================================================================================================================================================================================================================================+
      | scaling_resource_id   | String                                                              | Specifies the scaling resource ID.                                                                                                                                                                                                                    |
      +-----------------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | scaling_resource_type | String                                                              | Specifies the scaling resource type.                                                                                                                                                                                                                  |
      |                       |                                                                     |                                                                                                                                                                                                                                                       |
      |                       |                                                                     | -  AS group: **SCALING_GROUP**                                                                                                                                                                                                                        |
      |                       |                                                                     | -  Bandwidth: **BANDWIDTH**                                                                                                                                                                                                                           |
      +-----------------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | scaling_policy_name   | String                                                              | Specifies the AS policy name.                                                                                                                                                                                                                         |
      |                       |                                                                     |                                                                                                                                                                                                                                                       |
      |                       |                                                                     | Supports fuzzy search.                                                                                                                                                                                                                                |
      +-----------------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | scaling_policy_id     | String                                                              | Specifies the AS policy ID.                                                                                                                                                                                                                           |
      +-----------------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | policy_status         | String                                                              | Specifies the AS policy status.                                                                                                                                                                                                                       |
      |                       |                                                                     |                                                                                                                                                                                                                                                       |
      |                       |                                                                     | -  **INSERVICE**: The AS policy is enabled.                                                                                                                                                                                                           |
      |                       |                                                                     | -  **PAUSED**: The AS policy is disabled.                                                                                                                                                                                                             |
      |                       |                                                                     | -  **EXECUTING**: The AS policy is being executed.                                                                                                                                                                                                    |
      +-----------------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | scaling_policy_type   | String                                                              | Specifies the AS policy type.                                                                                                                                                                                                                         |
      |                       |                                                                     |                                                                                                                                                                                                                                                       |
      |                       |                                                                     | -  **ALARM**: indicates that the scaling action is triggered by an alarm. A value is returned for **alarm_id**, and no value is returned for **scheduled_policy**.                                                                                    |
      |                       |                                                                     | -  **SCHEDULED**: indicates that the scaling action is triggered as scheduled. A value is returned for **scheduled_policy**, and no value is returned for **alarm_id**, **recurrence_type**, **recurrence_value**, **start_time**, or **end_time**.   |
      |                       |                                                                     | -  **RECURRENCE**: indicates that the scaling action is triggered periodically. Values are returned for **scheduled_policy**, **recurrence_type**, **recurrence_value**, **start_time**, and **end_time**, and no value is returned for **alarm_id**. |
      +-----------------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | alarm_id              | String                                                              | Specifies the alarm ID.                                                                                                                                                                                                                               |
      +-----------------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | scheduled_policy      | :ref:`scheduled_policy <as_06_0409__table179725552211>` object      | Specifies the periodic or scheduled AS policy. For details, see :ref:`Table 4 <as_06_0409__table179725552211>`.                                                                                                                                       |
      +-----------------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | scaling_policy_action | :ref:`scaling_policy_action <as_06_0409__table483105512229>` object | Specifies the scaling action of the AS policy. For details, see :ref:`Table 5 <as_06_0409__table483105512229>`.                                                                                                                                       |
      +-----------------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | cool_down_time        | Integer                                                             | Specifies the cooldown period (s).                                                                                                                                                                                                                    |
      +-----------------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | create_time           | String                                                              | Specifies the time when an AS policy was created. The time format complies with UTC.                                                                                                                                                                  |
      +-----------------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | meta_data             | :ref:`meta_data <as_06_0409__table14568680175854>` object           | Provides additional information. For details, see :ref:`Table 6 <as_06_0409__table14568680175854>`.                                                                                                                                                   |
      +-----------------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | description           | String                                                              | Specifies the AS policy description.                                                                                                                                                                                                                  |
      +-----------------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _as_06_0409__table179725552211:

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

   .. _as_06_0409__table483105512229:

   .. table:: **Table 5** **scaling_policy_action** field description

      +-----------------------+-----------------------+-----------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                 |
      +=======================+=======================+=============================================================================+
      | operation             | String                | Specifies the scaling action.                                               |
      |                       |                       |                                                                             |
      |                       |                       | -  **ADD**: indicates adding instances.                                     |
      |                       |                       | -  **REDUCE**: indicates reducing instances.                                |
      |                       |                       | -  **SET**: indicates setting the number of instances to a specified value. |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------+
      | size                  | Integer               | Specifies the operation size.                                               |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------+
      | percentage            | Integer               | Specifies the percentage of instances to be operated.                       |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------+
      | limits                | Integer               | Specifies the operation restrictions.                                       |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------+

   .. _as_06_0409__table14568680175854:

   .. table:: **Table 6** **meta_data** field description

      +-------------------------------+--------+-------------------------------------------------------------------------+
      | Parameter                     | Type   | Description                                                             |
      +===============================+========+=========================================================================+
      | metadata_bandwidth_share_type | String | Specifies the bandwidth sharing type in the bandwidth scaling policy.   |
      +-------------------------------+--------+-------------------------------------------------------------------------+
      | metadata_eip_id               | String | Specifies the EIP ID for the bandwidth in the bandwidth scaling policy. |
      +-------------------------------+--------+-------------------------------------------------------------------------+
      | metadata_eip_address          | String | Specifies the EIP for the bandwidth in the bandwidth scaling policy.    |
      +-------------------------------+--------+-------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "scaling_policy": {
                 "scaling_policy_id": "906f73ff-56e8-41b2-a005-8157d0c60361",
                 "scaling_policy_name": "hth_aspolicy_1",
                 "scaling_resource_id": "8ade64b5-d685-40b8-8582-4ce306ea37a6",
                 "scaling_resource_type": "BANDWIDTH",
                 "scaling_policy_type": "ALARM",
                 "alarm_id": "al1513822380493GvlJKZwA8",
                 "scheduled_policy": {
                 },
                 "cool_down_time": 900,
                 "scaling_policy_action": {
                        "operation": "ADD",
                        "size": 1,
                        "limits": 111
                 },
                 "policy_status": "INSERVICE",
                 "create_time": "2018-03-21T08:03:35Z",
                 "meta_data": {
                     "metadata_eip_id": "263f0886-de6a-4e21-ad83-814ca9f3844e",
                     "metadata_eip_address": "255.255.255.255"
                 }
          }
      }

Returned Values
---------------

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
