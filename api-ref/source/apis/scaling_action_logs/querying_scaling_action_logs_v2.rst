:original_name: as_06_0602.html

.. _as_06_0602:

Querying Scaling Action Logs (V2)
=================================

Function
--------

This API is used to query scaling action logs based on search criteria. The scaling actions include increasing instances and migrating instances to balance load. The results are displayed by page.

-  The difference between the V2 and V1 APIs for querying scaling action logs is that V2 displays more detailed action logs, such as ELB migration logs.
-  Search criteria can be the start time, end time, start line number, number of records, and scaling action type.
-  If no search criteria are specified, a maximum of 20 scaling action logs can be queried by default.

URI
---

GET /autoscaling-api/v2/{project_id}/scaling_activity_log/{scaling_group_id}

.. note::

   You can type the question mark (?) and ampersand (&) at the end of the URI to define multiple search criteria. Scaling action logs can be searched by all optional parameters in the following table. For details, see the example request.

.. table:: **Table 1** Parameter description

   +------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory       | Type            | Description                                                                                                                                 |
   +==================+=================+=================+=============================================================================================================================================+
   | project_id       | Yes             | String          | Specifies the project ID.                                                                                                                   |
   +------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | scaling_group_id | Yes             | String          | Specifies the AS group ID.                                                                                                                  |
   +------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | log_id           | No              | String          | Specifies the scaling action log ID.                                                                                                        |
   +------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | start_time       | No              | String          | Specifies the start time that complies with UTC for querying scaling action logs. The format of the start time is **yyyy-MM-ddThh:mm:ssZ**. |
   +------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | end_time         | No              | String          | Specifies the end time that complies with UTC for querying scaling action logs. The format of the end time is **yyyy-MM-ddThh:mm:ssZ**.     |
   +------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | start_number     | No              | Integer         | Specifies the start line number. The default value is **0**. The minimum parameter value is **0**.                                          |
   +------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | limit            | No              | Integer         | Specifies the number of query records. The default value is **20**. The value ranges from 0 to 100.                                         |
   +------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | type             | No              | String          | Specifies the types of the scaling actions to be queried. Different types are separated by commas (,).                                      |
   |                  |                 |                 |                                                                                                                                             |
   |                  |                 |                 | -  **NORMAL**: indicates a common scaling action.                                                                                           |
   |                  |                 |                 | -  **MANUAL_REMOVE**: indicates manually removing instances from an AS group.                                                               |
   |                  |                 |                 | -  **MANUAL_DELETE**: indicates manually removing and deleting instances from an AS group.                                                  |
   |                  |                 |                 | -  **MANUAL_ADD**: indicates manually adding instances to an AS group.                                                                      |
   |                  |                 |                 | -  **ELB_CHECK_DELETE**: indicates that instances are removed from an AS group and deleted based on the ELB health check result.            |
   |                  |                 |                 | -  **AUDIT_CHECK_DELETE**: indicates that instances are removed from an AS group and deleted based on the audit.                            |
   |                  |                 |                 | -  **DIFF**: indicates that the number of expected instances is different from the actual number of instances.                              |
   |                  |                 |                 | -  **MODIFY_ELB**: indicates the load balancer migration.                                                                                   |
   +------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | status           | No              | String          | Specifies the status of the scaling action.                                                                                                 |
   |                  |                 |                 |                                                                                                                                             |
   |                  |                 |                 | -  **SUCCESS**: The scaling action has been performed.                                                                                      |
   |                  |                 |                 | -  **FAIL**: Performing the scaling action failed.                                                                                          |
   |                  |                 |                 | -  **DOING**: The scaling action is being performed.                                                                                        |
   +------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

None

Example Request
---------------

This example queries the scaling action logs of the AS group with ID **e5d27f5c-dd76-4a61-b4bc-a67c5686719a**. The start time is 2018-11-22T00:00:00Z, and the end time is 2018-11-22T14:00:00Z.

.. code-block:: text

   GET https://{Endpoint}/autoscaling-api/v2/{project_id}/scaling_activity_log/e5d27f5c-dd76-4a61-b4bc-a67c5686719a?start_time=2018-11-22T00:00:00Z&end_time=2018-11-22T14:00:00Z

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
   | scaling_activity_log | Array of :ref:`scaling_activity_log <as_06_0602__table5100505111129>` objects | Specifies scaling action logs. For details, see :ref:`Table 3 <as_06_0602__table5100505111129>`. |
   +----------------------+-------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+

.. _as_06_0602__table5100505111129:

.. table:: **Table 3** **scaling_activity_log** field description

   +------------------------+-------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter              | Type                                                                    | Description                                                                                                                                                                                            |
   +========================+=========================================================================+========================================================================================================================================================================================================+
   | status                 | String                                                                  | Specifies the status of the scaling action.                                                                                                                                                            |
   |                        |                                                                         |                                                                                                                                                                                                        |
   |                        |                                                                         | -  **SUCCESS**: The scaling action has been performed.                                                                                                                                                 |
   |                        |                                                                         | -  **FAIL**: Performing the scaling action failed.                                                                                                                                                     |
   |                        |                                                                         | -  **DOING**: The scaling action is being performed.                                                                                                                                                   |
   +------------------------+-------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | start_time             | String                                                                  | Specifies the start time of the scaling action. The time format must comply with UTC.                                                                                                                  |
   +------------------------+-------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | end_time               | String                                                                  | Specifies the end time of the scaling action. The time format must comply with UTC.                                                                                                                    |
   +------------------------+-------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                     | String                                                                  | Specifies the scaling action log ID.                                                                                                                                                                   |
   +------------------------+-------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_removed_list  | Array of :ref:`scaling_instance <as_06_0602__table54708193137>` objects | Specifies names of the ECSs that are removed from the AS group in a scaling action. For details, see :ref:`Table 4 <as_06_0602__table54708193137>`.                                                    |
   +------------------------+-------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_deleted_list  | Array of :ref:`scaling_instance <as_06_0602__table54708193137>` objects | Specifies names of the ECSs that are removed from the AS group and deleted in a scaling action. For details, see :ref:`Table 4 <as_06_0602__table54708193137>`.                                        |
   +------------------------+-------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_added_list    | Array of :ref:`scaling_instance <as_06_0602__table54708193137>` objects | Specifies names of the ECSs that are added to the AS group in a scaling action. For details, see :ref:`Table 4 <as_06_0602__table54708193137>`.                                                        |
   +------------------------+-------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_failed_list   | Array of :ref:`scaling_instance <as_06_0602__table54708193137>` objects | Specifies the ECSs for which a scaling action fails. For details, see :ref:`Table 4 <as_06_0602__table54708193137>`.                                                                                   |
   +------------------------+-------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_standby_list  | Array of :ref:`scaling_instance <as_06_0602__table54708193137>` objects | Specifies the ECSs that are set to standby mode or for which standby mode is canceled in a scaling action. For details, see :ref:`Table 4 <as_06_0602__table54708193137>`. This parameter is reserved. |
   +------------------------+-------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | scaling_value          | Integer                                                                 | Specifies the number of added or deleted instances during the scaling.                                                                                                                                 |
   +------------------------+-------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description            | String                                                                  | Specifies the description of the scaling action.                                                                                                                                                       |
   +------------------------+-------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_value         | Integer                                                                 | Specifies the number of instances in the AS group.                                                                                                                                                     |
   +------------------------+-------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | desire_value           | Integer                                                                 | Specifies the expected number of instances for the scaling action.                                                                                                                                     |
   +------------------------+-------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | lb_bind_success_list   | Array of :ref:`modify_lb <as_06_0602__table1680205901311>` objects      | Specifies the load balancers that are bound to the AS group. For details, see :ref:`Table 5 <as_06_0602__table1680205901311>`.                                                                         |
   +------------------------+-------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | lb_bind_failed_list    | Array of :ref:`modify_lb <as_06_0602__table1680205901311>` objects      | Specifies the load balancers that failed to be bound to the AS group. For details, see :ref:`Table 5 <as_06_0602__table1680205901311>`.                                                                |
   +------------------------+-------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | lb_unbind_success_list | Array of :ref:`modify_lb <as_06_0602__table1680205901311>` objects      | Specifies the load balancers that are unbound from the AS group. For details, see :ref:`Table 5 <as_06_0602__table1680205901311>`.                                                                     |
   +------------------------+-------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | lb_unbind_failed_list  | Array of :ref:`modify_lb <as_06_0602__table1680205901311>` objects      | Specifies the load balancers that failed to be unbound from the AS group. For details, see :ref:`Table 5 <as_06_0602__table1680205901311>`.                                                            |
   +------------------------+-------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type                   | String                                                                  | Specifies the type of the scaling action.                                                                                                                                                              |
   +------------------------+-------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _as_06_0602__table54708193137:

.. table:: **Table 4** **scaling_instance** field description

   +-----------------+--------+----------------------------------------------------------+
   | Parameter       | Type   | Description                                              |
   +=================+========+==========================================================+
   | instance_name   | String | Specifies the ECS name.                                  |
   +-----------------+--------+----------------------------------------------------------+
   | instance_id     | String | Specifies the ECS ID.                                    |
   +-----------------+--------+----------------------------------------------------------+
   | failed_reason   | String | Specifies the cause of the instance scaling failure.     |
   +-----------------+--------+----------------------------------------------------------+
   | failed_details  | String | Specifies details of the instance scaling failure.       |
   +-----------------+--------+----------------------------------------------------------+
   | instance_config | String | Specifies the information about instance configurations. |
   +-----------------+--------+----------------------------------------------------------+

.. _as_06_0602__table1680205901311:

.. table:: **Table 5** **modify_lb** field description

   +----------------+-----------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
   | Parameter      | Type                                                      | Description                                                                                                          |
   +================+===========================================================+======================================================================================================================+
   | lbaas_listener | :ref:`lbaas_listener <as_06_0602__table153260162>` object | Specifies information about an enhanced load balancer. For details, see :ref:`Table 6 <as_06_0602__table153260162>`. |
   +----------------+-----------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
   | listener       | String                                                    | Specifies information about a classic load balancer.                                                                 |
   +----------------+-----------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
   | failed_reason  | String                                                    | Specifies the cause of a load balancer migration failure.                                                            |
   +----------------+-----------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
   | failed_details | String                                                    | Specifies the details of a load balancer migration failure.                                                          |
   +----------------+-----------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+

.. _as_06_0602__table153260162:

.. table:: **Table 6** **lbaas_listener** field description

   +---------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Type    | Description                                                                                                                                                  |
   +===============+=========+==============================================================================================================================================================+
   | listener_id   | String  | Specifies the listener ID.                                                                                                                                   |
   +---------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | pool_id       | String  | Specifies the backend ECS group ID.                                                                                                                          |
   +---------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | protocol_port | Integer | Specifies the backend protocol port, which is the port on which a backend ECS listens for traffic.                                                           |
   +---------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | weight        | Integer | Specifies the weight, which determines the portion of requests a backend ECS processes when being compared to other backend ECSs added to the same listener. |
   +---------------+---------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "limit": 20,
       "scaling_activity_log": [
       {
         "id": "8753a18c-931d-4cb8-8d49-6c99396af348",
         "instance_value": 0,
         "desire_value": 0,
         "scaling_value": 0,
         "start_time": "2018-11-22T13:46:20Z",
         "end_time": "2018-11-22T13:47:38Z",
         "status": "SUCCESS",
         "lb_bind_success_list": [
           {
             "lbaas_listener": {
               "weight": 1,
               "listener_id": null,
               "pool_id": "0f0a9dd8-2e1d-4432-8ca2-49adc75aa662",
               "protocol_port": 82
             }
           }
         ],
         "lb_bind_failed_list": [],
         "lb_unbind_success_list": [],
         "lb_unbind_failed_list": [],
         "type": "MODIFY_ELB"
       },
       {
         "id": "44152cf2-a005-4507-b6e9-66a2a64eff52",
         "instance_value": 0,
         "desire_value": 1,
         "scaling_value": 1,
         "start_time": "2018-11-22T13:44:22Z",
         "end_time": "2018-11-22T13:46:02Z",
         "instance_added_list": [
           {
             "instance_id": "8e273bac-d303-46dc-9883-628be2294bdf",
             "instance_name": "as-config-t66a_9W8L9SSK"
           }
         ],
         "instance_deleted_list": [],
         "instance_removed_list": [],
         "instance_failed_list": [],
         "status": "SUCCESS",
         "description": "{\"reason\":[{\"change_reason\":\"MANNUAL\",\"old_value\":0,\"change_time\":\"2018-11-22T13:44:19Z\",\"new_value\":1}]}",
         "type": "NORMAL"
       }
   ],
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
