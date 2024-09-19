:original_name: as_06_0905.html

.. _as_06_0905:

Calling Back a Lifecycle Hook
=============================

Function
--------

This interface is used to call back the lifecycle hook specified by a scaling instance based on the lifecycle action key or based on the instance ID and lifecycle hook name.

-  If you have completed customized operations before the timeout duration expires, you can terminate or continue the lifecycle operations.
-  If you require more time to complete your custom operations, extend the timeout duration to enable the instance to remain in a wait state for an additional hour.
-  The callback operation can be performed only when the lifecycle hook of the target instance is in **HANGING** state.

URI
---

PUT /autoscaling-api/v1/{project_id}/scaling_instance_hook/{scaling_group_id}/callback

.. table:: **Table 1** Parameter description

   ================ ========= ====== ==========================
   Parameter        Mandatory Type   Description
   ================ ========= ====== ==========================
   project_id       Yes       String Specifies the project ID.
   scaling_group_id Yes       String Specifies the AS group ID.
   ================ ========= ====== ==========================

Request
-------

.. table:: **Table 2** Request parameters

   +-------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter               | Mandatory       | Type            | Description                                                                                                                                                                                                                           |
   +=========================+=================+=================+=======================================================================================================================================================================================================================================+
   | lifecycle_action_key    | No              | String          | Specifies the lifecycle operation token, which is obtained by calling the API for :ref:`querying instance suspension <as_06_0906>`.                                                                                                   |
   |                         |                 |                 |                                                                                                                                                                                                                                       |
   |                         |                 |                 | When specifying a lifecycle callback object, this field is mandatory if the **instance_id** parameter is not used. If both this parameter and the **instance_id** parameter are used, preferentially use this parameter for callback. |
   +-------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_id             | No              | String          | Specifies the instance ID.                                                                                                                                                                                                            |
   |                         |                 |                 |                                                                                                                                                                                                                                       |
   |                         |                 |                 | When a lifecycle callback object is specified, this parameter is mandatory if the **lifecycle_action_key** parameter is not used.                                                                                                     |
   +-------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | lifecycle_hook_name     | No              | String          | Specifies the lifecycle hook name.                                                                                                                                                                                                    |
   |                         |                 |                 |                                                                                                                                                                                                                                       |
   |                         |                 |                 | When a lifecycle callback object is specified, this parameter is mandatory if the **lifecycle_action_key** parameter is not used.                                                                                                     |
   +-------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | lifecycle_action_result | Yes             | String          | Specifies the lifecycle callback action.                                                                                                                                                                                              |
   |                         |                 |                 |                                                                                                                                                                                                                                       |
   |                         |                 |                 | -  **ABANDON**: terminates the instance.                                                                                                                                                                                              |
   |                         |                 |                 | -  **CONTINUE**: continues the instance.                                                                                                                                                                                              |
   |                         |                 |                 | -  **EXTEND**: extends the timeout duration, one hour each time.                                                                                                                                                                      |
   +-------------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

This example uses the lifecycle token **23880867-6288-4470-98a8-f8bda096b6c4** to perform the **ABANDON** callback operation in the AS group with ID **e5d27f5c-dd76-4a61-b4bc-a67c5686719a**.

.. code-block:: text

   PUT https://{Endpoint}/autoscaling-api/v1/{project_id}/scaling_instance_hook/e5d27f5c-dd76-4a61-b4bc-a67c5686719a/callback

   {
       "lifecycle_action_result": "ABANDON",
       "lifecycle_action_key":"23880867-6288-4470-98a8-f8bda096b6c4"
   }

Response
--------

None

Example Response
----------------

None

Returned Values
---------------

-  Normal

   204

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
