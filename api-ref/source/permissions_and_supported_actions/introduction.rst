:original_name: as_07_0201.html

.. _as_07_0201:

Introduction
============

You can use Identity and Access Management (IAM) for fine-grained permissions management of your AS resources. If your account does not need individual IAM users, you can skip this section.

By default, new IAM users do not have any permissions assigned. You need to add a user to one or more groups, and assign policies or roles to these groups. The users then inherit permissions from the groups and can perform specified operations on cloud services based on the permissions.

You can grant users permissions by using roles and policies. Roles: A type of coarse-grained authorization mechanism that defines permissions related to user responsibilities. Policies define API-based permissions for operations on specific resources under certain conditions, allowing for more fine-grained, secure access control of cloud resources.

.. note::

   Policy-based authorization is useful if you want to allow or deny access to an API.

An account has all of the permissions required to call all APIs, but IAM users must have the required permissions specifically assigned. The required permissions are determined by the actions supported by the API. Only users with the policies allowing for those actions can call the API successfully. For example, if an IAM user wants to query AS groups using an API, the user must have been granted permissions that allow the **as:groups:list** action.

Supported Actions
-----------------

Operations supported by a fine-grained policy are specific to APIs. The following describes the headers of the action tables provided in this chapter:

-  Permissions: defined by actions in a custom policy.
-  APIs: REST APIs that can be called by a user who has been granted specific permissions
-  Actions: specific operations that are allowed or denied
-  Dependencies: actions which a specific action depends on. When allowing an action for a user, you also need to allow any existing action dependencies for that user.
-  IAM projects/Enterprise projects: the authorization scope of a custom policy. A custom policy can be applied to IAM projects or enterprise projects or both. Policies that contain actions for both IAM and enterprise projects can be used and take effect for both IAM and Enterprise Management. Policies that contain actions only for IAM projects can be used and applied to IAM only. Administrators can check whether an action supports IAM projects or enterprise projects in the action list. "Y" indicates that the action supports the project and "x" indicates that the action does not support the project.

AS supports the following actions in custom policies:

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
