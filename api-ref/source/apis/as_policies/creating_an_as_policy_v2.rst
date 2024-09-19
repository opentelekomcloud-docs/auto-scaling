:original_name: as_06_0402.html

.. _as_06_0402:

Creating an AS Policy (V2)
==========================

Function
--------

This API is used to create an AS policy for an AS group or bandwidth.

The difference between the V2 and V1 APIs for creating an AS policy is that V2 supports creating an AS policy for adjusting bandwidth and differentiating scaling resources by their types.

URI
---

POST /autoscaling-api/v2/{project_id}/scaling_policy

.. table:: **Table 1** Parameter description

   ========== ========= ====== =========================
   Parameter  Mandatory Type   Description
   ========== ========= ====== =========================
   project_id Yes       String Specifies the project ID.
   ========== ========= ====== =========================

Request
-------

.. table:: **Table 2** Request parameters

   +-----------------------+-----------------+-----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type                                                                  | Description                                                                                                                                                                                                                                                                                              |
   +=======================+=================+=======================================================================+==========================================================================================================================================================================================================================================================================================================+
   | scaling_policy_name   | Yes             | String                                                                | Specifies the AS policy name. The name contains only letters, digits, underscores (_), and hyphens (-), and cannot exceed 64 characters.                                                                                                                                                                 |
   +-----------------------+-----------------+-----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | scaling_resource_id   | Yes             | String                                                                | Specifies the scaling resource ID, which is the unique ID of an AS group or bandwidth.                                                                                                                                                                                                                   |
   |                       |                 |                                                                       |                                                                                                                                                                                                                                                                                                          |
   |                       |                 |                                                                       | -  If **scaling_resource_type** is set to **SCALING_GROUP**, this parameter indicates the unique AS group ID.                                                                                                                                                                                            |
   |                       |                 |                                                                       | -  If **scaling_resource_type** is set to **BANDWIDTH**, this parameter indicates the unique bandwidth ID.                                                                                                                                                                                               |
   +-----------------------+-----------------+-----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | scaling_resource_type | Yes             | String                                                                | Specifies the scaling resource type.                                                                                                                                                                                                                                                                     |
   |                       |                 |                                                                       |                                                                                                                                                                                                                                                                                                          |
   |                       |                 |                                                                       | -  AS group: **SCALING_GROUP**                                                                                                                                                                                                                                                                           |
   |                       |                 |                                                                       | -  Bandwidth: **BANDWIDTH**                                                                                                                                                                                                                                                                              |
   +-----------------------+-----------------+-----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | scaling_policy_type   | Yes             | String                                                                | Specifies the AS policy type.                                                                                                                                                                                                                                                                            |
   |                       |                 |                                                                       |                                                                                                                                                                                                                                                                                                          |
   |                       |                 |                                                                       | -  **ALARM** (corresponding to **alarm_id**): indicates that the scaling action is triggered by an alarm.                                                                                                                                                                                                |
   |                       |                 |                                                                       | -  **SCHEDULED** (corresponding to **scheduled_policy**): indicates that the scaling action is triggered as scheduled.                                                                                                                                                                                   |
   |                       |                 |                                                                       | -  **RECURRENCE** (corresponding to **scheduled_policy**): indicates that the scaling action is triggered periodically.                                                                                                                                                                                  |
   +-----------------------+-----------------+-----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | alarm_id              | No              | String                                                                | Specifies the alarm rule ID. This parameter is mandatory when **scaling_policy_type** is set to **ALARM**. After this parameter is specified, the value of **scheduled_policy** does not take effect.                                                                                                    |
   |                       |                 |                                                                       |                                                                                                                                                                                                                                                                                                          |
   |                       |                 |                                                                       | After you create an alarm policy, the system automatically adds an alarm triggering activity of the autoscaling type to the **alarm_actions** field in the alarm rule specified by the parameter value.                                                                                                  |
   |                       |                 |                                                                       |                                                                                                                                                                                                                                                                                                          |
   |                       |                 |                                                                       | You can obtain the parameter value by querying Cloud Eye alarm rules.                                                                                                                                                                                                                                    |
   +-----------------------+-----------------+-----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | scheduled_policy      | No              | :ref:`scheduled_policy <as_06_0402__table10424101264616>` object      | Specifies the periodic or scheduled AS policy. This parameter is mandatory when **scaling_policy_type** is set to **SCHEDULED** or **RECURRENCE**. After this parameter is specified, the value of **alarm_id** does not take effect. For details, see :ref:`Table 3 <as_06_0402__table10424101264616>`. |
   +-----------------------+-----------------+-----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | scaling_policy_action | No              | :ref:`scaling_policy_action <as_06_0402__table14148153113492>` object | Specifies the scaling action of the AS policy. For details, see :ref:`Table 4 <as_06_0402__table14148153113492>`.                                                                                                                                                                                        |
   +-----------------------+-----------------+-----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cool_down_time        | No              | Integer                                                               | Specifies the cooldown period (in seconds). The value ranges from 0 to 86400 and is 300 by default.                                                                                                                                                                                                      |
   +-----------------------+-----------------+-----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | No              | String                                                                | Specifies the description of the AS policy. The value can contain 1 to 256 characters.                                                                                                                                                                                                                   |
   +-----------------------+-----------------+-----------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _as_06_0402__table10424101264616:

.. table:: **Table 3** **scheduled_policy** field description

   +------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                   |
   +==================+=================+=================+===============================================================================================================================================================================================================================================================================================================+
   | launch_time      | Yes             | String          | Specifies the time when the scaling action is triggered. The time format complies with UTC.                                                                                                                                                                                                                   |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                               |
   |                  |                 |                 | -  If **scaling_policy_type** is set to **SCHEDULED**, the time format is **YYYY-MM-DDThh:mmZ**.                                                                                                                                                                                                              |
   |                  |                 |                 | -  If **scaling_policy_type** is set to **RECURRENCE**, the time format is **hh:mm**.                                                                                                                                                                                                                         |
   +------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | recurrence_type  | No              | String          | Specifies the periodic triggering type. This parameter is mandatory when **scaling_policy_type** is set to **RECURRENCE**.                                                                                                                                                                                    |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                               |
   |                  |                 |                 | -  **Daily**: indicates that the scaling action is triggered once a day.                                                                                                                                                                                                                                      |
   |                  |                 |                 | -  **Weekly**: indicates that the scaling action is triggered once a week.                                                                                                                                                                                                                                    |
   |                  |                 |                 | -  **Monthly**: indicates that the scaling action is triggered once a month.                                                                                                                                                                                                                                  |
   +------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | recurrence_value | No              | String          | Specifies the day when a periodic scaling action is triggered. This parameter is mandatory when **scaling_policy_type** is set to **RECURRENCE**.                                                                                                                                                             |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                               |
   |                  |                 |                 | -  If **recurrence_type** is set to **Daily**, the value is **null**, indicating that the scaling action is triggered once a day.                                                                                                                                                                             |
   |                  |                 |                 | -  If **recurrence_type** is set to **Weekly**, the value ranges from **1** (Sunday) to **7** (Saturday). The digits refer to dates in each week and separated by a comma, such as **1,3,5**.                                                                                                                 |
   |                  |                 |                 | -  If **recurrence_type** is set to **Monthly**, the value ranges from **1** to **31**. The digits refer to the dates in each month and separated by a comma, such as **1,10,13,28**.                                                                                                                         |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                               |
   |                  |                 |                 |    .. note::                                                                                                                                                                                                                                                                                                  |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                               |
   |                  |                 |                 |       When **recurrence_type** is set to **Daily**, this parameter does not take effect.                                                                                                                                                                                                                      |
   +------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | start_time       | No              | String          | Specifies the start time of the scaling action triggered periodically. The time format complies with UTC. The default value is the local time.                                                                                                                                                                |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                               |
   |                  |                 |                 | The time format is **YYYY-MM-DDThh:mmZ**.                                                                                                                                                                                                                                                                     |
   +------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | end_time         | No              | String          | Specifies the end time of the scaling action triggered periodically. The time format complies with UTC. This parameter is mandatory when **scaling_policy_type** is set to **RECURRENCE**. When the scaling action is triggered periodically, the end time cannot be earlier than the current and start time. |
   |                  |                 |                 |                                                                                                                                                                                                                                                                                                               |
   |                  |                 |                 | The time format is **YYYY-MM-DDThh:mmZ**.                                                                                                                                                                                                                                                                     |
   +------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _as_06_0402__table14148153113492:

.. table:: **Table 4** **scaling_policy_action** field description

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                  |
   +=================+=================+=================+==============================================================================================================================================================================================================================================================+
   | operation       | No              | String          | Specifies the operation to be performed. The default operation is **ADD**.                                                                                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                                                                              |
   |                 |                 |                 | -  If **scaling_resource_type** is set to **SCALING_GROUP**, the following operations are supported:                                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                                                                                                                              |
   |                 |                 |                 |    -  **ADD**: indicates adding instances.                                                                                                                                                                                                                   |
   |                 |                 |                 |    -  **REMOVE/REDUCE**: indicates removing or reducing instances.                                                                                                                                                                                           |
   |                 |                 |                 |    -  **SET**: indicates setting the number of instances to a specified value.                                                                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                                                              |
   |                 |                 |                 | -  If **scaling_resource_type** is set to **BANDWIDTH**, the following operations are supported:                                                                                                                                                             |
   |                 |                 |                 |                                                                                                                                                                                                                                                              |
   |                 |                 |                 |    -  **ADD**: indicates adding instances.                                                                                                                                                                                                                   |
   |                 |                 |                 |    -  **REDUCE**: indicates reducing instances.                                                                                                                                                                                                              |
   |                 |                 |                 |    -  **SET**: indicates setting the number of instances to a specified value.                                                                                                                                                                               |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | size            | No              | Integer         | Specifies the operation size. The value is an integer from 0 to 300. The default value is **1**. This parameter can be set to **0** only when **operation** is set to **SET**.                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                                                              |
   |                 |                 |                 | -  If **scaling_resource_type** is set to **SCALING_GROUP**, this parameter indicates the number of instances. The value is an integer from 0 to 300 and the default value is **1**.                                                                         |
   |                 |                 |                 | -  If **scaling_resource_type** is set to **BANDWIDTH**, this parameter indicates the bandwidth (Mbit/s). The value is an integer from 1 to 300 and the default value is **1**.                                                                              |
   |                 |                 |                 | -  If **scaling_resource_type** is set to **SCALING_GROUP**, either **size** or **percentage** can be set.                                                                                                                                                   |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | percentage      | No              | Integer         | Specifies the percentage of instances to be operated. If **operation** is set to **ADD**, **REMOVE**, or **REDUCE**, the value of this parameter is an integer from 1 to 20000. If **operation** is set to **SET**, the value is an integer from 0 to 20000. |
   |                 |                 |                 |                                                                                                                                                                                                                                                              |
   |                 |                 |                 | -  If **scaling_resource_type** is set to **SCALING_GROUP**, either **size** or **percentage** can be set. If neither **size** nor **percentage** is set, the default value of **size** is **1**.                                                            |
   |                 |                 |                 | -  If **scaling_resource_type** is set to **BANDWIDTH**, **percentage** is unavailable.                                                                                                                                                                      |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limits          | No              | Integer         | Specifies the operation restrictions.                                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                                                              |
   |                 |                 |                 | If **scaling_resource_type** is set to **BANDWIDTH** and **operation** is not **SET**, this parameter takes effect and the unit is Mbit/s.                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                                                                                                                              |
   |                 |                 |                 | -  If **operation** is set to **ADD**, this parameter indicates the maximum bandwidth allowed.                                                                                                                                                               |
   |                 |                 |                 | -  If **operation** is set to **REDUCE**, this parameter indicates the minimum bandwidth allowed.                                                                                                                                                            |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

This example creates an alarm-based scaling policy named **hth_aspolicy_1** using the alarm rule with ID **al1513822380493GvlJKZwA8**. The action defined in the policy is to increase the bandwidth with ID **8ade64b5-d685-40b8-8582-4ce306ea37a6** by 1 Mbit/s when the alarm threshold configured in the alarm rule is reached until the bandwidth reaches 10 Mbit/s.

.. code-block:: text

   POST https://{Endpoint}/autoscaling-api/v2/{project_id}/scaling_policy

   {
       "alarm_id": "al1513822380493GvlJKZwA8",
       "cool_down_time": 900,
       "scaling_resource_id": "8ade64b5-d685-40b8-8582-4ce306ea37a6",
       "scaling_resource_type": "BANDWIDTH",
       "scaling_policy_action": {
              "size": 1,
              "operation": "ADD",
              "limits": 10
       },
       "scaling_policy_name": "hth_aspolicy_1",
       "scaling_policy_type": "ALARM"
   }

Response
--------

.. table:: **Table 5** Response parameters

   ================= ====== ===========================
   Parameter         Type   Description
   ================= ====== ===========================
   scaling_policy_id String Specifies the AS policy ID.
   ================= ====== ===========================

Example Response
----------------

.. code-block::

   {
        "scaling_policy_id": "0h327883-324n-4dzd-9c61-68d03ee191dd"
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
