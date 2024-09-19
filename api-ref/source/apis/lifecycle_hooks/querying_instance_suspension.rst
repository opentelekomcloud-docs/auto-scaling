:original_name: as_06_0906.html

.. _as_06_0906:

Querying Instance Suspension
============================

Function
--------

After a lifecycle hook is added, when an AS group performs a scaling action, the lifecycle hook suspends the target instance and sets it to be in waiting state. You can query the instance suspension based on search criteria.

-  Search instance suspension by instance ID.
-  If no search criteria are specified, the suspension about all instances in the specified AS group is queried by default.

URI
---

GET /autoscaling-api/v1/{project_id}/scaling_instance_hook/{scaling_group_id}/list

.. note::

   You can type the question mark (?) and ampersand (&) at the end of the URI to define multiple search criteria. Instance suspension can be searched by all optional parameters in the following table. For details, see the example request.

.. table:: **Table 1** Parameter description

   ================ ========= ====== =============================
   Parameter        Mandatory Type   Description
   ================ ========= ====== =============================
   project_id       Yes       String Specifies the project ID.
   scaling_group_id Yes       String Specifies the AS group ID.
   instance_id      No        String Specifies the AS instance ID.
   ================ ========= ====== =============================

Request
-------

None

Example Request
---------------

This example queries the suspension of the instance with ID **b25c1589-c96c-465b-9fef-d06540d1945c** in the AS group with ID **e5d27f5c-dd76-4a61-b4bc-a67c5686719a**.

.. code-block:: text

   GET https://{Endpoint}/autoscaling-api/v1/{project_id}/scaling_instance_hook/e5d27f5c-dd76-4a61-b4bc-a67c5686719a/list?instance_id=b25c1589-c96c-465b-9fef-d06540d1945c

Response
--------

.. table:: **Table 2** Response parameters

   +-----------------------+--------------------------------------------------------------------------------+------------------------------------------------------------+
   | Parameter             | Type                                                                           | Description                                                |
   +=======================+================================================================================+============================================================+
   | instance_hanging_info | Array of :ref:`instance_hanging_info <as_06_0906__table3818677995816>` objects | Specifies lifecycle hook information about an AS instance. |
   +-----------------------+--------------------------------------------------------------------------------+------------------------------------------------------------+

.. _as_06_0906__table3818677995816:

.. table:: **Table 3** **instance_hanging_info** field description

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                        |
   +=======================+=======================+====================================================================================================+
   | lifecycle_hook_name   | String                | Specifies the lifecycle hook name.                                                                 |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------+
   | lifecycle_action_key  | String                | Specifies the lifecycle action key, which determines the lifecycle callback object.                |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------+
   | instance_id           | String                | Specifies the AS instance ID.                                                                      |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------+
   | scaling_group_id      | String                | Specifies the AS group ID.                                                                         |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------+
   | lifecycle_hook_status | String                | Specifies the lifecycle hook status.                                                               |
   |                       |                       |                                                                                                    |
   |                       |                       | -  **HANGING**: suspends the instance.                                                             |
   |                       |                       | -  **CONTINUE**: continues the instance.                                                           |
   |                       |                       | -  **ABANDON**: terminates the instance.                                                           |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------+
   | timeout               | String                | Specifies the timeout duration in the format of "YYYY-MM-DDThh:mm:ssZ". The time is UTC-compliant. |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------+
   | default_result        | String                | Specifies the default lifecycle hook callback operation.                                           |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "instance_hanging_info": [
           {
               "instance_id": "b25c1589-c96c-465b-9fef-d06540d1945c",
               "scaling_group_id": "e5d27f5c-dd76-4a61-b4bc-a67c5686719a",
               "lifecycle_hook_name": "hook-test",
               "lifecycle_action_key": "6ebe6e72-4b09-4adb-ae4a-a91dc0560069",
               "default_result": "ABANDON",
               "timeout": "2016-11-15T06:43:41Z",
               "lifecycle_hook_status": "HANGING"
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
