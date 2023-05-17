:original_name: as_07_0201.html

.. _as_07_0201:

Introduction
============

This section describes fine-grained permissions management for your AS resources. If your account does not need individual IAM users, you may skip this section.

By default, new IAM users do not have any permissions granted. You need to add a user to one or more groups, and assign policies or roles to these groups. The user then inherits permissions from the groups it is a member of. This process is called authorization. After authorization, the user can perform specified operations on AS based on the permissions.

You can grant users permissions by using roles and policies. Roles: A type of coarse-grained authorization mechanism that defines permissions related to user responsibilities. Policies define API-based permissions for operations on specific resources under certain conditions, allowing for more fine-grained, secure access control of cloud resources.

.. note::

   Policy-based authorization is useful if you want to allow or deny access to an API.

An account has all of the permissions required to call all APIs, but IAM users must have the required permissions specifically assigned. The permissions required for calling an API are determined by the actions supported by the API. Only users that have been granted permissions allowing the actions can call the API successfully. For example, if an IAM user wants to query AS groups using an API, the user must have been granted permissions that allow the **as:groups:list** action.

Supported Actions
-----------------

Operations supported by a fine-grained policy are specific to APIs. The following describes the headers of the action tables provided in this chapter:

-  Permissions: defined by actions in a custom policy.
-  APIs: REST APIs that can be called in a custom policy.
-  Actions: added to a custom policy to control permissions for specific operations.
-  Related actions: actions on which a specific action depends to take effect. When assigning permissions for the action to a user, you also need to assign permissions for the dependent actions.
-  IAM projects or enterprise projects: scope of users a permission is granted to. Policies that contain actions supporting both IAM and enterprise projects can be assigned to user groups and take effect in both IAM and Enterprise Management. Policies that only contain actions supporting IAM projects can be assigned to user groups and only take effect for IAM. Such policies will not take effect if they are assigned to user groups in Enterprise Project. Administrators can check whether an action supports IAM projects or enterprise projects in the action list. "Y" indicates that the action supports the project and "x" indicates that the action does not support the project.

AS supports the following actions that can be defined in custom policies:

-  :ref:`AS group <as_05_0202>` actions, including actions supported by all AS group APIs, such as the APIs for creating, modifying, and querying an AS group.
-  :ref:`AS configuration <as_07_0203>` actions, including actions supported by all AS configuration APIs, such as the APIs for creating, deleting, and querying AS configurations.
-  :ref:`Instance <as_07_0204>` actions, including actions supported by all instance APIs, such as the APIs for querying the instances in an AS group and removing instances from an AS group.
-  :ref:`AS policy <as_07_0205>` actions, including actions supported by all AS policy APIs, such as the APIs for creating and modifying an AS policy.
-  :ref:`AS policy execution log <as_07_0206>` actions, including the action supported by the API for querying AS policy execution logs.
-  :ref:`Scaling action log <as_07_0207>` actions, including actions supported by the APIs for querying scaling action logs.
-  :ref:`Quota <as_07_0208>` actions, including actions supported by all AS quota APIs, such as the API for querying AS quotas.
-  :ref:`Notification <as_07_0209>` actions, including actions supported by all AS notification APIs, such as the API for querying notifications of an AS group.
-  :ref:`Lifecycle hook <as_07_0210>` actions, including actions supported by all lifecycle hook APIs, such as the API for creating a lifecycle hook.
-  :ref:`Tag management <as_07_0211>` actions, including actions supported by all AS tag APIs, such as the API for querying tags.
