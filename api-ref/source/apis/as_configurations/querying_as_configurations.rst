:original_name: as_06_0202.html

.. _as_06_0202:

Querying AS Configurations
==========================

Function
--------

This API is used to query AS configurations based on search criteria. The results are displayed by page.

-  Search criteria can be the AS configuration name, image ID, start line number, and number of records.
-  If no search criteria are specified, a maximum of 20 AS configurations can be queried for a tenant by default.

URI
---

GET /autoscaling-api/v1/{project_id}/scaling_configuration

.. note::

   You can type the question mark (?) and ampersand (&) at the end of the URI to define multiple search criteria. AS configurations can be searched by all optional parameters in the following table. For details, see the example request.

.. table:: **Table 1** Parameter description

   +----------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                  | Mandatory       | Type            | Description                                                                                                                                                                                         |
   +============================+=================+=================+=====================================================================================================================================================================================================+
   | project_id                 | Yes             | String          | **Definition**                                                                                                                                                                                      |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | Specifies the project ID. For details, see :ref:`Obtaining a Project ID <as_04_0106>`.                                                                                                              |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | **Constraints**                                                                                                                                                                                     |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | N/A                                                                                                                                                                                                 |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | **Range**                                                                                                                                                                                           |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | N/A                                                                                                                                                                                                 |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | **Default Value**                                                                                                                                                                                   |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | N/A                                                                                                                                                                                                 |
   +----------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | scaling_configuration_name | No              | String          | **Definition**                                                                                                                                                                                      |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | Specifies the AS configuration name.                                                                                                                                                                |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | **Constraints**                                                                                                                                                                                     |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | N/A                                                                                                                                                                                                 |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | **Range**                                                                                                                                                                                           |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | The value can contain 1 to 64 characters. Only letters, digits, underscores (_), and hyphens (-) are allowed.                                                                                       |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | **Default Value**                                                                                                                                                                                   |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | N/A                                                                                                                                                                                                 |
   +----------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | image_id                   | No              | String          | **Definition**                                                                                                                                                                                      |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | Specifies the image ID. Its value is the same as that of **imageRef** for specifying the image selected during ECS creation. You can obtain an image ID by calling the IMS API for querying images. |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | **Constraints**                                                                                                                                                                                     |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | N/A                                                                                                                                                                                                 |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | **Range**                                                                                                                                                                                           |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | N/A                                                                                                                                                                                                 |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | **Default Value**                                                                                                                                                                                   |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | N/A                                                                                                                                                                                                 |
   +----------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | start_number               | No              | Integer         | **Definition**                                                                                                                                                                                      |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | Specifies the start line number.                                                                                                                                                                    |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | **Constraints**                                                                                                                                                                                     |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | N/A                                                                                                                                                                                                 |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | **Range**                                                                                                                                                                                           |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | Minimum value: **0**                                                                                                                                                                                |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | **Default Value**                                                                                                                                                                                   |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | 0                                                                                                                                                                                                   |
   +----------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit                      | No              | Integer         | **Definition**                                                                                                                                                                                      |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | Specifies the number of records to be returned.                                                                                                                                                     |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | **Constraints**                                                                                                                                                                                     |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | N/A                                                                                                                                                                                                 |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | **Range**                                                                                                                                                                                           |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | 0-100                                                                                                                                                                                               |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | **Default Value**                                                                                                                                                                                   |
   |                            |                 |                 |                                                                                                                                                                                                     |
   |                            |                 |                 | 20                                                                                                                                                                                                  |
   +----------------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

None

Example Request
---------------

This example queries the AS configurations with image ID **37ca2b35-6fc7-47ab-93c7-900324809c5c**.

.. code-block:: text

   GET https://{Endpoint}/autoscaling-api/v1/{project_id}/scaling_configuration?image_id=37ca2b35-6fc7-47ab-93c7-900324809c5c

Response
--------

.. table:: **Table 2** Response

   +------------------------+---------------------------------------------------------------------------------+----------------------------------------+
   | Parameter              | Type                                                                            | Description                            |
   +========================+=================================================================================+========================================+
   | total_number           | Integer                                                                         | **Definition**                         |
   |                        |                                                                                 |                                        |
   |                        |                                                                                 | Specifies the total number of records. |
   |                        |                                                                                 |                                        |
   |                        |                                                                                 | **Range**                              |
   |                        |                                                                                 |                                        |
   |                        |                                                                                 | N/A                                    |
   +------------------------+---------------------------------------------------------------------------------+----------------------------------------+
   | start_number           | Integer                                                                         | **Definition**                         |
   |                        |                                                                                 |                                        |
   |                        |                                                                                 | Specifies the start line number.       |
   |                        |                                                                                 |                                        |
   |                        |                                                                                 | **Range**                              |
   |                        |                                                                                 |                                        |
   |                        |                                                                                 | Minimum value: **0**                   |
   +------------------------+---------------------------------------------------------------------------------+----------------------------------------+
   | limit                  | Integer                                                                         | **Definition**                         |
   |                        |                                                                                 |                                        |
   |                        |                                                                                 | Specifies the number of query records. |
   |                        |                                                                                 |                                        |
   |                        |                                                                                 | **Range**                              |
   |                        |                                                                                 |                                        |
   |                        |                                                                                 | 0-100                                  |
   +------------------------+---------------------------------------------------------------------------------+----------------------------------------+
   | scaling_configurations | Array of :ref:`scaling_configurations <as_06_0202__table5681858093547>` objects | **Definition**                         |
   |                        |                                                                                 |                                        |
   |                        |                                                                                 | Specifies the AS configuration list.   |
   +------------------------+---------------------------------------------------------------------------------+----------------------------------------+

.. _as_06_0202__table5681858093547:

.. table:: **Table 3** **scaling_configurations** field description

   +----------------------------+---------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                  | Type                                                          | Description                                                                                                                                                             |
   +============================+===============================================================+=========================================================================================================================================================================+
   | scaling_configuration_id   | String                                                        | **Definition**                                                                                                                                                          |
   |                            |                                                               |                                                                                                                                                                         |
   |                            |                                                               | Specifies the AS configuration ID. This parameter is globally unique.                                                                                                   |
   |                            |                                                               |                                                                                                                                                                         |
   |                            |                                                               | **Range**                                                                                                                                                               |
   |                            |                                                               |                                                                                                                                                                         |
   |                            |                                                               | N/A                                                                                                                                                                     |
   +----------------------------+---------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tenant                     | String                                                        | **Definition**                                                                                                                                                          |
   |                            |                                                               |                                                                                                                                                                         |
   |                            |                                                               | Specifies the tenant ID.                                                                                                                                                |
   |                            |                                                               |                                                                                                                                                                         |
   |                            |                                                               | **Range**                                                                                                                                                               |
   |                            |                                                               |                                                                                                                                                                         |
   |                            |                                                               | N/A                                                                                                                                                                     |
   +----------------------------+---------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | scaling_configuration_name | String                                                        | **Definition**                                                                                                                                                          |
   |                            |                                                               |                                                                                                                                                                         |
   |                            |                                                               | Specifies the AS configuration name. Fuzzy match is supported.                                                                                                          |
   |                            |                                                               |                                                                                                                                                                         |
   |                            |                                                               | **Range**                                                                                                                                                               |
   |                            |                                                               |                                                                                                                                                                         |
   |                            |                                                               | The value can contain 1 to 64 characters. Only letters, digits, underscores (_), and hyphens (-) are allowed.                                                           |
   +----------------------------+---------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_config            | :ref:`instance_config <as_06_0202__table420823093759>` object | **Definition**                                                                                                                                                          |
   |                            |                                                               |                                                                                                                                                                         |
   |                            |                                                               | Specifies the information about instance configurations.                                                                                                                |
   +----------------------------+---------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time                | String                                                        | **Definition**                                                                                                                                                          |
   |                            |                                                               |                                                                                                                                                                         |
   |                            |                                                               | Specifies the time when AS configurations were created. The time format complies with UTC. The format is *yyyy-MM-ddTHH:mm:ssZ*, for example, **2025-05-10T10:00:00Z**. |
   |                            |                                                               |                                                                                                                                                                         |
   |                            |                                                               | **Range**                                                                                                                                                               |
   |                            |                                                               |                                                                                                                                                                         |
   |                            |                                                               | N/A                                                                                                                                                                     |
   +----------------------------+---------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | scaling_group_id           | String                                                        | **Definition**                                                                                                                                                          |
   |                            |                                                               |                                                                                                                                                                         |
   |                            |                                                               | Specifies the ID of the AS group to which the AS configuration is bound.                                                                                                |
   |                            |                                                               |                                                                                                                                                                         |
   |                            |                                                               | **Range**                                                                                                                                                               |
   |                            |                                                               |                                                                                                                                                                         |
   |                            |                                                               | N/A                                                                                                                                                                     |
   +----------------------------+---------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _as_06_0202__table420823093759:

.. table:: **Table 4** **instance_config** field description

   +------------------------------+-------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                    | Type                                                                    | Description                                                                                                                                                             |
   +==============================+=========================================================================+=========================================================================================================================================================================+
   | flavorRef                    | String                                                                  | **Definition**                                                                                                                                                          |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | Specifies the ECS flavor ID.                                                                                                                                            |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | **Range**                                                                                                                                                               |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | N/A                                                                                                                                                                     |
   +------------------------------+-------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | imageRef                     | String                                                                  | **Definition**                                                                                                                                                          |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | Specifies the image ID. It is the same as **image_id**.                                                                                                                 |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | **Range**                                                                                                                                                               |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | N/A                                                                                                                                                                     |
   +------------------------------+-------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | disk                         | Array of :ref:`disk <as_06_0202__table2679008093849>` objects           | **Definition**                                                                                                                                                          |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | Specifies the disk group information.                                                                                                                                   |
   +------------------------------+-------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | key_name                     | String                                                                  | **Definition**                                                                                                                                                          |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | Specifies the name of the SSH key pair used to log in to the ECS.                                                                                                       |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | **Range**                                                                                                                                                               |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | N/A                                                                                                                                                                     |
   +------------------------------+-------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | key_fingerprint              | String                                                                  | **Definition**                                                                                                                                                          |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | Specifies the fingerprint of the SSH key pair used to log in to the ECS.                                                                                                |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | **Range**                                                                                                                                                               |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | N/A                                                                                                                                                                     |
   +------------------------------+-------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_name                | String                                                                  | **Definition**                                                                                                                                                          |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | Specifies the instance name. This parameter is reserved.                                                                                                                |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | .. note::                                                                                                                                                               |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         |    When you call APIs to query details about an AS configuration created from an ECS or to list such AS configurations, **instance_name** is omitted from the response. |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | **Range**                                                                                                                                                               |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | N/A                                                                                                                                                                     |
   +------------------------------+-------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | instance_id                  | String                                                                  | **Definition**                                                                                                                                                          |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | Specifies the instance ID. This parameter is reserved.                                                                                                                  |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | **Range**                                                                                                                                                               |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | N/A                                                                                                                                                                     |
   +------------------------------+-------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | adminPass                    | String                                                                  | **Definition**                                                                                                                                                          |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | Specifies the password used to log in to the ECS. The displayed password is not plaintext. This parameter is reserved.                                                  |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | **Range**                                                                                                                                                               |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | N/A                                                                                                                                                                     |
   +------------------------------+-------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | personality                  | Array of :ref:`personality <as_06_0202__table1186638793926>` objects    | **Definition**                                                                                                                                                          |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | Specifies information about the injected file.                                                                                                                          |
   +------------------------------+-------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | public_ip                    | :ref:`public_ip <as_06_0202__tcdec56e5b04447d7b37ba3897d12796c>` object | **Definition**                                                                                                                                                          |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | Specifies the EIP of the ECS.                                                                                                                                           |
   +------------------------------+-------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_data                    | String                                                                  | **Definition**                                                                                                                                                          |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | Specifies the Cloud-Init user data, which is encoded using Base64.                                                                                                      |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | **Range**                                                                                                                                                               |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | N/A                                                                                                                                                                     |
   +------------------------------+-------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata                     | :ref:`metadata <as_06_0202__table6119722495435>` object                 | **Definition**                                                                                                                                                          |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | Specifies the ECS metadata. For details, see :ref:`Table 11 <as_06_0202__table6119722495435>`.                                                                          |
   +------------------------------+-------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | security_groups              | Array of :ref:`security_groups <as_06_0202__table121274211250>` objects | **Definition**                                                                                                                                                          |
   |                              |                                                                         |                                                                                                                                                                         |
   |                              |                                                                         | Specifies security group information.                                                                                                                                   |
   +------------------------------+-------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | server_group_id              | String                                                                  | This parameter is reserved.                                                                                                                                             |
   +------------------------------+-------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tenancy                      | String                                                                  | This parameter is reserved.                                                                                                                                             |
   +------------------------------+-------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dedicated_host_id            | String                                                                  | This parameter is reserved.                                                                                                                                             |
   +------------------------------+-------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | market_type                  | String                                                                  | This parameter is reserved.                                                                                                                                             |
   +------------------------------+-------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | multi_flavor_priority_policy | String                                                                  | This parameter is reserved.                                                                                                                                             |
   +------------------------------+-------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _as_06_0202__table2679008093849:

.. table:: **Table 5** **disk** field description

   +-----------------------+----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                     | Description                                                                                                   |
   +=======================+==========================================================+===============================================================================================================+
   | size                  | Integer                                                  | **Definition**                                                                                                |
   |                       |                                                          |                                                                                                               |
   |                       |                                                          | Specifies the disk size. The unit is GB.                                                                      |
   |                       |                                                          |                                                                                                               |
   |                       |                                                          | **Range**                                                                                                     |
   |                       |                                                          |                                                                                                               |
   |                       |                                                          | -  System disk: 1 GB to 1024 GB                                                                               |
   |                       |                                                          | -  Data disk: 10 GB to 32,768 GB                                                                              |
   +-----------------------+----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | volume_type           | String                                                   | **Definition**                                                                                                |
   |                       |                                                          |                                                                                                               |
   |                       |                                                          | Specifies the disk type.                                                                                      |
   |                       |                                                          |                                                                                                               |
   |                       |                                                          | **Range**                                                                                                     |
   |                       |                                                          |                                                                                                               |
   |                       |                                                          | -  **SATA**: common I/O                                                                                       |
   |                       |                                                          | -  **SAS**: high I/O                                                                                          |
   |                       |                                                          | -  **GPSSD**: general-purpose SSD                                                                             |
   |                       |                                                          | -  **SSD**: ultra-I/O                                                                                         |
   |                       |                                                          | -  **ESSD**: extreme SSD                                                                                      |
   |                       |                                                          | -  **GPSSD2**: general-purpose SSD V2                                                                         |
   |                       |                                                          | -  **ESSD2**: extreme SSD V2                                                                                  |
   +-----------------------+----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | disk_type             | String                                                   | **Definition**                                                                                                |
   |                       |                                                          |                                                                                                               |
   |                       |                                                          | Specifies the disk type (system disk or data disk).                                                           |
   |                       |                                                          |                                                                                                               |
   |                       |                                                          | **Range**                                                                                                     |
   |                       |                                                          |                                                                                                               |
   |                       |                                                          | -  **DATA**: data disk                                                                                        |
   |                       |                                                          | -  **SYS**: system disk                                                                                       |
   +-----------------------+----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | data_disk_image_id    | String                                                   | **Definition**                                                                                                |
   |                       |                                                          |                                                                                                               |
   |                       |                                                          | Specifies the ID of the data disk image for creating a data disk.                                             |
   |                       |                                                          |                                                                                                               |
   |                       |                                                          | **Range**                                                                                                     |
   |                       |                                                          |                                                                                                               |
   |                       |                                                          | N/A                                                                                                           |
   +-----------------------+----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | snapshot_id           | String                                                   | **Definition**                                                                                                |
   |                       |                                                          |                                                                                                               |
   |                       |                                                          | Specifies the disk backup snapshot ID.                                                                        |
   |                       |                                                          |                                                                                                               |
   |                       |                                                          | **Range**                                                                                                     |
   |                       |                                                          |                                                                                                               |
   |                       |                                                          | N/A                                                                                                           |
   +-----------------------+----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+
   | metadata              | :ref:`metadata <as_06_0202__table17912164981110>` object | **Definition**                                                                                                |
   |                       |                                                          |                                                                                                               |
   |                       |                                                          | Specifies the metadata for creating disks. For details, see :ref:`Table 6 <as_06_0202__table17912164981110>`. |
   +-----------------------+----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------+

.. _as_06_0202__table17912164981110:

.. table:: **Table 6** **metadata** Field Description for Creating Disks

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                   |
   +=======================+=======================+===============================================================================================================================================+
   | \__system__encrypted  | String                | **Definition**                                                                                                                                |
   |                       |                       |                                                                                                                                               |
   |                       |                       | Specifies whether disks are encrypted.                                                                                                        |
   |                       |                       |                                                                                                                                               |
   |                       |                       | If this parameter is absent, disks are not encrypted by default.                                                                              |
   |                       |                       |                                                                                                                                               |
   |                       |                       | **Range**                                                                                                                                     |
   |                       |                       |                                                                                                                                               |
   |                       |                       | **0**: not encrypted                                                                                                                          |
   |                       |                       |                                                                                                                                               |
   |                       |                       | **1**: encrypted                                                                                                                              |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
   | \__system__cmkid      | String                | **Definition**                                                                                                                                |
   |                       |                       |                                                                                                                                               |
   |                       |                       | Specifies the CMK ID which is used for encryption. This parameter is used with **\__system__encrypted**.                                      |
   |                       |                       |                                                                                                                                               |
   |                       |                       | .. note::                                                                                                                                     |
   |                       |                       |                                                                                                                                               |
   |                       |                       |    For details about how to use an HTTPS request to obtain the CMK ID, see "Querying the Key List" in *Key Management Service API Reference*. |
   |                       |                       |                                                                                                                                               |
   |                       |                       | **Range**                                                                                                                                     |
   |                       |                       |                                                                                                                                               |
   |                       |                       | N/A                                                                                                                                           |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------+

.. _as_06_0202__table1186638793926:

.. table:: **Table 7** **personality** field description

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                               |
   +=======================+=======================+===========================================================================================================================================================================================================+
   | path                  | String                | **Definition**                                                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                           |
   |                       |                       | Specifies the path of the injected file.                                                                                                                                                                  |
   |                       |                       |                                                                                                                                                                                                           |
   |                       |                       | **Range**                                                                                                                                                                                                 |
   |                       |                       |                                                                                                                                                                                                           |
   |                       |                       | -  For Linux, specify the path, for example, **/etc/foo.txt**, of the injected file.                                                                                                                      |
   |                       |                       | -  For Windows, the injected file is automatically stored in the root directory of drive C. You only need to specify the file name, for example, **foo**. The file name contains only letters and digits. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | content               | String                | **Definition**                                                                                                                                                                                            |
   |                       |                       |                                                                                                                                                                                                           |
   |                       |                       | Specifies the content of the file to be injected. The file content is encoded using Base64.                                                                                                               |
   |                       |                       |                                                                                                                                                                                                           |
   |                       |                       | **Range**                                                                                                                                                                                                 |
   |                       |                       |                                                                                                                                                                                                           |
   |                       |                       | N/A                                                                                                                                                                                                       |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _as_06_0202__tcdec56e5b04447d7b37ba3897d12796c:

.. table:: **Table 8** **public_ip** field description

   +-----------------------+-------------------------------------------------------------------+-------------------------------------------+
   | Parameter             | Type                                                              | Description                               |
   +=======================+===================================================================+===========================================+
   | eip                   | :ref:`eip <as_06_0202__tdd0bc92fd16345d48c819c97641a369f>` object | **Definition**                            |
   |                       |                                                                   |                                           |
   |                       |                                                                   | Specifies the automatically assigned EIP. |
   +-----------------------+-------------------------------------------------------------------+-------------------------------------------+

.. _as_06_0202__tdd0bc92fd16345d48c819c97641a369f:

.. table:: **Table 9** **eip** field description

   +-----------------------+-------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                    | Description                                                                                             |
   +=======================+=========================================================================+=========================================================================================================+
   | ip_type               | String                                                                  | **Definition**                                                                                          |
   |                       |                                                                         |                                                                                                         |
   |                       |                                                                         | Specifies the IP address type.                                                                          |
   |                       |                                                                         |                                                                                                         |
   |                       |                                                                         | For details, see the **publicip** field in "Assigning an EIP" in *Virtual Private Cloud API Reference*. |
   |                       |                                                                         |                                                                                                         |
   |                       |                                                                         | **Range**                                                                                               |
   |                       |                                                                         |                                                                                                         |
   |                       |                                                                         | -  **5_bgp**: dynamic BGP                                                                               |
   |                       |                                                                         | -  **5_sbgp**: static BGP                                                                               |
   +-----------------------+-------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+
   | bandwidth             | :ref:`bandwidth <as_06_0202__t5334015bf90941a996bc1c9ca7ef4637>` object | **Definition**                                                                                          |
   |                       |                                                                         |                                                                                                         |
   |                       |                                                                         | Specifies the bandwidth of an IP address.                                                               |
   +-----------------------+-------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------+

.. _as_06_0202__t5334015bf90941a996bc1c9ca7ef4637:

.. table:: **Table 10** **bandwidth** field description

   +-----------------------+-----------------------+---------------------------------------+
   | Parameter             | Type                  | Description                           |
   +=======================+=======================+=======================================+
   | size                  | Integer               | **Definition**                        |
   |                       |                       |                                       |
   |                       |                       | Specifies the bandwidth (Mbit/s).     |
   |                       |                       |                                       |
   |                       |                       | **Range**                             |
   |                       |                       |                                       |
   |                       |                       | [1,500]                               |
   +-----------------------+-----------------------+---------------------------------------+
   | share_type            | String                | **Definition**                        |
   |                       |                       |                                       |
   |                       |                       | Specifies the bandwidth sharing type. |
   |                       |                       |                                       |
   |                       |                       | **Range**                             |
   |                       |                       |                                       |
   |                       |                       | -  **PER**: dedicated                 |
   +-----------------------+-----------------------+---------------------------------------+
   | charging_mode         | String                | **Definition**                        |
   |                       |                       |                                       |
   |                       |                       | Specifies the bandwidth billing mode. |
   |                       |                       |                                       |
   |                       |                       | **Range**                             |
   |                       |                       |                                       |
   |                       |                       | -  **traffic**: billed by traffic.    |
   +-----------------------+-----------------------+---------------------------------------+

.. _as_06_0202__table6119722495435:

.. table:: **Table 11** **metadata** field description

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                |
   +=======================+=======================+============================================================================================================================================================+
   | admin_pass            | String                | **Definition**                                                                                                                                             |
   |                       |                       |                                                                                                                                                            |
   |                       |                       | Specifies the password of the **Administrator** account for a Windows ECS.                                                                                 |
   |                       |                       |                                                                                                                                                            |
   |                       |                       | **Range**                                                                                                                                                  |
   |                       |                       |                                                                                                                                                            |
   |                       |                       | The password must:                                                                                                                                         |
   |                       |                       |                                                                                                                                                            |
   |                       |                       | -  Contain 8 to 26 characters.                                                                                                                             |
   |                       |                       | -  Contain at least three of the following character types: uppercase letters, lowercase letters, digits, and special characters (``!@$%^-_=+[{}]:,./?``). |
   |                       |                       | -  Not contain the username or the username in reversed order.                                                                                             |
   |                       |                       | -  Not contain the username, the username in reversed order, or more than two consecutive characters in the username. (for Windows)                        |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _as_06_0202__table121274211250:

.. table:: **Table 12** **security_groups** field description

   +-----------------------+-----------------------+----------------------------------+
   | Parameter             | Type                  | Description                      |
   +=======================+=======================+==================================+
   | id                    | String                | **Definition**                   |
   |                       |                       |                                  |
   |                       |                       | Specifies the security group ID. |
   |                       |                       |                                  |
   |                       |                       | **Range**                        |
   |                       |                       |                                  |
   |                       |                       | N/A                              |
   +-----------------------+-----------------------+----------------------------------+

Example Response
----------------

.. code-block::

   {
       "limit": 20,
       "total_number": 2,
       "start_number": 0,
       "scaling_configurations": [
           {
               "tenant": "ce061903a53545dcaddb300093b477d2",
               "scaling_configuration_id": "6afe46f9-7d3d-4046-8748-3b2a1085ad86",
               "scaling_configuration_name": "config_name_1",
               "instance_config": {
                   "disk": [
                       {
                           "size": 40,
                           "volume_type": "SATA",
                           "disk_type": "SYS"
                       },
                       {
                           "size": 100,
                           "volume_type": "SATA",
                           "disk_type": "DATA"
                       }
                   ],
                   "personality": null,
                   "instance_name": null,
                   "instance_id": null,
                   "flavorRef": "103",
                   "imageRef": "37ca2b35-6fc7-47ab-93c7-900324809c5c",
                   "key_name": "keypair01",
                   "key_fingerprint" : "SHA256:qlvdUkYgSjKUxcr2uJgJJRMCKMLkJO5BPLooBcgsF8k",
                   "public_ip": null,
                   "user_data": null,
                   "metadata": {},
                   "security_groups": [{
                        "id": "6c22a6c0-b5d2-4a84-ac56-51090dcc33be"
                   }],
               },
               "create_time": "2015-07-23T01:04:07Z"
           },
           {
               "tenant": "ce061903a53545dcaddb300093b477d2",
               "scaling_configuration_id": "24a8c5f3-c713-4aba-ac29-c17101009e5d",
               "scaling_configuration_name": "config_name_2",
               "instance_config": {
                   "disk": [
                       {
                           "size": 40,
                           "volume_type": "SATA",
                           "disk_type": "SYS"
                       }
                   ],
                   "personality": null,
                   "instance_name": null,
                   "instance_id": null,
                   "flavorRef": "103",
                   "imageRef": "37ca2b35-6fc7-47ab-93c7-900324809c5c",
                   "key_name": "keypair01",
                   "key_fingerprint" : "SHA256:qlvdUkYgSjKUxcr2uJgJJRMCKMLkJO5BPLooBcgsF8k",
                   "public_ip": null,
                   "user_data": null,
                   "metadata": {},
                   "security_groups": [{
                        "id": "6c22a6c0-b5d2-4a84-ac56-51090dcc33be"
                   }],
                   "multi_flavor_priority_policy": "PICK_FIRST"
               },
               "create_time": "2015-07-22T01:08:41Z"
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
   | 404 Not Found                     | The server cannot find the requested page.                                                 |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 405 Method Not Allowed            | You are not allowed to use the method specified in the request.                            |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 406 Not Acceptable                | The client does not accept the response generated by the server.                           |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 407 Proxy Authentication Required | The client must be authorized by the proxy before the request can proceed.                 |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 408 Request Timeout               | The request timed out.                                                                     |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 409 Conflict                      | The request cannot be processed due to a conflict.                                         |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 500 Internal Server Error         | Failed to complete the request because of an internal service error.                       |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 501 Not Implemented               | Failed to complete the request because the server does not support the requested function. |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 502 Bad Gateway                   | Failed to complete the request because the request is invalid.                             |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 503 Service Unavailable           | Failed to complete the request because the system is unavailable.                          |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 504 Gateway Timeout               | The gateway timed out.                                                                     |
   +-----------------------------------+--------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <as_07_0102>`.
