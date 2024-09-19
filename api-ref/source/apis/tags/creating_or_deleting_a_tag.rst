:original_name: as_06_1003.html

.. _as_06_1003:

Creating or Deleting a Tag
==========================

Function
--------

This API is used to create or delete a tag.

Each AS group can have a maximum of 10 tags added to it.

URI
---

POST /autoscaling-api/v1/{project_id}/{resource_type}/{resource_id}/tags/action

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
   | resource_id     | Yes             | String          | Resource ID                                                           |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------+

Request
-------

.. table:: **Table 2** Request parameters

   +-----------------+-----------------+-----------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                  | Description                                                                                                                   |
   +=================+=================+=======================================================================+===============================================================================================================================+
   | tags            | Yes             | Array of :ref:`ResourceTag <as_06_1003__table64069331114716>` objects | Specifies the tag list. For details, see :ref:`Table 3 <as_06_1003__table64069331114716>`.                                    |
   |                 |                 |                                                                       |                                                                                                                               |
   |                 |                 |                                                                       | If **action** is set to **delete**, the tag structure cannot be missing, and the key cannot be left blank or an empty string. |
   +-----------------+-----------------+-----------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | action          | Yes             | String                                                                | Specifies the operation ID. The value is case-sensitive and can be any of the following:                                      |
   |                 |                 |                                                                       |                                                                                                                               |
   |                 |                 |                                                                       | -  **delete**: indicates deleting a tag.                                                                                      |
   |                 |                 |                                                                       | -  **create**: indicates creating a tag. If the same key value already exists, it will be overwritten.                        |
   +-----------------+-----------------+-----------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+

.. _as_06_1003__table64069331114716:

.. table:: **Table 3** **ResourceTag** field description

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                         |
   +=================+=================+=================+=====================================================================================================================================================================+
   | key             | Yes             | String          | Specifies the tag key. Tag keys of a resource must be unique.                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                     |
   |                 |                 |                 | It contains a maximum of 36 Unicode characters. It cannot be left blank. It can contain only digits, letters, hyphens (-), underscores (_), and at signs (@).       |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value           | No              | String          | Specifies the tag value.                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                     |
   |                 |                 |                 | A tag value contains a maximum of 43 Unicode characters and can be left blank. It can contain only digits, letters, hyphens (-), underscores (_), and at signs (@). |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

This example adds two tags (key = **ENV15** and value = **ENV15**) and (key = **ENV151** and value = **ENV151**) to the AS group with ID **e5d27f5c-dd76-4a61-b4bc-a67c5686719a**.

.. code-block:: text

   POST https://{Endpoint}/autoscaling-api/v1/{project_id}/scaling_group_tag/e5d27f5c-dd76-4a61-b4bc-a67c5686719a/tags/action

   {
     "tags": [
       {
           "key": "ENV15",
           "value": "ENV15"
       },
       {
           "key": "ENV151",
           "value": "ENV151"
       }
       ],
     "action": "create"
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
