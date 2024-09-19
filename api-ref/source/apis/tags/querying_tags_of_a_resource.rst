:original_name: as_06_1002.html

.. _as_06_1002:

Querying Tags of a Resource
===========================

Function
--------

This interface is used to query tags of a specified resource in a project.

URI
---

GET /autoscaling-api/v1/{project_id}/{resource_type}/{resource_id}/tags

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
   | resource_id     | Yes             | String          | Specifies the resource ID.                                            |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+

Request
-------

None

Example Request
---------------

This example queries the tags of the AS group with ID **e5d27f5c-dd76-4a61-b4bc-a67c5686719a**.

.. code-block:: text

   GET https://{Endpoint}/autoscaling-api/v1/{project_id}/scaling_group_tag/e5d27f5c-dd76-4a61-b4bc-a67c5686719a/tags

Response
--------

.. table:: **Table 2** Response parameters

   +-----------+-----------------------------------------------------------------------+-------------------------------------------------------------------------------------------+
   | Parameter | Type                                                                  | Description                                                                               |
   +===========+=======================================================================+===========================================================================================+
   | tags      | Array of :ref:`ResourceTag <as_06_1002__table64069331114716>` objects | Specifies tags. For details, see :ref:`Table 3 <as_06_1002__table64069331114716>`.        |
   +-----------+-----------------------------------------------------------------------+-------------------------------------------------------------------------------------------+
   | sys_tags  | Array of :ref:`ResourceTag <as_06_1002__table64069331114716>` objects | Specifies system tags. For details, see :ref:`Table 3 <as_06_1002__table64069331114716>`. |
   +-----------+-----------------------------------------------------------------------+-------------------------------------------------------------------------------------------+

.. _as_06_1002__table64069331114716:

.. table:: **Table 3** **ResourceTag** field description

   ========= ====== =========================
   Parameter Type   Description
   ========= ====== =========================
   key       String Specifies the tag key.
   value     String Specifies the tag values.
   ========= ====== =========================

Example Response
----------------

.. code-block::

    {
       "tags": [
           {
               "key": "ENV15",
               "value": "ENV15"
           },
           {
               "key": "ENV151",
               "value": "ENV151"
           },
           {
               "key": "ENV152",
               "value": "ENV152"
           }
       ],
       "sys_tags": null
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
