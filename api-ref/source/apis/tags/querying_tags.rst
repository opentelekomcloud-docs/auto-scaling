:original_name: as_06_1001.html

.. _as_06_1001:

Querying Tags
=============

Function
--------

This API is used to query tags of a specific type of resource in a project.

URI
---

GET /autoscaling-api/v1/{project_id}/{resource_type}/tags

.. table:: **Table 1** Parameter description

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                           |
   +=================+=================+=================+=======================================================================+
   | project_id      | Yes             | String          | Specifies the project ID.                                             |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+
   | resource_type   | Yes             | String          | Specifies the resource type. The option is as follows:                |
   |                 |                 |                 |                                                                       |
   |                 |                 |                 | **scaling_group_tag**: indicates that the resource type is AS groups. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+

Request
-------

None

Example Request
---------------

This example queries tags of AS groups in a project.

.. code-block:: text

   GET https://{Endpoint}/autoscaling-api/v1/{project_id}/scaling_group_tag/tags

Response
--------

.. table:: **Table 2** Response parameters

   +-----------+----------------------------------------------------------------+---------------------+
   | Parameter | Type                                                           | Description         |
   +===========+================================================================+=====================+
   | tags      | Array of :ref:`tags <as_06_1001__table40593624114129>` objects | Specifies the tags. |
   +-----------+----------------------------------------------------------------+---------------------+

.. _as_06_1001__table40593624114129:

.. table:: **Table 3** **tags** field description

   ========= ================ =========================
   Parameter Type             Description
   ========= ================ =========================
   key       String           Specifies the tag key.
   values    Array of strings Specifies the tag values.
   ========= ================ =========================

Example Response
----------------

.. code-block::

    {
       "tags": [
           {
               "key": "ENV15",
               "values": [
                   "ENV15"
               ]
           },
           {
               "key": "111",
               "values": [
                   ""
               ]
           },
           {
               "key": "environment",
               "values": [
                   "DEV"
               ]
           },
           {
               "key": "ENV151",
               "values": [
                   "ENV151"
               ]
           },
           {
               "key": "ENV152",
               "values": [
                   "ENV152"
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
   | 500 Internal Server Error         | Failed to complete the request because an internal service error occurred.                 |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 501 Not Implemented               | Failed to complete the request because the server does not support the requested function. |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 502 Bad Gateway                   | Failed to complete the request because the server has received an invalid response.        |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 503 Service Unavailable           | Failed to complete the request because the system is currently unavailable.                |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 504 Gateway Timeout               | A gateway timeout error occurred.                                                          |
   +-----------------------------------+--------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <as_07_0102>`.
