:original_name: as_07_0103.html

.. _as_07_0103:

AS Custom Policies
==================

Scenarios
---------

Custom policies can be created to supplement the system-defined policies of AS. For the actions that can be added to custom policies, see "Permissions Policies and Supported Actions" in *Auto Scaling API Reference*.

You can create custom policies in either of the following ways:

-  Visual editor: Select cloud services, actions, resources, and request conditions. This does not require knowledge of policy syntax.
-  JSON: Edit JSON policies from scratch or based on an existing policy.

For operation details, see `Creating a Custom Policy <https://docs.otc.t-systems.com/identity-access-management/umn/user_guide/permissions/creating_a_custom_policy.html>`__. The following section contains examples of common AS custom policies.

Example Custom Policies
-----------------------

-  Example 1: Allowing users to remove instances from an AS group and create AS configurations

   .. code-block::

      {
            "Version": "1.1",
            "Statement": [
                  {
                        "Effect": "Allow",
                        "Action": [
                              "as:instances:delete",
                              "as:configs:create"
                        ]
                  }
            ]
      }

-  Example 2: Denying AS group deletion

   A policy with only "Deny" permissions must be used together with other policies. If the permissions assigned to a user contain both "Allow" and "Deny", the "Deny" permissions take precedence over the "Allow" permissions.

   Assume that you need to grant the permissions of the **AutoScaling FullAccess** policy to a user but want to prevent the user from deleting AS groups. You can create a custom policy for denying AS group deletion, and attach this policy together with the **AutoScaling FullAccess** policy to the user. As an explicit deny in any policy overrides any allows, the user can perform all operations on AS excepting deleting AS groups. The following is an example of a deny policy:

   .. code-block::

      {
              "Version": "1.1",
              "Statement": [
                      {
                              "Action": [
                                      "as:groups:delete"
                              ],
                              "Effect": "Deny"
                      }
              ]
      }
