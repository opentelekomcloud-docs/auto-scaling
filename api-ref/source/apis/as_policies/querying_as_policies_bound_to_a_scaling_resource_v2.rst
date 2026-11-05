:original_name: as_06_0406.html

.. _as_06_0406:

Querying AS Policies Bound to a Scaling Resource (V2)
=====================================================

Function
--------

This API is used to query AS policies based on search criteria. The results are displayed by page.

-  The difference between the V2 and V1 APIs for querying AS policies is that V2 contains scaling resource types in response messages.
-  Search criteria can be the AS policy name, policy type, policy ID, start line number, and number of records.
-  If no search criteria are specified, a maximum of 20 AS policies for specified resources can be queried for a tenant by default.

URI
---

GET /autoscaling-api/v2/{project_id}/scaling_policy/{scaling_resource_id}/list

.. note::

   You can type the question mark (?) and ampersand (&) at the end of the URI to define multiple search criteria. AS policies can be searched by all optional parameters in the following table. For details, see the example request.

.. table:: **Table 1** Parameter description

   +---------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------+
   | Parameter           | Mandatory       | Type            | Description                                                                                                        |
   +=====================+=================+=================+====================================================================================================================+
   | project_id          | Yes             | String          | **Definition**                                                                                                     |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | Specifies the project ID. For details, see :ref:`Obtaining a Project ID <as_04_0106>`.                             |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | **Constraints**                                                                                                    |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | N/A                                                                                                                |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | **Range**                                                                                                          |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | N/A                                                                                                                |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | **Default Value**                                                                                                  |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | N/A                                                                                                                |
   +---------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------+
   | scaling_resource_id | Yes             | String          | **Definition**                                                                                                     |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | Specifies the scaling resource ID, which is the ID of a unique AS group or bandwidth.                              |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | -  If **scaling_resource_type** is set to **SCALING_GROUP**, this parameter indicates a unique AS group ID.        |
   |                     |                 |                 | -  If **scaling_resource_type** is set to **BANDWIDTH**, this parameter indicates a unique bandwidth ID.           |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | **Constraints**                                                                                                    |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | N/A                                                                                                                |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | **Range**                                                                                                          |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | N/A                                                                                                                |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | **Default Value**                                                                                                  |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | N/A                                                                                                                |
   +---------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------+
   | scaling_policy_name | No              | String          | **Definition**                                                                                                     |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | Specifies the AS policy name.                                                                                      |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | **Constraints**                                                                                                    |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | N/A                                                                                                                |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | **Range**                                                                                                          |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | The value can contain 1 to 64 characters. Only letters, digits, underscores (_), and hyphens (-) are allowed.      |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | **Default Value**                                                                                                  |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | N/A                                                                                                                |
   +---------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------+
   | scaling_policy_type | No              | String          | **Definition**                                                                                                     |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | Specifies the AS policy type.                                                                                      |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | **Constraints**                                                                                                    |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | N/A                                                                                                                |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | **Range**                                                                                                          |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | -  **ALARM**: alarm policy                                                                                         |
   |                     |                 |                 | -  **SCHEDULED**: scheduled policy                                                                                 |
   |                     |                 |                 | -  **RECURRENCE**: periodic policy                                                                                 |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | **Default Value**                                                                                                  |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | N/A                                                                                                                |
   +---------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------+
   | scaling_policy_id   | No              | String          | **Definition**                                                                                                     |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | Specifies the AS policy ID. For details about how to obtain it, see :ref:`Querying AS Policies (V2) <as_06_0407>`. |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | **Constraints**                                                                                                    |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | N/A                                                                                                                |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | **Range**                                                                                                          |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | N/A                                                                                                                |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | **Default Value**                                                                                                  |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | N/A                                                                                                                |
   +---------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------+
   | start_number        | No              | Integer         | **Definition**                                                                                                     |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | Specifies the start line number.                                                                                   |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | **Constraints**                                                                                                    |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | N/A                                                                                                                |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | **Range**                                                                                                          |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | The minimum value is **0**, and there is no limit on the maximum value.                                            |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | **Default Value**                                                                                                  |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | 0                                                                                                                  |
   +---------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------+
   | limit               | No              | Integer         | **Definition**                                                                                                     |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | Specifies the number of records to be returned.                                                                    |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | **Constraints**                                                                                                    |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | N/A                                                                                                                |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | **Range**                                                                                                          |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | 0-100                                                                                                              |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | **Default Value**                                                                                                  |
   |                     |                 |                 |                                                                                                                    |
   |                     |                 |                 | 20                                                                                                                 |
   +---------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------+

Request
-------

None

Example Request
---------------

This example shows how to query all periodic AS policies for the resource with ID **8ade64b5-d685-40b8-8582-4ce306ea37a6**.

.. code-block:: text

   GET https://{Endpoint}/autoscaling-api/v2/{project_id}/scaling_policy/8ade64b5-d685-40b8-8582-4ce306ea37a6/list?scaling_policy_type=RECURRENCE

Response
--------

.. table:: **Table 2** Response parameters

   +-----------------------+----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                       | Description                                                                               |
   +=======================+============================================================================+===========================================================================================+
   | total_number          | Integer                                                                    | **Definition**                                                                            |
   |                       |                                                                            |                                                                                           |
   |                       |                                                                            | Specifies the total number of query records.                                              |
   |                       |                                                                            |                                                                                           |
   |                       |                                                                            | **Range**                                                                                 |
   |                       |                                                                            |                                                                                           |
   |                       |                                                                            | N/A                                                                                       |
   +-----------------------+----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------+
   | start_number          | Integer                                                                    | **Definition**                                                                            |
   |                       |                                                                            |                                                                                           |
   |                       |                                                                            | Specifies the start line number.                                                          |
   |                       |                                                                            |                                                                                           |
   |                       |                                                                            | **Range**                                                                                 |
   |                       |                                                                            |                                                                                           |
   |                       |                                                                            | The minimum value is **0**, and there is no limit on the maximum value.                   |
   +-----------------------+----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------+
   | limit                 | Integer                                                                    | **Definition**                                                                            |
   |                       |                                                                            |                                                                                           |
   |                       |                                                                            | Specifies the maximum number of resources to be queried.                                  |
   |                       |                                                                            |                                                                                           |
   |                       |                                                                            | **Range**                                                                                 |
   |                       |                                                                            |                                                                                           |
   |                       |                                                                            | 0-100                                                                                     |
   +-----------------------+----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------+
   | scaling_policies      | Array of :ref:`scaling_policies <as_06_0406__table19638345141818>` objects | **Definition**                                                                            |
   |                       |                                                                            |                                                                                           |
   |                       |                                                                            | Specifies AS policies. For details, see :ref:`Table 3 <as_06_0406__table19638345141818>`. |
   +-----------------------+----------------------------------------------------------------------------+-------------------------------------------------------------------------------------------+

.. _as_06_0406__table19638345141818:

.. table:: **Table 3** **scaling_policies** field description

   +-----------------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                | Description                                                                                                                                                                                                                                           |
   +=======================+=====================================================================+=======================================================================================================================================================================================================================================================+
   | scaling_policy_name   | String                                                              | **Definition**                                                                                                                                                                                                                                        |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | Specifies the AS policy name. Fuzzy match is supported.                                                                                                                                                                                               |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | **Range**                                                                                                                                                                                                                                             |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | N/A                                                                                                                                                                                                                                                   |
   +-----------------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | scaling_policy_id     | String                                                              | **Definition**                                                                                                                                                                                                                                        |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | Specifies the AS policy ID.                                                                                                                                                                                                                           |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | **Range**                                                                                                                                                                                                                                             |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | N/A                                                                                                                                                                                                                                                   |
   +-----------------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | scaling_resource_id   | String                                                              | **Definition**                                                                                                                                                                                                                                        |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | Specifies the scaling resource ID.                                                                                                                                                                                                                    |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | **Range**                                                                                                                                                                                                                                             |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | N/A                                                                                                                                                                                                                                                   |
   +-----------------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | scaling_resource_type | String                                                              | **Definition**                                                                                                                                                                                                                                        |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | Specifies the scaling resource type.                                                                                                                                                                                                                  |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | **Range**                                                                                                                                                                                                                                             |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | -  **SCALING_GROUP**: AS group                                                                                                                                                                                                                        |
   |                       |                                                                     | -  **BANDWIDTH**: bandwidth                                                                                                                                                                                                                           |
   +-----------------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | policy_status         | String                                                              | **Definition**                                                                                                                                                                                                                                        |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | Specifies the AS policy status.                                                                                                                                                                                                                       |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | **Range**                                                                                                                                                                                                                                             |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | -  **INSERVICE**: The AS policy is enabled.                                                                                                                                                                                                           |
   |                       |                                                                     | -  **PAUSED**: The AS policy is disabled.                                                                                                                                                                                                             |
   |                       |                                                                     | -  **EXECUTING**: The AS policy is being executed.                                                                                                                                                                                                    |
   +-----------------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | scaling_policy_type   | String                                                              | **Definition**                                                                                                                                                                                                                                        |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | Specifies the AS policy type.                                                                                                                                                                                                                         |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | **Range**                                                                                                                                                                                                                                             |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | -  **ALARM**: indicates that the scaling action is triggered by an alarm. A value is returned for **alarm_id**, and no value is returned for **scheduled_policy**.                                                                                    |
   |                       |                                                                     | -  **SCHEDULED**: indicates that the scaling action is triggered as scheduled. A value is returned for **scheduled_policy**, and no value is returned for **alarm_id**, **recurrence_type**, **recurrence_value**, **start_time**, or **end_time**.   |
   |                       |                                                                     | -  **RECURRENCE**: indicates that the scaling action is triggered periodically. Values are returned for **scheduled_policy**, **recurrence_type**, **recurrence_value**, **start_time**, and **end_time**, and no value is returned for **alarm_id**. |
   +-----------------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | alarm_id              | String                                                              | **Definition**                                                                                                                                                                                                                                        |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | Specifies the alarm ID.                                                                                                                                                                                                                               |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | **Range**                                                                                                                                                                                                                                             |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | N/A                                                                                                                                                                                                                                                   |
   +-----------------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | scheduled_policy      | :ref:`scheduled_policy <as_06_0406__table1276581101919>` object     | **Definition**                                                                                                                                                                                                                                        |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | Specifies the periodic or scheduled AS policy. For details, see :ref:`Table 4 <as_06_0406__table1276581101919>`.                                                                                                                                      |
   +-----------------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | scaling_policy_action | :ref:`scaling_policy_action <as_06_0406__table881433612199>` object | **Definition**                                                                                                                                                                                                                                        |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | Specifies the scaling action of the AS policy. For details, see :ref:`Table 5 <as_06_0406__table881433612199>`.                                                                                                                                       |
   +-----------------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | cool_down_time        | Integer                                                             | **Definition**                                                                                                                                                                                                                                        |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | Specifies the cooldown period, in seconds.                                                                                                                                                                                                            |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | **Range**                                                                                                                                                                                                                                             |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | 0s to 86,400s                                                                                                                                                                                                                                         |
   +-----------------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | String                                                              | **Definition**                                                                                                                                                                                                                                        |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | Specifies the time when an AS policy was created. The value is a UTC time in the format of *YYYY-MM-DDTHH:mm:ssZ*, for example, **2017-08-31T03:02:41Z**.                                                                                             |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | **Range**                                                                                                                                                                                                                                             |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | N/A                                                                                                                                                                                                                                                   |
   +-----------------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | meta_data             | :ref:`meta_data <as_06_0406__table14568680175854>` object           | **Definition**                                                                                                                                                                                                                                        |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | Provides additional information. For details, see :ref:`Table 6 <as_06_0406__table14568680175854>`.                                                                                                                                                   |
   +-----------------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                                                              | **Definition**                                                                                                                                                                                                                                        |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | Specifies the AS policy description.                                                                                                                                                                                                                  |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | **Range**                                                                                                                                                                                                                                             |
   |                       |                                                                     |                                                                                                                                                                                                                                                       |
   |                       |                                                                     | N/A                                                                                                                                                                                                                                                   |
   +-----------------------+---------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _as_06_0406__table1276581101919:

.. table:: **Table 4** **scheduled_policy** field description

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                   |
   +=======================+=======================+===============================================================================================================================================================================================+
   | launch_time           | String                | **Definition**                                                                                                                                                                                |
   |                       |                       |                                                                                                                                                                                               |
   |                       |                       | Specifies the time when the scaling action is triggered. The time format complies with UTC.                                                                                                   |
   |                       |                       |                                                                                                                                                                                               |
   |                       |                       | -  If **scaling_policy_type** is set to **SCHEDULED**, the time format is *YYYY-MM-DDThh:mmZ*.                                                                                                |
   |                       |                       | -  If **scaling_policy_type** is set to **RECURRENCE**, the time format is *hh:mm*.                                                                                                           |
   |                       |                       |                                                                                                                                                                                               |
   |                       |                       | **Range**                                                                                                                                                                                     |
   |                       |                       |                                                                                                                                                                                               |
   |                       |                       | N/A                                                                                                                                                                                           |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | recurrence_type       | String                | **Definition**                                                                                                                                                                                |
   |                       |                       |                                                                                                                                                                                               |
   |                       |                       | Specifies the type of a periodically triggered scaling action.                                                                                                                                |
   |                       |                       |                                                                                                                                                                                               |
   |                       |                       | **Range**                                                                                                                                                                                     |
   |                       |                       |                                                                                                                                                                                               |
   |                       |                       | -  **Daily**: indicates that the scaling action is triggered once a day.                                                                                                                      |
   |                       |                       | -  **Weekly**: The scaling action is triggered once a week.                                                                                                                                   |
   |                       |                       | -  **Monthly**: The scaling action is triggered once a month.                                                                                                                                 |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | recurrence_value      | String                | **Definition**                                                                                                                                                                                |
   |                       |                       |                                                                                                                                                                                               |
   |                       |                       | Specifies the frequency at which scaling actions are triggered.                                                                                                                               |
   |                       |                       |                                                                                                                                                                                               |
   |                       |                       | **Range**                                                                                                                                                                                     |
   |                       |                       |                                                                                                                                                                                               |
   |                       |                       | -  If **recurrence_type** is set to **Daily**, the value is **null**, indicating that the scaling action is triggered once a day.                                                             |
   |                       |                       | -  If **recurrence_type** is set to **Weekly**, the value ranges from **1** (Sunday) to **7** (Saturday). The digits refer to dates in each week and separated by a comma, such as **1,3,5**. |
   |                       |                       | -  If **recurrence_type** is set to **Monthly**, the value ranges from **1** to **31**. The digits refer to the dates in each month and separated by a comma, such as **1,10,13,28**.         |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | start_time            | String                | **Definition**                                                                                                                                                                                |
   |                       |                       |                                                                                                                                                                                               |
   |                       |                       | Specifies the start time of the scaling action triggered periodically. The time format complies with UTC.                                                                                     |
   |                       |                       |                                                                                                                                                                                               |
   |                       |                       | The time format is *YYYY-MM-DDThh:mmZ*.                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                                               |
   |                       |                       | **Range**                                                                                                                                                                                     |
   |                       |                       |                                                                                                                                                                                               |
   |                       |                       | N/A                                                                                                                                                                                           |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | end_time              | String                | **Definition**                                                                                                                                                                                |
   |                       |                       |                                                                                                                                                                                               |
   |                       |                       | Specifies the end time of the scaling action triggered periodically. The time format complies with UTC.                                                                                       |
   |                       |                       |                                                                                                                                                                                               |
   |                       |                       | The time format is *YYYY-MM-DDThh:mmZ*.                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                                               |
   |                       |                       | **Range**                                                                                                                                                                                     |
   |                       |                       |                                                                                                                                                                                               |
   |                       |                       | N/A                                                                                                                                                                                           |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _as_06_0406__table881433612199:

.. table:: **Table 5** **scaling_policy_action** field description

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                          |
   +=======================+=======================+======================================================================================================================================================================================================+
   | operation             | String                | **Definition**                                                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                                                      |
   |                       |                       | Specifies the operation to be performed.                                                                                                                                                             |
   |                       |                       |                                                                                                                                                                                                      |
   |                       |                       | **Range**                                                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                      |
   |                       |                       | -  If **scaling_resource_type** is set to **SCALING_GROUP**, the following operations are supported:                                                                                                 |
   |                       |                       |                                                                                                                                                                                                      |
   |                       |                       |    -  **ADD**: adds instances to the AS group.                                                                                                                                                       |
   |                       |                       |    -  **REMOVE**/**REDUCE**: removes or reduces instances from the AS group.                                                                                                                         |
   |                       |                       |    -  **SET**: sets the number of instances in the AS group.                                                                                                                                         |
   |                       |                       |                                                                                                                                                                                                      |
   |                       |                       | -  If **scaling_resource_type** is set to **BANDWIDTH**, the following operations are supported:                                                                                                     |
   |                       |                       |                                                                                                                                                                                                      |
   |                       |                       |    -  **ADD**: increases the bandwidth.                                                                                                                                                              |
   |                       |                       |    -  **REDUCE**: decreases the bandwidth.                                                                                                                                                           |
   |                       |                       |    -  **SET**: sets the bandwidth to a fixed value.                                                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | size                  | Integer               | **Definition**                                                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                                                      |
   |                       |                       | Specifies the number of instances to be operated.                                                                                                                                                    |
   |                       |                       |                                                                                                                                                                                                      |
   |                       |                       | **Range**                                                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                      |
   |                       |                       | -  If **scaling_resource_type** is set to **SCALING_GROUP**, this parameter indicates the number of instances. The value is an integer ranging from **0** to **300** and the default value is **1**. |
   |                       |                       | -  If **scaling_resource_type** is set to **BANDWIDTH**, this parameter indicates the bandwidth (Mbit/s). The value is an integer ranging from **1** to **300** and the default value is **1**.      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | percentage            | Integer               | **Definition**                                                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                                                      |
   |                       |                       | Specifies the percentage of instances to be operated.                                                                                                                                                |
   |                       |                       |                                                                                                                                                                                                      |
   |                       |                       | **Range**                                                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                      |
   |                       |                       | -  If **operation** is set to **ADD**, **REMOVE**, or **REDUCE**, the value is an integer ranging from **1** to **20000**.                                                                           |
   |                       |                       | -  If **operation** is set to **SET**, the value is an integer ranging from **0** to **20000**.                                                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limits                | Integer               | **Definition**                                                                                                                                                                                       |
   |                       |                       |                                                                                                                                                                                                      |
   |                       |                       | Specifies the operation restrictions.                                                                                                                                                                |
   |                       |                       |                                                                                                                                                                                                      |
   |                       |                       | -  If **operation** is set to **ADD**, this parameter indicates the maximum bandwidth allowed.                                                                                                       |
   |                       |                       | -  If **operation** is set to **REDUCE**, this parameter indicates the minimum bandwidth allowed.                                                                                                    |
   |                       |                       |                                                                                                                                                                                                      |
   |                       |                       | **Range**                                                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                      |
   |                       |                       | N/A                                                                                                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _as_06_0406__table14568680175854:

.. table:: **Table 6** **meta_data** field description

   +-------------------------------+-----------------------+-------------------------------------------------------------------------+
   | Parameter                     | Type                  | Description                                                             |
   +===============================+=======================+=========================================================================+
   | metadata_bandwidth_share_type | String                | **Definition**                                                          |
   |                               |                       |                                                                         |
   |                               |                       | Specifies the bandwidth sharing type in the bandwidth scaling policy.   |
   |                               |                       |                                                                         |
   |                               |                       | **Range**                                                               |
   |                               |                       |                                                                         |
   |                               |                       | -  **PER**: dedicated                                                   |
   |                               |                       | -  **WHOLE**: shared                                                    |
   +-------------------------------+-----------------------+-------------------------------------------------------------------------+
   | metadata_eip_id               | String                | **Definition**                                                          |
   |                               |                       |                                                                         |
   |                               |                       | Specifies the EIP ID for the bandwidth in the bandwidth scaling policy. |
   |                               |                       |                                                                         |
   |                               |                       | **Range**                                                               |
   |                               |                       |                                                                         |
   |                               |                       | N/A                                                                     |
   +-------------------------------+-----------------------+-------------------------------------------------------------------------+
   | metadata_eip_address          | String                | **Definition**                                                          |
   |                               |                       |                                                                         |
   |                               |                       | Specifies the EIP for the bandwidth in the bandwidth scaling policy.    |
   |                               |                       |                                                                         |
   |                               |                       | **Range**                                                               |
   |                               |                       |                                                                         |
   |                               |                       | N/A                                                                     |
   +-------------------------------+-----------------------+-------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "limit": 20,
       "total_number": 3,
       "start_number": 0,
       "scaling_policies": [
           {
               "scaling_policy_id": "803a35a5-38fb-4d27-a042-496c14bc1fb8",
               "scaling_policy_name": "as-policy-7a75",
               "scaling_resource_id": "8ade64b5-d685-40b8-8582-4ce306ea37a6",
               "scaling_resource_type": "SCALING_GROUP",
               "scaling_policy_type": "RECURRENCE",
               "scheduled_policy": {
                   "launch_time": "03:30",
                   "recurrence_type": "Daily",
                   "start_time": "2017-08-28T03:08Z",
                   "end_time": "2017-09-01T03:08Z"
               },
               "cool_down_time": 900,
               "scaling_policy_action": {
                   "operation": "ADD",
                   "size": 1
               },
               "policy_status": "INSERVICE",
               "create_time": "2017-08-31T03:02:41Z"
           },
           {
               "scaling_policy_id": "535fd67e-276b-409c-879e-52f4e09e14bb",
               "scaling_policy_name": "as-policy-7a75",
               "scaling_resource_id": "8ade64b5-d685-40b8-8582-4ce306ea37a6",
               "scaling_resource_type": "SCALING_GROUP",
               "scaling_policy_type": "RECURRENCE",
               "scheduled_policy": {
                   "launch_time": "21:30",
                   "recurrence_type": "Daily",
                   "start_time": "2017-08-27T21:08Z",
                   "end_time": "2017-08-31T21:08Z"
               },
               "cool_down_time": 900,
               "scaling_policy_action": {
                   "operation": "ADD",
                   "size": 1
               },
               "policy_status": "INSERVICE",
               "create_time": "2017-08-31T07:35:05Z"
           },
           {
               "scaling_policy_id": "37df92f8-73cb-469e-a420-c15f445d2ee1",
               "scaling_policy_name": "as-policy-7a75",
               "scaling_resource_id": "8ade64b5-d685-40b8-8582-4ce306ea37a6",
               "scaling_resource_type": "SCALING_GROUP",
               "scaling_policy_type": "RECURRENCE",
               "scheduled_policy": {
                   "launch_time": "22:30",
                   "recurrence_type": "Daily",
                   "start_time": "2017-08-27T22:08Z",
                   "end_time": "2017-08-31T22:08Z"
               },
               "cool_down_time": 900,
               "scaling_policy_action": {
                   "operation": "ADD",
                   "size": 1
               },
               "policy_status": "INSERVICE",
               "create_time": "2017-08-31T07:41:06Z"
           }
       ]
   }

Returned Values
---------------

-  Normal

   200

-  Abnormal

   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | Returned Values                   | Description                                                                                |
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
