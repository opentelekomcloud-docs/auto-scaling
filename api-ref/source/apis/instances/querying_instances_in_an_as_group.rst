:original_name: as_06_0301.html

.. _as_06_0301:

Querying Instances in an AS Group
=================================

Function
--------

This API is used to query instances in an AS group based on search criteria. The results are displayed by page.

-  Search criteria can be the instance lifecycle status, instance health status, instance protection status, start line number, and number of records in the AS group.
-  If no search criteria are specified, a maximum of 20 instances in an AS group can be queried by default.

URI
---

GET /autoscaling-api/v1/{project_id}/scaling_group_instance/{scaling_group_id}/list

.. note::

   You can type the question mark (?) and ampersand (&) at the end of the URI to define multiple search criteria. Instances in an AS group can be searched by all optional parameters in the following table. For details, see the example request.

.. table:: **Table 1** Parameter description

   +---------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------+
   | Parameter                 | Mandatory       | Type            | Description                                                                                         |
   +===========================+=================+=================+=====================================================================================================+
   | project_id                | Yes             | String          | Specifies the project ID.                                                                           |
   +---------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------+
   | scaling_group_id          | Yes             | String          | Specifies the AS group ID.                                                                          |
   +---------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------+
   | life_cycle_state          | No              | String          | Specifies the instance lifecycle status in the AS group.                                            |
   |                           |                 |                 |                                                                                                     |
   |                           |                 |                 | -  **INSERVICE**: The instance is enabled.                                                          |
   |                           |                 |                 | -  **PENDING**: The instance is being added to the AS group.                                        |
   |                           |                 |                 | -  **REMOVING**: The instance is being removed from the AS group.                                   |
   +---------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------+
   | health_status             | No              | String          | Specifies the instance health status.                                                               |
   |                           |                 |                 |                                                                                                     |
   |                           |                 |                 | -  **INITIALIZING**: The instance is initializing.                                                  |
   |                           |                 |                 | -  **NORMAL**: The instance is normal.                                                              |
   |                           |                 |                 | -  **ERROR**: The instance is abnormal.                                                             |
   +---------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------+
   | protect_from_scaling_down | No              | String          | Specifies the instance protection status.                                                           |
   |                           |                 |                 |                                                                                                     |
   |                           |                 |                 | -  **true**: Instance protection is enabled.                                                        |
   |                           |                 |                 | -  **false**: Instance protection is disabled.                                                      |
   +---------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------+
   | start_number              | No              | Integer         | Specifies the start line number. The default value is **0**. The minimum parameter value is **0**.  |
   +---------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------+
   | limit                     | No              | Integer         | Specifies the number of query records. The default value is **20**. The value ranges from 0 to 100. |
   +---------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------+

Request
-------

None

Example Request
---------------

This example queries enabled, healthy instances in the AS group with ID **e5d27f5c-dd76-4a61-b4bc-a67c5686719a**.

.. code-block:: text

   GET https://{Endpoint}/autoscaling-api/v1/{project_id}/scaling_group_instance/e5d27f5c-dd76-4a61-b4bc-a67c5686719a/list?life_cycle_state=INSERVICE&health_status=NORMAL

Response
--------

.. table:: **Table 2** Response parameters

   +-------------------------+----------------------------------------------------------------------------------+----------------------------------------------------------+
   | Parameter               | Type                                                                             | Description                                              |
   +=========================+==================================================================================+==========================================================+
   | total_number            | Integer                                                                          | Specifies the total number of query records.             |
   +-------------------------+----------------------------------------------------------------------------------+----------------------------------------------------------+
   | start_number            | Integer                                                                          | Specifies the start line number.                         |
   +-------------------------+----------------------------------------------------------------------------------+----------------------------------------------------------+
   | limit                   | Integer                                                                          | Specifies the maximum number of resources to be queried. |
   +-------------------------+----------------------------------------------------------------------------------+----------------------------------------------------------+
   | scaling_group_instances | Array of :ref:`scaling_group_instances <as_06_0301__table4301093319610>` objects | Specifies details about the instances in the AS group.   |
   +-------------------------+----------------------------------------------------------------------------------+----------------------------------------------------------+

.. _as_06_0301__table4301093319610:

.. table:: **Table 3** **scaling_group_instances** field description

   +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
   | Parameter                  | Type                  | Description                                                                                           |
   +============================+=======================+=======================================================================================================+
   | instance_id                | String                | Specifies the instance ID.                                                                            |
   +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
   | instance_name              | String                | Specifies the instance name.                                                                          |
   +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
   | scaling_group_id           | String                | Specifies the ID of the AS group to which the instance belongs.                                       |
   +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
   | scaling_group_name         | String                | Specifies the name of the AS group to which the instance belongs.                                     |
   |                            |                       |                                                                                                       |
   |                            |                       | Supports fuzzy search.                                                                                |
   +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
   | life_cycle_state           | String                | Specifies the instance lifecycle status in the AS group.                                              |
   |                            |                       |                                                                                                       |
   |                            |                       | -  **INSERVICE**: The instance is enabled.                                                            |
   |                            |                       | -  **PENDING**: The instance is being added to the AS group.                                          |
   |                            |                       | -  **REMOVING**: The instance is being removed from the AS group.                                     |
   +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
   | health_status              | String                | Specifies the instance health status.                                                                 |
   |                            |                       |                                                                                                       |
   |                            |                       | -  **INITIALIZING**: The instance is being initialized.                                               |
   |                            |                       | -  **NORMAL**: The instance is functional.                                                            |
   |                            |                       | -  **ERROR**: The instance is faulty.                                                                 |
   +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
   | scaling_configuration_name | String                | Specifies the AS configuration name.                                                                  |
   +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
   | scaling_configuration_id   | String                | Specifies the AS configuration ID.                                                                    |
   |                            |                       |                                                                                                       |
   |                            |                       | If the returned value is not empty, the instance is an ECS automatically created in a scaling action. |
   |                            |                       |                                                                                                       |
   |                            |                       | If the returned value is empty, the instance is an ECS manually added to the AS group.                |
   +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
   | create_time                | String                | Specifies the time when the instance is added to the AS group. The time format complies with UTC.     |
   +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------+
   | protect_from_scaling_down  | Boolean               | Specifies the instance protection status.                                                             |
   +----------------------------+-----------------------+-------------------------------------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "limit": 10,
       "total_number": 1,
       "start_number": 0,
       "scaling_group_instances": [
           {
               "instance_id": "b25c1589-c96c-465b-9fef-d06540d1945c",
               "scaling_group_id": "e5d27f5c-dd76-4a61-b4bc-a67c5686719a",
               "scaling_group_name": "discuz",
               "life_cycle_state": "INSERVICE",
               "health_status": "NORMAL",
               "scaling_configuration_name": "discuz",
               "scaling_configuration_id": "ca3dcd84-d197-4c4f-af2a-cf8ba39696ac",
               "create_time": "2015-07-23T06:47:33Z",
               "instance_name": "discuz_3D210808",
               "protect_from_scaling_down": false
           }
       ]
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
