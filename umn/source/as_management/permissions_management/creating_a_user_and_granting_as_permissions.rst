:original_name: as_07_0102.html

.. _as_07_0102:

Creating a User and Granting AS Permissions
===========================================

Scenarios
---------

`IAM <https://docs.otc.t-systems.com/identity-access-management/umn/service_overview/what_is_iam.html>`__ can help you implement fine-grained permissions control over your AS resources. With IAM, you can

-  Create IAM users for employees based on your enterprise's organizational structure. Each IAM user will have their own security credentials for accessing AS resources.
-  Grant only the permissions required for users to perform a specific task.
-  Use `IAM <https://docs.otc.t-systems.com/identity-access-management/umn/service_overview/what_is_iam.html>`__ to entrust an account or cloud service to perform efficient O&M on your AS resources.

If your account does not require individual IAM users, skip this section.

This section describes the procedure for granting permissions (see :ref:`Figure 1 <as_07_0102__fig1515164216142>`).

Prerequisites
-------------

Learn about the permissions (see :ref:`Permissions Management <as_pro_0007>`) supported by AS and choose policies or roles according to your requirements. For the permissions of other services, see `Permission Description <https://docs.otc.t-systems.com/additional/permissions.html>`__.

Process Flow
------------

.. _as_07_0102__fig1515164216142:

.. figure:: /_static/images/en-us_image_0171188722.jpg
   :alt: **Figure 1** Process for granting AS permissions

   **Figure 1** Process for granting AS permissions

#. .. _as_07_0102__li10176121316284:

   `Create a user group and assign permissions to it <https://docs.otc.t-systems.com/identity-access-management/umn/getting_started/creating_a_user_group_and_assigning_permissions.html#iam-01-0030>`__.

   Create a user group on the IAM console, and attach the **AutoScaling ReadOnlyAccess** policy to the group.

#. `Create an IAM user and add it to the user group <https://docs.otc.t-systems.com/identity-access-management/umn/user_guide/user_and_user_group_management/creating_a_user.html#en-us-topic-0046611303>`__.

   Create a user on the IAM console and add the user to the group created in :ref:`1 <as_07_0102__li10176121316284>`.

#. `Log in <https://docs.otc.t-systems.com/identity-access-management/umn/getting_started/logging_in_as_a_user.html#iam-01-0032>`__ and verify permissions.

   Log in to the AS console as the created user, and verify the user's permissions for AS.

   -  Choose **Service List** > **Auto Scaling**. Then, click **Create AS Group** on the AS console. If a message appears indicating that you have insufficient permissions to perform the operation, the **AutoScaling ReadOnlyAccess** policy has already taken effect.
   -  Choose any other service in the **Service List**. If a message appears indicating that you have insufficient permissions to access the service, the **AutoScaling ReadOnlyAccess** policy has already taken effect.
