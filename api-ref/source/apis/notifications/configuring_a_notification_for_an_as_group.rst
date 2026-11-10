:original_name: as_06_0801.html

.. _as_06_0801:

Configuring a Notification for an AS Group
==========================================

Function
--------

This API is used to configure a notification for an AS group. When calling this API, you need to specify an SMN topic and a scaling event which will trigger a notification. After the configuration is complete, this API establishes an association between the AS group and the specified SMN topic to send notifications. When a specified scenario occurs, the AS group sends a notification to the endpoints subscribed to the topic.

Constraints
-----------

-  You need to create a topic in SMN and add subscriptions to it in advance. For details about how to create a topic and add subscriptions to it, see "Creating a Topic" and "Adding a Subscription to a Topic" in *Simple Message Notification (SMN) User Guide*.
-  Each time this API is called, the AS group adds a notification topic and scenario. A maximum of five topics can be added for each AS group.

URI
---

PUT /autoscaling-api/v1/{project_id}/scaling_notification/{scaling_group_id}

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

   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                          |
   +=================+=================+==================+======================================================================================+
   | topic_urn       | Yes             | String           | Specifies a unique topic in SMN.                                                     |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------+
   | topic_scene     | Yes             | Array of strings | Specifies a notification scenario, which can be one of the following:                |
   |                 |                 |                  |                                                                                      |
   |                 |                 |                  | -  **SCALING_UP**: indicates that the capacity has been expanded.                    |
   |                 |                 |                  | -  **SCALING_UP_FAIL**: indicates that the capacity expansion failed.                |
   |                 |                 |                  | -  **SCALING_DOWN**: indicates that the capacity has been reduced.                   |
   |                 |                 |                  | -  **SCALING_DOWN_FAIL**: indicates that the capacity reduction failed.              |
   |                 |                 |                  | -  **SCALING_GROUP_ABNORMAL**: indicates that an error has occurred in the AS group. |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------------------------+

Example Request
---------------

This example configures a notification with **topic_urn** set to **urn:smn:**\ *regionId*\ **:b53e5554fad0494d96206fb84296510b:gsh** for the AS group with ID **e5d27f5c-dd76-4a61-b4bc-a67c5686719a**. After the configuration is complete, a notification will be sent when capacity expansion succeeds or fails, capacity reduction succeeds or fails, or an error occurs in the AS group.

.. code-block:: text

   PUT https://{Endpoint}/autoscaling-api/v1/{project_id}/scaling_notification/e5d27f5c-dd76-4a61-b4bc-a67c5686719a

   {
       "topic_urn": "urn:smn:regionId:b53e5554fad0494d96206fb84296510b:gsh",
       "topic_scene": [
           "SCALING_UP","SCALING_UP_FAIL","SCALING_DOWN","SCALING_DOWN_FAIL","SCALING_GROUP_ABNORMAL"
        ]
   }

Response
--------

.. table:: **Table 3** Response parameters

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                          |
   +=======================+=======================+======================================================================================+
   | topic_urn             | String                | Specifies a unique topic in SMN.                                                     |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------+
   | topic_scene           | Array of strings      | Specifies a notification scenario, which can be one of the following:                |
   |                       |                       |                                                                                      |
   |                       |                       | -  **SCALING_UP**: indicates that the capacity has been expanded.                    |
   |                       |                       | -  **SCALING_UP_FAIL**: indicates that the capacity expansion failed.                |
   |                       |                       | -  **SCALING_DOWN**: indicates that the capacity has been reduced.                   |
   |                       |                       | -  **SCALING_DOWN_FAIL**: indicates that the capacity reduction failed.              |
   |                       |                       | -  **SCALING_GROUP_ABNORMAL**: indicates that an error has occurred in the AS group. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------+
   | topic_name            | String                | Specifies the topic name in SMN.                                                     |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "topic_urn": "urn:smn:regionId:b53e5554fad0494d96206fb84296510b:gsh",
       "topic_scene": [
           "SCALING_UP","SCALING_UP_FAIL","SCALING_DOWN","SCALING_DOWN_FAIL","SCALING_GROUP_ABNORMAL"
        ],
       "topic_name": "gsh"
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
