:original_name: as_07_0102.html

.. _as_07_0102:

Creating a User and Granting AS Permissions
===========================================

Scenarios
---------

`IAM <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0026.html>`__ can help you implement fine-grained permissions control over your AS resources. With IAM, you can:

-  Create IAM users for employees based on your enterprise's organizational structure. Each IAM user will have their own security credentials for accessing AS resources.
-  Grant users only the permissions required to perform a given task based on their job responsibilities.
-  Use `IAM <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0026.html>`__ to entrust an account or cloud service to perform efficient O&M on your AS resources.

If your account does not require individual IAM users, skip this section.

This section describes the procedure for granting permissions. :ref:`Figure 1 <as_07_0102__fig1515164216142>` shows the process flow.

Prerequisites
-------------

Before granting permissions to user groups, you should learn about the permissions (:ref:`Permissions Management <as_pro_0007>`) supported by AS and choose policies or roles based on service requirements. To grant permissions for other services, learn about all `permissions <https://docs.otc.t-systems.com/permissions/index.html>`__ supported by IAM.

Process Flow
------------

.. _as_07_0102__fig1515164216142:

.. figure:: /_static/images/en-us_image_0171188722.jpg
   :alt: **Figure 1** Process for granting AS permissions

   **Figure 1** Process for granting AS permissions

#. .. _as_07_0102__li10176121316284:

   `Create a user group and assign permissions to it <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0030.html>`__.

   Create a user group on the IAM console, and assign the ASReadOnlyAccess permissions to the group.

#. `Create an IAM user and add it to the user group <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0031.html>`__.

   Create a user on the IAM console and add the user to the group created in :ref:`1 <as_07_0102__li10176121316284>`.

#. `Log in <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0032.html>`__ and verify permissions.

   Log in to the AS console as the created user, and verify the user's permissions for AS.

   -  Choose **Service List** > **Auto Scaling**. Then, click **Create AS Group** on the AS console. If a message appears indicating that you have insufficient permissions to perform the operation, the ASReadOnlyAccess policy is in effect.
   -  Choose another in the **Service List**. If a message appears indicating that you have insufficient permissions to access the service, the ASReadOnlyAccess policy is in effect.
