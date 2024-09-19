:original_name: as_06_0501.html

.. _as_06_0501:

Querying AS Policy Execution Logs
=================================

Function
--------

This API is used to query the historical records of AS policy execution based on search criteria. The results are displayed by page.

-  Search criteria can be the log ID, AS resource type, AS resource ID, policy execution type, start time, end time, start line number, and number of records.
-  If no search criteria are specified, a maximum of 20 AS policy execution logs can be queried by default.

URI
---

GET /autoscaling-api/v1/{project_id}/scaling_policy_execute_log/{scaling_policy_id}

.. note::

   You can type the question mark (?) and ampersand (&) at the end of the URI to define multiple search criteria. AS policy execution logs can be searched by all optional parameters in the following table. For details, see the example request.

.. table:: **Table 1** Parameter description

   +-----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type            | Description                                                                                                                                      |
   +=======================+=================+=================+==================================================================================================================================================+
   | project_id            | Yes             | String          | Specifies the project ID.                                                                                                                        |
   +-----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | scaling_policy_id     | Yes             | String          | Specifies the AS policy ID.                                                                                                                      |
   +-----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | log_id                | No              | String          | Specifies the ID of an AS policy execution log.                                                                                                  |
   +-----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | scaling_resource_type | No              | String          | Specifies the scaling resource type.                                                                                                             |
   |                       |                 |                 |                                                                                                                                                  |
   |                       |                 |                 | -  AS group: **SCALING_GROUP**                                                                                                                   |
   |                       |                 |                 | -  Bandwidth: **BANDWIDTH**                                                                                                                      |
   +-----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | scaling_resource_id   | No              | String          | Specifies the scaling resource ID.                                                                                                               |
   +-----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | execute_type          | No              | String          | Specifies the AS policy execution type.                                                                                                          |
   |                       |                 |                 |                                                                                                                                                  |
   |                       |                 |                 | -  **SCHEDULED**: automatically triggered at a specified time point                                                                              |
   |                       |                 |                 | -  **RECURRENCE**: automatically triggered at a specified time period                                                                            |
   |                       |                 |                 | -  **ALARM**: alarm-triggered                                                                                                                    |
   |                       |                 |                 | -  **MANUAL**: manually triggered                                                                                                                |
   +-----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | start_time            | No              | String          | Specifies the start time that complies with UTC for querying AS policy execution logs. The format of the start time is **yyyy-MM-ddThh:mm:ssZ**. |
   +-----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | end_time              | No              | String          | Specifies the end time that complies with UTC for querying AS policy execution logs. The format of the end time is **yyyy-MM-ddThh:mm:ssZ**.     |
   +-----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | start_number          | No              | Integer         | Specifies the start line number. The default value is **0**. The minimum parameter value is **0**.                                               |
   +-----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit                 | No              | Integer         | Specifies the number of query records. The default value is **20**. The value range is 0 to 100.                                                 |
   +-----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

None

Example Request
---------------

This example queries the execution logs of the AS policy with ID **05545d3d-ccf9-4bca-ae4f-1e5e73ca0bf6**.

.. code-block:: text

   GET https://{Endpoint}/autoscaling-api/v1/edcb94a885a84ed3a3fdf8ea4d2741da/scaling_policy_execute_log/05545d3d-ccf9-4bca-ae4f-1e5e73ca0bf6

Response
--------

.. table:: **Table 2** Response parameters

   +----------------------------+------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------+
   | Parameter                  | Type                                                                               | Description                                                                                              |
   +============================+====================================================================================+==========================================================================================================+
   | total_number               | Integer                                                                            | Specifies the total number of query records.                                                             |
   +----------------------------+------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------+
   | start_number               | Integer                                                                            | Specifies the start line number.                                                                         |
   +----------------------------+------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------+
   | limit                      | Integer                                                                            | Specifies the maximum number of resources to be queried.                                                 |
   +----------------------------+------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------+
   | scaling_policy_execute_log | Array of :ref:`scaling_policy_execute_log <as_06_0501__table253953315328>` objects | Specifies the AS policy execution logs. For details, see :ref:`Table 3 <as_06_0501__table253953315328>`. |
   +----------------------------+------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------+

.. _as_06_0501__table253953315328:

.. table:: **Table 3** **scaling_policy_execute_log** field description

   +-----------------------+-----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                  | Description                                                                                                                                 |
   +=======================+=======================================================================+=============================================================================================================================================+
   | status                | String                                                                | Specifies the AS policy execution status.                                                                                                   |
   |                       |                                                                       |                                                                                                                                             |
   |                       |                                                                       | -  **SUCCESS**: The AS policy has been executed.                                                                                            |
   |                       |                                                                       | -  **FAIL**: Executing the AS policy failed.                                                                                                |
   |                       |                                                                       | -  **EXECUTING**: The AS policy is being executed.                                                                                          |
   +-----------------------+-----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | failed_reason         | String                                                                | Specifies the AS policy execution failure.                                                                                                  |
   +-----------------------+-----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | execute_type          | String                                                                | Specifies the AS policy execution type.                                                                                                     |
   |                       |                                                                       |                                                                                                                                             |
   |                       |                                                                       | -  **SCHEDULED**: automatically triggered at a specified time point                                                                         |
   |                       |                                                                       | -  **RECURRENCE**: automatically triggered at a specified time period                                                                       |
   |                       |                                                                       | -  **ALARM**: alarm-triggered                                                                                                               |
   |                       |                                                                       | -  **MANUAL**: manually triggered                                                                                                           |
   +-----------------------+-----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | execute_time          | String                                                                | Specifies the time when an AS policy was executed. The time format complies with UTC.                                                       |
   +-----------------------+-----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | id                    | String                                                                | Specifies the ID of an AS policy execution log.                                                                                             |
   +-----------------------+-----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | tenant_id             | String                                                                | Specifies the project ID.                                                                                                                   |
   +-----------------------+-----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | scaling_policy_id     | String                                                                | Specifies the AS policy ID.                                                                                                                 |
   +-----------------------+-----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | scaling_resource_type | String                                                                | Specifies the scaling resource type.                                                                                                        |
   |                       |                                                                       |                                                                                                                                             |
   |                       |                                                                       | -  AS group: **SCALING_GROUP**                                                                                                              |
   |                       |                                                                       | -  Bandwidth: **BANDWIDTH**                                                                                                                 |
   +-----------------------+-----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | scaling_resource_id   | String                                                                | Specifies the scaling resource ID.                                                                                                          |
   +-----------------------+-----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | old_value             | String                                                                | Specifies the source value.                                                                                                                 |
   +-----------------------+-----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | desire_value          | String                                                                | Specifies the target value.                                                                                                                 |
   +-----------------------+-----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | limit_value           | String                                                                | Specifies the operation restrictions.                                                                                                       |
   |                       |                                                                       |                                                                                                                                             |
   |                       |                                                                       | If **scaling_resource_type** is set to **BANDWIDTH** and **operation** is not **SET**, this parameter takes effect and the unit is Mbit/s.  |
   |                       |                                                                       |                                                                                                                                             |
   |                       |                                                                       | In this case:                                                                                                                               |
   |                       |                                                                       |                                                                                                                                             |
   |                       |                                                                       | -  If **operation** is set to **ADD**, this parameter indicates the maximum bandwidth allowed.                                              |
   |                       |                                                                       | -  If **operation** is set to **REDUCE**, this parameter indicates the minimum bandwidth allowed.                                           |
   +-----------------------+-----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | type                  | String                                                                | Specifies the AS policy execution type.                                                                                                     |
   |                       |                                                                       |                                                                                                                                             |
   |                       |                                                                       | -  **ADD**: indicates adding instances.                                                                                                     |
   |                       |                                                                       | -  **REMOVE**: indicates reducing instances.                                                                                                |
   |                       |                                                                       | -  **SET**: indicates setting the number of instances to a specified value.                                                                 |
   +-----------------------+-----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | job_records           | Array of :ref:`job_records <as_06_0501__table10573113383219>` objects | Specifies the tasks contained in a scaling action based on an AS policy. For details, see :ref:`Table 4 <as_06_0501__table10573113383219>`. |
   +-----------------------+-----------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+

.. _as_06_0501__table10573113383219:

.. table:: **Table 4** **job_records** field description

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                     |
   +=======================+=======================+=================================================================================================+
   | job_name              | String                | Specifies the task name.                                                                        |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+
   | record_type           | String                | Specifies the record type.                                                                      |
   |                       |                       |                                                                                                 |
   |                       |                       | -  **API**: API calling type                                                                    |
   |                       |                       | -  **MEG**: message type                                                                        |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+
   | record_time           | String                | Specifies the record time.                                                                      |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+
   | request               | String                | Specifies the request body. This parameter is valid only if **record_type** is set to **API**.  |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+
   | response              | String                | Specifies the response body. This parameter is valid only if **record_type** is set to **API**. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+
   | code                  | String                | Specifies the returned code. This parameter is valid only if **record_type** is set to **API**. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+
   | message               | String                | Specifies the message. This parameter is valid only if **record_type** is set to **MEG**.       |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+
   | job_status            | String                | Specifies the execution status of the task.                                                     |
   |                       |                       |                                                                                                 |
   |                       |                       | -  **SUCCESS**: The task is successfully executed.                                              |
   |                       |                       | -  **FAIL**: The task failed to be executed.                                                    |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+

.. table:: **Table 5** **meta_data** field description

   +-------------------------------+--------+-------------------------------------------------------------------------+
   | Parameter                     | Type   | Description                                                             |
   +===============================+========+=========================================================================+
   | metadata_bandwidth_share_type | String | Specifies the bandwidth sharing type in the bandwidth scaling policy.   |
   +-------------------------------+--------+-------------------------------------------------------------------------+
   | metadata_eip_id               | String | Specifies the EIP ID for the bandwidth in the bandwidth scaling policy. |
   +-------------------------------+--------+-------------------------------------------------------------------------+
   | metadataeip_address           | String | Specifies the EIP for the bandwidth in the bandwidth scaling policy.    |
   +-------------------------------+--------+-------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
     "limit": 20,
     "scaling_policy_execute_log": [
       {
         "id": "b86e4175-30cb-4b1e-a332-83f9ee472c58",
         "status": "SUCCESS",
         "type": "REMOVE",
         "tenant_id": "0428982a1b8039f42f01c005edde7c0d",
         "scaling_resource_type": "SCALING_GROUP",
         "scaling_resource_id": "1f2d3e73-7ef6-40b3-a8fa-514b68eccaa7",
         "scaling_policy_id": "05545d3d-ccf9-4bca-ae4f-1e5e73ca0bf6",
         "old_value": "1",
         "desire_value": "0",
         "limit_value": "0",
         "execute_time": "2019-03-18T16:00:00Z",
         "execute_type": "RECURRENCE",
         "job_records": [
           {
             "message": "modify desire number of scaling group",
             "job_name": "ADJUST_VM_NUMBERS",
             "record_type": "MEG",
             "record_time": "2019-03-18T16:00:00Z",
             "job_status": "SUCCESS"
           }
         ]
       }
     ],
     "total_number": 1,
     "start_number": 0
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
