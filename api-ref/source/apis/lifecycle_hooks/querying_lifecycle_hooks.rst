:original_name: as_06_0902.html

.. _as_06_0902:

Querying Lifecycle Hooks
========================

Function
--------

This interface is used to query lifecycle hooks by AS group ID.

URI
---

GET /autoscaling-api/v1/{project_id}/scaling_lifecycle_hook/{scaling_group_id}/list

.. table:: **Table 1** Parameter description

   ================ ========= ====== ==========================
   Parameter        Mandatory Type   Description
   ================ ========= ====== ==========================
   project_id       Yes       String Specifies the project ID.
   scaling_group_id Yes       String Specifies the AS group ID.
   ================ ========= ====== ==========================

Request
-------

None

Example Request
---------------

This example queries the lifecycle hooks of the AS group with ID **e5d27f5c-dd76-4a61-b4bc-a67c5686719a**.

.. code-block:: text

   GET https://{Endpoint}/autoscaling-api/v1/{project_id}/scaling_lifecycle_hook/e5d27f5c-dd76-4a61-b4bc-a67c5686719a/list

Response
--------

.. table:: **Table 2** Response parameters

   +-----------------+--------------------------------------------------------------------------+----------------------------------------------------------------------------------------------+
   | Parameter       | Type                                                                     | Description                                                                                  |
   +=================+==========================================================================+==============================================================================================+
   | lifecycle_hooks | Array of :ref:`lifecycle_hooks <as_06_0902__table5077231195423>` objects | Specifies lifecycle hooks. For details, see :ref:`Table 3 <as_06_0902__table5077231195423>`. |
   +-----------------+--------------------------------------------------------------------------+----------------------------------------------------------------------------------------------+

.. _as_06_0902__table5077231195423:

.. table:: **Table 3** **lifecycle_hooks** field description

   +-------------------------+-----------------------+-----------------------------------------------------------------------------------+
   | Parameter               | Type                  | Description                                                                       |
   +=========================+=======================+===================================================================================+
   | lifecycle_hook_name     | String                | Specifies the lifecycle hook name.                                                |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------+
   | lifecycle_hook_type     | String                | Specifies the lifecycle hook type.                                                |
   |                         |                       |                                                                                   |
   |                         |                       | -  INSTANCE_TERMINATING                                                           |
   |                         |                       | -  INSTANCE_LAUNCHING                                                             |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------+
   | default_result          | String                | Specifies the default lifecycle hook callback operation.                          |
   |                         |                       |                                                                                   |
   |                         |                       | -  ABANDON                                                                        |
   |                         |                       | -  CONTINUE                                                                       |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------+
   | default_timeout         | Integer               | Specifies the lifecycle hook timeout duration in the unit of second.              |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------+
   | notification_topic_urn  | String                | Specifies a unique topic in SMN.                                                  |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------+
   | notification_topic_name | String                | Specifies the topic name in SMN.                                                  |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------+
   | notification_metadata   | String                | Specifies the customized notification.                                            |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------+
   | create_time             | String                | Specifies the time when the lifecycle hook is created. The time is UTC-compliant. |
   +-------------------------+-----------------------+-----------------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "lifecycle_hooks": [
           {
               "lifecycle_hook_name": "test-hook1",
               "default_result": "ABANDON",
               "default_timeout": 3600,
               "notification_topic_urn": "urn:smn:regionId:b53e5554fad0494d96206fb84296510b:gsh",
               "notification_topic_name": "gsh",
               "lifecycle_hook_type": "INSTANCE_LAUNCHING",
               "notification_metadata": null,
               "create_time": "2016-11-18T04:01:34Z"
           },
           {
               "lifecycle_hook_name": "test-hook2",
               "default_result": "CONTINUE",
               "default_timeout": 300,
               "notification_topic_urn": "urn:smn:regionId:a5b95554fad0494d94596fb84296510b:test",
               "notification_topic_name": "test",
               "lifecycle_hook_type": "INSTANCE_TERMINATING",
               "notification_metadata": null,
               "create_time": "2016-11-17T04:00:34Z"
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
