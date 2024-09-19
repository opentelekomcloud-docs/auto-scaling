:original_name: as_06_0901.html

.. _as_06_0901:

Creating a Lifecycle Hook
=========================

Function
--------

This interface is used to create a lifecycle hook for an AS group. Up to five lifecycle hooks can be created for one AS group.

-  After the creation, when the AS group is resized, the lifecycle hook suspends the involved instance and puts it to a **Wait (Adding to AS group)** or **Wait (Removing from AS group)** status. This status is retained until the timeout duration ends or you manually perform a callback.
-  During the instance waiting duration, you can perform customized operations. For example, you can install or configure software on a newly started instance, or download the log file from the instance before the instance terminates.

URI
---

POST /autoscaling-api/v1/{project_id}/scaling_lifecycle_hook/{scaling_group_id}

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

   +------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter              | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                                        |
   +========================+=================+=================+====================================================================================================================================================================================================================================================================================================================================+
   | lifecycle_hook_name    | Yes             | String          | Specifies the lifecycle hook name. The name contains only letters, digits, underscores (_), and hyphens (-), and cannot exceed 32 characters.                                                                                                                                                                                      |
   +------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | lifecycle_hook_type    | Yes             | String          | Specifies the lifecycle hook type. Options:                                                                                                                                                                                                                                                                                        |
   |                        |                 |                 |                                                                                                                                                                                                                                                                                                                                    |
   |                        |                 |                 | -  **INSTANCE_TERMINATING**: The hook suspends the instance when the instance is terminated.                                                                                                                                                                                                                                       |
   |                        |                 |                 | -  **INSTANCE_LAUNCHING**: The hook suspends the instance when the instance is started.                                                                                                                                                                                                                                            |
   +------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | default_result         | No              | String          | Specifies the default lifecycle hook callback operation. By default, this operation is performed when the timeout duration expires.                                                                                                                                                                                                |
   |                        |                 |                 |                                                                                                                                                                                                                                                                                                                                    |
   |                        |                 |                 | -  ABANDON                                                                                                                                                                                                                                                                                                                         |
   |                        |                 |                 | -  CONTINUE                                                                                                                                                                                                                                                                                                                        |
   |                        |                 |                 |                                                                                                                                                                                                                                                                                                                                    |
   |                        |                 |                 | .. note::                                                                                                                                                                                                                                                                                                                          |
   |                        |                 |                 |                                                                                                                                                                                                                                                                                                                                    |
   |                        |                 |                 |    -  If an instance is starting, **CONTINUE** indicates that your customized operations are successful and the instance can be used. **ABANDON** indicates that your customized operations failed, and the instance will be terminated. In such a case, the scaling action fails, and you must create a new instance.             |
   |                        |                 |                 |    -  If an instance is stopping, both **ABANDON** and **CONTINUE** allow instance termination. The difference between the two states is as follows: **ABANDON** stops other lifecycle hooks, but **CONTINUE** allows the completion of other lifecycle hooks.                                                                     |
   |                        |                 |                 |    -  The default value of this parameter is **ABANDON**.                                                                                                                                                                                                                                                                          |
   +------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | default_timeout        | No              | Integer         | Specifies the lifecycle hook timeout duration, which ranges from 60 to 86400 in the unit of second. The default value is 3600.                                                                                                                                                                                                     |
   |                        |                 |                 |                                                                                                                                                                                                                                                                                                                                    |
   |                        |                 |                 | By default, this parameter specifies the instance waiting duration. You can prolong the timeout duration or perform the **CONTINUE** or **ABANDON** operation before the timeout duration expires.                                                                                                                                 |
   +------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | notification_topic_urn | Yes             | String          | Specifies a unique topic in SMN.                                                                                                                                                                                                                                                                                                   |
   |                        |                 |                 |                                                                                                                                                                                                                                                                                                                                    |
   |                        |                 |                 | This parameter specifies a notification object for a lifecycle hook. When an instance is suspended by the lifecycle hook, the SMN service sends a notification to the object. This notification contains the basic instance information, your customized notification content, and the token for controlling lifecycle operations. |
   +------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | notification_metadata  | No              | String          | Specifies a customized notification, which contains no more than 256 characters in length. The message cannot contain the following characters: <>&'()                                                                                                                                                                             |
   |                        |                 |                 |                                                                                                                                                                                                                                                                                                                                    |
   |                        |                 |                 | After a notification object is configured, the SMN service sends your customized notification to the object.                                                                                                                                                                                                                       |
   +------------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

This example creates the lifecycle hook named **test-hook1** in the AS group with ID **e5d27f5c-dd76-4a61-b4bc-a67c5686719a**. The configuration is as follows: The callback operation is **ABANDON**, the timeout duration is **3600 seconds**; the notification topic_urn is **urn:smn:**\ *regionId*\ **:b53e5554fad0494d96206fb84296510b:gsh**, the hook suspends the instance when the instance is started.

.. code-block:: text

   POST https://{Endpoint}/autoscaling-api/v1/{project_id}/scaling_lifecycle_hook/e5d27f5c-dd76-4a61-b4bc-a67c5686719a

   {
       "lifecycle_hook_name": "test-hook1",
       "default_result": "ABANDON",
       "default_timeout": 3600,
       "notification_topic_urn": "urn:smn:regionId:b53e5554fad0494d96206fb84296510b:gsh",
       "lifecycle_hook_type": "INSTANCE_LAUNCHING"
   }

Response
--------

.. table:: **Table 3** Response parameters

   +-------------------------+-----------------------+----------------------------------------------------------------------+
   | Parameter               | Type                  | Description                                                          |
   +=========================+=======================+======================================================================+
   | lifecycle_hook_name     | String                | Specifies the lifecycle hook name.                                   |
   +-------------------------+-----------------------+----------------------------------------------------------------------+
   | lifecycle_hook_type     | String                | Specifies the lifecycle hook type.                                   |
   |                         |                       |                                                                      |
   |                         |                       | -  INSTANCE_TERMINATING                                              |
   |                         |                       | -  INSTANCE_LAUNCHING                                                |
   +-------------------------+-----------------------+----------------------------------------------------------------------+
   | default_result          | String                | Specifies the default lifecycle hook callback operation.             |
   |                         |                       |                                                                      |
   |                         |                       | -  ABANDON                                                           |
   |                         |                       | -  CONTINUE                                                          |
   +-------------------------+-----------------------+----------------------------------------------------------------------+
   | default_timeout         | Integer               | Specifies the lifecycle hook timeout duration in the unit of second. |
   +-------------------------+-----------------------+----------------------------------------------------------------------+
   | notification_topic_urn  | String                | Specifies a unique topic in SMN.                                     |
   +-------------------------+-----------------------+----------------------------------------------------------------------+
   | notification_topic_name | String                | Specifies the topic name in SMN.                                     |
   +-------------------------+-----------------------+----------------------------------------------------------------------+
   | notification_metadata   | String                | Specifies the notification message.                                  |
   +-------------------------+-----------------------+----------------------------------------------------------------------+
   | create_time             | String                | Specifies the UTC-compliant time when the lifecycle hook is created. |
   +-------------------------+-----------------------+----------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "lifecycle_hook_name": "test-hook1",
       "default_result": "ABANDON",
       "default_timeout": 3600,
       "notification_topic_urn": "urn:smn:regionId:b53e5554fad0494d96206fb84296510b:gsh",
       "notification_topic_name": "gsh",
       "lifecycle_hook_type": "INSTANCE_LAUNCHING",
       "notification_metadata": null,
       "create_time": "2019-03-18T16:00:11Z"
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
