:original_name: as_pro_0007.html

.. _as_pro_0007:

Permissions Management
======================

If you need to assign different permissions to employees in your enterprise to access your AS resources, Identity and Access Management (IAM) is a good choice for fine-grained permissions management. IAM provides identity authentication, permissions management, and access control, helping you securely access to your resources.

With IAM, you can create IAM users and assign permissions to the users to control their access to specific resources. For example, you can assign permissions to allow some software developers to use AS resources but disallow them to delete or perform any high-risk operations on the resources.

If your account does not need individual IAM users for permissions management, skip this section.

IAM can be used free of charge. You pay only for the resources in your account. For more information about IAM, see `IAM Service Overview <https://docs.otc.t-systems.com/en-us/usermanual/iam/iam_01_0026.html>`__.

AS Permissions
--------------

By default, new IAM users do not have any permissions assigned. You need to add them to one or more groups and attach policies or roles to these groups so that these users can inherit permissions from the groups and perform specified operations on cloud services.

When you grant AS permissions to a user group, set **Scope** to **Region-specific projects** and then select projects for the permissions to take effect. If you select **All projects**, the permissions will take effect for the user group in all region-specific projects. When accessing AS, the users need to switch to a region where they have been authorized to use this service.

You can grant users permissions by using roles and policies.

-  Roles: A type of coarse-grained authorization mechanism that defines permissions related to user responsibilities. This mechanism provides only a limited number of service-level roles for authorization. When using roles to grant permissions, you need to also assign other roles on which the permissions depend to take effect. However, roles are not an ideal choice for fine-grained authorization and secure access control.

-  Policies: A type of fine-grained authorization mechanism that defines permissions required to perform operations on specific cloud resources under certain conditions. This mechanism allows for more flexible policy-based authorization, meeting requirements for secure access control. For example, you can grant AS users only the permissions for managing a certain type of ECSs. Most policies define permissions based on APIs. For the API actions supported by AS, see "Permissions Policies and Supported Actions" in *Auto Scaling API Reference*.

   :ref:`Table 1 <as_pro_0007__table199851925151514>` lists all the system policies supported by AS.

   .. _as_pro_0007__table199851925151514:

   .. table:: **Table 1** System-defined permissions supported by AS

      +----------------------------+-----------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Policy Name                | Description                                   | Category              | Dependency                                                                                                                                              |
      +============================+===============================================+=======================+=========================================================================================================================================================+
      | AutoScaling FullAccess     | All operation permissions on all AS resources | System-defined policy | None                                                                                                                                                    |
      +----------------------------+-----------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
      | AutoScaling ReadOnlyAccess | Read-only permissions on all AS resources     | System-defined policy | None                                                                                                                                                    |
      +----------------------------+-----------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
      | AutoScaling Administrator  | All operation permissions on all AS resources | System role           | The **ELB Administrator**, **CES Administrator**, **Server Administrator**, and **Tenant Administrator** roles need to be assigned in the same project. |
      +----------------------------+-----------------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+

   :ref:`Table 2 <as_pro_0007__table1076523412110>` lists the common operations supported by each system-defined policy of AS. Select the policies as required.

   .. _as_pro_0007__table1076523412110:

   .. table:: **Table 2** Common operations supported by each system-defined policy of AS

      +-------------------------------------+------------------------+----------------------------+---------------------------+
      | Operation                           | AutoScaling FullAccess | AutoScaling ReadOnlyAccess | AutoScaling Administrator |
      +=====================================+========================+============================+===========================+
      | Creating an AS group                | Y                      | x                          | Y                         |
      +-------------------------------------+------------------------+----------------------------+---------------------------+
      | Modifying an AS group               | Y                      | x                          | Y                         |
      +-------------------------------------+------------------------+----------------------------+---------------------------+
      | Querying details about an AS group  | Y                      | Y                          | Y                         |
      +-------------------------------------+------------------------+----------------------------+---------------------------+
      | Deleting an AS group                | Y                      | x                          | Y                         |
      +-------------------------------------+------------------------+----------------------------+---------------------------+
      | Creating an AS configuration        | Y                      | x                          | Y                         |
      +-------------------------------------+------------------------+----------------------------+---------------------------+
      | Creating an AS policy               | Y                      | x                          | Y                         |
      +-------------------------------------+------------------------+----------------------------+---------------------------+
      | Creating a bandwidth scaling policy | Y                      | x                          | Y                         |
      +-------------------------------------+------------------------+----------------------------+---------------------------+
