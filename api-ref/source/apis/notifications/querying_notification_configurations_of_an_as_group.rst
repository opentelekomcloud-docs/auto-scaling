:original_name: as_06_0802.html

.. _as_06_0802:

Querying Notification Configurations of an AS Group
===================================================

Function
--------

This API is used to query notification configurations of an AS group by group ID.

URI
---

GET /autoscaling-api/v1/{project_id}/scaling_notification/{scaling_group_id}

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

This example queries notification configurations of the AS group with ID **e5d27f5c-dd76-4a61-b4bc-a67c5686719a**.

.. code-block:: text

   GET https://{Endpoint}/autoscaling-api/v1/{project_id}/scaling_notification/e5d27f5c-dd76-4a61-b4bc-a67c5686719a

Response
--------

.. table:: **Table 2** Response parameters

   +-----------+-----------------------------------------------------------------+-------------------------------------------------+
   | Parameter | Type                                                            | Description                                     |
   +===========+=================================================================+=================================================+
   | topics    | Array of :ref:`topics <as_06_0802__table5664134195536>` objects | Specifies AS group notification configurations. |
   +-----------+-----------------------------------------------------------------+-------------------------------------------------+

.. _as_06_0802__table5664134195536:

.. table:: **Table 3** **topics** field description

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                              |
   +=======================+=======================+==========================================================================================+
   | topic_urn             | String                | Specifies a unique topic in SMN.                                                         |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------+
   | topic_scene           | Array of strings      | Specifies a notification scenario, which can be one of the following:                    |
   |                       |                       |                                                                                          |
   |                       |                       | -  **SCALING_UP**: indicates that the capacity has been expanded.                        |
   |                       |                       | -  **SCALING_UP_FAIL**: indicates that the capacity expansion failed.                    |
   |                       |                       | -  **SCALING_DOWN**: indicates that the capacity has been reduced.                       |
   |                       |                       | -  **SCALING_DOWN_FAIL**: indicates that the capacity reduction failed.                  |
   |                       |                       | -  **SCALING_GROUP_ABNORMAL**: indicates that an exception has occurred in the AS group. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------+
   | topic_name            | String                | Specifies the topic name in SMN.                                                         |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------+

Example Response
----------------

.. code-block::

   {
       "topics": [
           {
               "topic_name": "gsh",
               "topic_urn": "urn:smn:regionId:b53e5554fad0494d96206fb84296510b:gsh",
               "topic_scene": [
                   "SCALING_UP",
                   "SCALING_UP_FAIL",
                   "SCALING_DOWN",
                   "SCALING_DOWN_FAIL",
                   "SCALING_GROUP_ABNORMAL"
               ]
           },
           {
               "topic_name": "asdf",
               "topic_urn": "urn:smn:regionId:b53e5554fad0494d96206fb84296510b:asdf",
               "topic_scene": [
                   "SCALING_UP",
                   "SCALING_UP_FAIL"
               ]
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
