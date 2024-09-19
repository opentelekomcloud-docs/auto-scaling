:original_name: as_06_0403.html

.. _as_06_0403:

Modifying an AS Policy
======================

Function
--------

This API is used to modify a specified AS policy.

URI
---

PUT /autoscaling-api/v1/{project_id}/scaling_policy/{scaling_policy_id}

.. table:: **Table 1** Parameter description

   +-------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory | Type   | Description                                                                                                |
   +===================+===========+========+============================================================================================================+
   | project_id        | Yes       | String | Specifies the project ID.                                                                                  |
   +-------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+
   | scaling_policy_id | Yes       | String | Specifies an AS policy ID. For details, see :ref:`Querying AS Policies Bound to an AS Group <as_06_0405>`. |
   +-------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+

Request
-------

.. table:: **Table 2** Request parameters

   +-----------------------+-----------------+-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type                                                                                | Description                                                                                                                                                                                                                                                                                                            |
   +=======================+=================+=====================================================================================+========================================================================================================================================================================================================================================================================================================================+
   | scaling_policy_name   | No              | String                                                                              | Specifies the AS policy name. The name contains only letters, digits, underscores (_), and hyphens (-), and cannot exceed 64 characters.                                                                                                                                                                               |
   +-----------------------+-----------------+-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | scaling_policy_type   | No              | String                                                                              | Specifies the AS policy type.                                                                                                                                                                                                                                                                                          |
   |                       |                 |                                                                                     |                                                                                                                                                                                                                                                                                                                        |
   |                       |                 |                                                                                     | -  **ALARM** (corresponding to **alarm_id**): indicates that the scaling action is triggered by an alarm.                                                                                                                                                                                                              |
   |                       |                 |                                                                                     | -  **SCHEDULED** (corresponding to **scheduled_policy**): indicates that the scaling action is triggered as scheduled.                                                                                                                                                                                                 |
   |                       |                 |                                                                                     | -  **RECURRENCE** (corresponding to **scheduled_policy**): indicates that the scaling action is triggered periodically.                                                                                                                                                                                                |
   +-----------------------+-----------------+-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | alarm_id              | No              | String                                                                              | Specifies the alarm rule ID. This parameter is mandatory when **scaling_policy_type** is set to **ALARM**. After this parameter is specified, the value of **scheduled_policy** does not take effect.                                                                                                                  |
   |                       |                 |                                                                                     |                                                                                                                                                                                                                                                                                                                        |
   |                       |                 |                                                                                     | After you modify an alarm policy, the system automatically adds an alarm triggering activity of the autoscaling type to the **alarm_actions** field in the alarm rule specified by the parameter value.                                                                                                                |
   |                       |                 |                                                                                     |                                                                                                                                                                                                                                                                                                                        |
   |                       |                 |                                                                                     | You can obtain the parameter value by querying Cloud Eye alarm rules.                                                                                                                                                                                                                                                  |
   +-----------------------+-----------------+-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | scheduled_policy      | No              | :ref:`scheduled_policy <as_06_0403__t759e6d15d244474e8f286185ede143fb>` object      | Specifies the periodic or scheduled AS policy. This parameter is mandatory when **scaling_policy_type** is set to **SCHEDULED** or **RECURRENCE**. After this parameter is specified, the value of **alarm_id** does not take effect. For details, see :ref:`Table 3 <as_06_0403__t759e6d15d244474e8f286185ede143fb>`. |
   +-----------------------+-----------------+-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | scaling_policy_action | No              | :ref:`scaling_policy_action <as_06_0403__t34390832ab524bcc8123c0f9a056064f>` object | Specifies the scaling action of the AS policy. For details, see :ref:`Table 4 <as_06_0403__t34390832ab524bcc8123c0f9a056064f>`.                                                                                                                                                                                        |
   +-----------------------+-----------------+-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cool_down_time        | No              | Integer                                                                             | Specifies the cooldown period (in seconds). The value ranges from 0 to 86400.                                                                                                                                                                                                                                          |
   +-----------------------+-----------------+-------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _as_06_0403__t759e6d15d244474e8f286185ede143fb:

.. table:: **Table 3** **scheduled_policy** field description

   +------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory       | Type            | Description                                                                                                                                                                                   |
   +==================+=================+=================+===============================================================================================================================================================================================+
   | launch_time      | Yes             | String          | Specifies the time when the scaling action is triggered. The time format complies with UTC.                                                                                                   |
   |                  |                 |                 |                                                                                                                                                                                               |
   |                  |                 |                 | -  If **scaling_policy_type** is set to **SCHEDULED**, the time format is **YYYY-MM-DDThh:mmZ**.                                                                                              |
   |                  |                 |                 | -  If **scaling_policy_type** is set to **RECURRENCE**, the time format is **hh:mm**.                                                                                                         |
   +------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | recurrence_type  | No              | String          | Specifies the periodic triggering type. This parameter is mandatory when **scaling_policy_type** is set to **RECURRENCE**.                                                                    |
   |                  |                 |                 |                                                                                                                                                                                               |
   |                  |                 |                 | -  **Daily**: indicates that the scaling action is triggered once a day.                                                                                                                      |
   |                  |                 |                 | -  **Weekly**: indicates that the scaling action is triggered once a week.                                                                                                                    |
   |                  |                 |                 | -  **Monthly**: indicates that the scaling action is triggered once a month.                                                                                                                  |
   +------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | recurrence_value | No              | String          | Specifies the day when a periodic scaling action is triggered. This parameter is mandatory when **scaling_policy_type** is set to **RECURRENCE**.                                             |
   |                  |                 |                 |                                                                                                                                                                                               |
   |                  |                 |                 | -  If **recurrence_type** is set to **Daily**, the value is **null**, indicating that the scaling action is triggered once a day.                                                             |
   |                  |                 |                 | -  If **recurrence_type** is set to **Weekly**, the value ranges from **1** (Sunday) to **7** (Saturday). The digits refer to dates in each week and separated by a comma, such as **1,3,5**. |
   |                  |                 |                 | -  If **recurrence_type** is set to **Monthly**, the value ranges from **1** to **31**. The digits refer to the dates in each month and separated by a comma, such as **1,10,13,28**.         |
   +------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | start_time       | No              | String          | Specifies the start time of the scaling action triggered periodically. The time format complies with UTC.                                                                                     |
   |                  |                 |                 |                                                                                                                                                                                               |
   |                  |                 |                 | The time format is **YYYY-MM-DDThh:mmZ**.                                                                                                                                                     |
   +------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | end_time         | No              | String          | Specifies the end time of the scaling action triggered periodically. The time format complies with UTC. This parameter is mandatory when **scaling_policy_type** is set to **RECURRENCE**.    |
   |                  |                 |                 |                                                                                                                                                                                               |
   |                  |                 |                 | When the scaling action is triggered periodically, the end time cannot be earlier than the current and start time.                                                                            |
   |                  |                 |                 |                                                                                                                                                                                               |
   |                  |                 |                 | The time format is **YYYY-MM-DDThh:mmZ**.                                                                                                                                                     |
   +------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _as_06_0403__t34390832ab524bcc8123c0f9a056064f:

.. table:: **Table 4** **scaling_policy_action** field description

   +---------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter           | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                                                                                         |
   +=====================+=================+=================+=====================================================================================================================================================================================================================================================================================================================================================================================+
   | operation           | No              | String          | Specifies the operation to be performed. The default operation is **ADD**.                                                                                                                                                                                                                                                                                                          |
   |                     |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                     |
   |                     |                 |                 | -  **ADD**: adds specified number of instances to the AS group.                                                                                                                                                                                                                                                                                                                     |
   |                     |                 |                 | -  **REMOVE/REDUCE**: removes or reduces specified number of instances from the AS group.                                                                                                                                                                                                                                                                                           |
   |                     |                 |                 | -  **SET**: sets the number of instances in the AS group.                                                                                                                                                                                                                                                                                                                           |
   +---------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_number     | No              | Integer         | Specifies the number of instances to be operated. The default number is **1**. The value range is as follows for a default quota:                                                                                                                                                                                                                                                   |
   |                     |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                     |
   |                     |                 |                 | -  If **operation** is set to **SET**, the value ranges from 0 to 200.                                                                                                                                                                                                                                                                                                              |
   |                     |                 |                 | -  If **operation** is set to **ADD**, **REMOVE**, or **REDUCE**, the value ranges from 1 to 200.                                                                                                                                                                                                                                                                                   |
   |                     |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                     |
   |                     |                 |                 | .. note::                                                                                                                                                                                                                                                                                                                                                                           |
   |                     |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                     |
   |                     |                 |                 |    Either **instance_number** or **instance_percentage** is required.                                                                                                                                                                                                                                                                                                               |
   +---------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_percentage | No              | Integer         | Specifies the percentage of instances to be operated. You can increase, decrease, or set the number of instances in an AS group to the specified percentage of the current number of instances. If **operation** is set to **ADD**, **REMOVE** or **REDUCE**, the value is an integer from 1 to 20000. If **operation** is set to **SET**, the value is an integer from 0 to 20000. |
   |                     |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                     |
   |                     |                 |                 | If neither **instance_number** nor **instance_percentage** is specified, the number of instances to be operated is 1.                                                                                                                                                                                                                                                               |
   |                     |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                     |
   |                     |                 |                 | Either **instance_number** or **instance_percentage** is required.                                                                                                                                                                                                                                                                                                                  |
   +---------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

This example modifies the periodic AS policy with ID **0h327883-324n-4dzd-9c61-68d03ee191dd** for an AS group with two instances. The modification is as follows: The AS policy name is changed to **policy_01**, and the policy is executed at 16:00 every day from 2016-01-08T17:31Z to 2016-02-08T17:31Z.

.. code-block:: text

   PUT https://{Endpoint}/autoscaling-api/v1/{project_id}/scaling_policy/0h327883-324n-4dzd-9c61-68d03ee191dd

   {
       "scaling_policy_type": "RECURRENCE",
       "scaling_policy_name": "policy_01",
       "scheduled_policy": {
           "launch_time": "16:00",
           "recurrence_type": "Daily",
           "end_time": "2016-02-08T17:31Z",
           "start_time": "2016-01-08T17:31Z"
       },
       "scaling_policy_action": {
           "operation": "SET",
           "instance_number": 2
       }
   }

Response
--------

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
