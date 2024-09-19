:original_name: as_06_0601.html

.. _as_06_0601:

Querying Scaling Action Logs
============================

Function
--------

This API is used to query scaling action logs based on search criteria. The results are displayed by page.

-  Search criteria can be the start time, end time, start line number, and number of records.
-  If no search criteria are specified, a maximum of 20 scaling action logs can be queried by default.

URI
---

GET /autoscaling-api/v1/{project_id}/scaling_activity_log/{scaling_group_id}

.. note::

   You can type the question mark (?) and ampersand (&) at the end of the URI to define multiple search criteria. Scaling action logs can be searched by all optional parameters in the following table. For details, see the example request.

.. table:: **Table 1** Parameter description

   +------------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory | Type    | Description                                                                                                                                 |
   +==================+===========+=========+=============================================================================================================================================+
   | project_id       | Yes       | String  | Specifies the project ID.                                                                                                                   |
   +------------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | scaling_group_id | Yes       | String  | Specifies the AS group ID.                                                                                                                  |
   +------------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | start_time       | No        | String  | Specifies the start time that complies with UTC for querying scaling action logs. The format of the start time is **yyyy-MM-ddThh:mm:ssZ**. |
   +------------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | end_time         | No        | String  | Specifies the end time that complies with UTC for querying scaling action logs. The format of the end time is **yyyy-MM-ddThh:mm:ssZ**.     |
   +------------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | start_number     | No        | Integer | Specifies the start line number. The default value is **0**. The minimum parameter value is **0**.                                          |
   +------------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | limit            | No        | Integer | Specifies the number of query records. The default value is **20**. The value ranges from 0 to 100.                                         |
   +------------------+-----------+---------+---------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

None

Example Request
---------------

This example queries the scaling action logs of the AS group with ID **e5d27f5c-dd76-4a61-b4bc-a67c5686719a**.

.. code-block:: text

   GET https://{Endpoint}/autoscaling-api/v1/{project_id}/scaling_activity_log/e5d27f5c-dd76-4a61-b4bc-a67c5686719a

Response
--------

.. table:: **Table 2** Response parameters

   +----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | Parameter            | Type                                                                          | Description                                                                                      |
   +======================+===============================================================================+==================================================================================================+
   | total_number         | Integer                                                                       | Specifies the total number of query records.                                                     |
   +----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | start_number         | Integer                                                                       | Specifies the start line number.                                                                 |
   +----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | limit                | Integer                                                                       | Specifies the maximum number of resources to be queried.                                         |
   +----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
   | scaling_activity_log | Array of :ref:`scaling_activity_log <as_06_0601__table5100505111129>` objects | Specifies scaling action logs. For details, see :ref:`Table 3 <as_06_0601__table5100505111129>`. |
   +----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+

.. _as_06_0601__table5100505111129:

.. table:: **Table 3** **scaling_activity_log** field description

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                         |
   +=======================+=======================+=====================================================================================================================================================================+
   | status                | String                | Specifies the status of the scaling action.                                                                                                                         |
   |                       |                       |                                                                                                                                                                     |
   |                       |                       | -  **SUCCESS**: The scaling action has been performed.                                                                                                              |
   |                       |                       | -  **FAIL**: Performing the scaling action failed.                                                                                                                  |
   |                       |                       | -  **DOING**: The scaling action is being performed.                                                                                                                |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | start_time            | String                | Specifies the start time of the scaling action. The time format must comply with UTC.                                                                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | end_time              | String                | Specifies the end time of the scaling action. The time format must comply with UTC.                                                                                 |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                    | String                | Specifies the scaling action log ID.                                                                                                                                |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_removed_list | String                | Specifies the names of the instances removed from the AS group after the scaling action is complete. The instance names are separated using commas (,).             |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_deleted_list | String                | Specifies the names of the instances removed and deleted from the AS group after the scaling action is complete. The instance names are separated using commas (,). |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_added_list   | String                | Specifies the names of the instances added to the AS group after the scaling action is complete. The instance names are separated using commas (,).                 |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | scaling_value         | Integer               | Specifies the number of added or removed instances in the scaling action.                                                                                           |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | Specifies the description of the scaling action.                                                                                                                    |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_value        | Integer               | Specifies the number of instances in the AS group.                                                                                                                  |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | desire_value          | Integer               | Specifies the expected number of instances for the scaling action.                                                                                                  |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
     "limit": 20,
     "scaling_activity_log": [
       {
         "id": "66e0f775-c4ac-4b52-9d5c-f93ba217aa5f",
         "instance_value": 1,
         "desire_value": 0,
         "scaling_value": 1,
         "start_time": "2019-03-18T16:00:11Z",
         "end_time": "2019-03-18T16:00:32Z",
         "instance_added_list": null,
         "instance_deleted_list": "as-config-bblh-ONQE551S",
         "instance_removed_list": null,
         "status": "SUCCESS",
         "description": "{\"reason\":[{\"change_reason\":\"RECURRENCE\",\"old_value\":1,\"scaling_policy_name\":\"as-policy-bvfk\",\"change_time\":\"2019-03-18T16:00:00Z\",\"new_value\":0,\"scaling_policy_id\":\"05545d3d-ccf9-4bca-ae4f-1e5e73ca0bf6\"}]}"
       },
       {
         "id": "c3a1fff6-84a3-4cbc-8ac0-e3b0f645ecd8",
         "instance_value": 0,
         "desire_value": 1,
         "scaling_value": 1,
         "start_time": "2019-03-16T10:21:11Z",
         "end_time": "2019-03-16T10:25:12Z",
         "instance_added_list": "as-config-bblh-ONQE551S",
         "instance_deleted_list": null,
         "instance_removed_list": null,
         "status": "SUCCESS",
         "description": "{\"reason\":[{\"change_reason\":\"DIFF\",\"old_value\":0,\"change_time\":\"2019-03-16T10:21:11Z\",\"new_value\":1}]}"
       }],
       "total_number": 2,
       "start_number": 0
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
