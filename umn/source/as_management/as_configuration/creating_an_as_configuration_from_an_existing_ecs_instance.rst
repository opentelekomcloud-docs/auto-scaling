:original_name: as_02_0102.html

.. _as_02_0102:

Creating an AS Configuration from an Existing ECS Instance
==========================================================

Scenarios
---------

You can use an existing ECS instance to rapidly create an AS configuration. In such a case, the parameter settings, such as the ECS type, vCPUs, memory, image, and disk settings (including size, type, encryption, and key) in the AS configuration are the same as those of the selected instance by default.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner to select a region and a project.

#. Under **Computing**, click **Auto Scaling**. In the navigation pane on the left, choose **Instance Scaling**.

#. Click **Create AS Configuration**.

#. Set the parameters for the AS configuration. :ref:`Table 1 <as_02_0102__table27476571>` lists the AS configuration parameters.

   .. _as_02_0102__table27476571:

   .. table:: **Table 1** AS configuration parameters

      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------+
      | Parameter              | Description                                                                                                                                                                                                                          | Example Value                         |
      +========================+======================================================================================================================================================================================================================================+=======================================+
      | Region                 | A region is where an AS configuration resides.                                                                                                                                                                                       | N/A                                   |
      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------+
      | Name                   | Specifies the name of an AS configuration.                                                                                                                                                                                           | N/A                                   |
      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------+
      | Configuration Template | Choose **Use specifications of an existing ECS** > **Select ECS**.                                                                                                                                                                   | Use specifications of an existing ECS |
      |                        |                                                                                                                                                                                                                                      |                                       |
      |                        | In such a case, the parameter settings, such as the ECS type, vCPUs, memory, image, and disk settings (including size, type, encryption, and key) in the AS configuration are the same as those of the selected instance by default. |                                       |
      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------+
      | EIP                    | An EIP is a static public IP address bound to an ECS in a VPC. Using the EIP, the ECS provides services externally.                                                                                                                  | Automatically assign                  |
      |                        |                                                                                                                                                                                                                                      |                                       |
      |                        | The following options are provided:                                                                                                                                                                                                  |                                       |
      |                        |                                                                                                                                                                                                                                      |                                       |
      |                        | -  Do not use                                                                                                                                                                                                                        |                                       |
      |                        |                                                                                                                                                                                                                                      |                                       |
      |                        |    An ECS without an EIP cannot access the Internet. However, it can still be used as a service ECS or deployed in a cluster on a private network.                                                                                   |                                       |
      |                        |                                                                                                                                                                                                                                      |                                       |
      |                        | -  Automatically assign                                                                                                                                                                                                              |                                       |
      |                        |                                                                                                                                                                                                                                      |                                       |
      |                        |    An EIP with a dedicated bandwidth is automatically assigned to each ECS. The bandwidth size is configurable.                                                                                                                      |                                       |
      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------+
      | Key Pair               | A key pair is used for ECS login authentication. If you select this mode, create or import a key pair on the **Key Pair** page.                                                                                                      | N/A                                   |
      |                        |                                                                                                                                                                                                                                      |                                       |
      |                        | .. note::                                                                                                                                                                                                                            |                                       |
      |                        |                                                                                                                                                                                                                                      |                                       |
      |                        |    If you use an existing key, make sure that you have saved the key file locally. Without the key, you will not be able to log in to your instance.                                                                                 |                                       |
      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------+
      | Advanced Settings      | This allows you to configure **User Data**.                                                                                                                                                                                          | N/A                                   |
      |                        |                                                                                                                                                                                                                                      |                                       |
      |                        | You can select **Do not configure** or **Configure now**.                                                                                                                                                                            |                                       |
      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------+
      | User Data              | Enables an ECS to automatically inject user data when the ECS starts for the first time. This configuration is optional. If this function is enabled, the ECS automatically injects user data during its first startup.              | N/A                                   |
      |                        |                                                                                                                                                                                                                                      |                                       |
      |                        | For details, see `Elastic Cloud Server User Guide <https://docs.otc.t-systems.com/usermanual/ecs/en-us_topic_0032380449.html>`__.                                                                                                    |                                       |
      |                        |                                                                                                                                                                                                                                      |                                       |
      |                        | The following two methods are available:                                                                                                                                                                                             |                                       |
      |                        |                                                                                                                                                                                                                                      |                                       |
      |                        | -  **As text**: allows you to enter the user data in the text box below.                                                                                                                                                             |                                       |
      |                        | -  **As file**: allows you to inject a script or other files when you create an ECS instance.                                                                                                                                        |                                       |
      |                        |                                                                                                                                                                                                                                      |                                       |
      |                        |    .. note::                                                                                                                                                                                                                         |                                       |
      |                        |                                                                                                                                                                                                                                      |                                       |
      |                        |       -  For Linux, if you use password authentication, this function is not supported.                                                                                                                                              |                                       |
      |                        |       -  If the selected image does not support user data injection, this function is not supported.                                                                                                                                 |                                       |
      +------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------+

#. Click **Create Now**.

#. If you want to use the newly created AS configuration, add it to the AS group. For details, see :ref:`Changing the AS Configuration for an AS Group <as_01_0103>`.

.. |image1| image:: /_static/images/en-us_image_0210485079.png
