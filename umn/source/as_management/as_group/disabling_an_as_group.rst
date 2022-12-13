:original_name: as_01_0105.html

.. _as_01_0105:

Disabling an AS Group
=====================

Scenarios
---------

If you need to stop an instance in an AS group for configuration or upgrade, disable the AS group before performing the operation. This prevents the instance from being deleted in a health check. When the instance status is restored, you can enable the AS group again.

If a scaling action keeps failing and being retried (the failure cause can be viewed on the **Elastic Cloud Server** page) for an AS group, use either of the following methods to stop the action from being repeated:

-  Disable the AS group. Then, after the scaling action fails, it will not be retried. Enable the AS group again when the environment recovers or after replacing the AS configuration.
-  Disable the AS group and change the expected number of instances to the number of existing instances. Then after the scaling action fails, the scaling action will not be retried.

After an AS group is disabled, its status changes to **Disabled**. AS does not automatically trigger any scaling actions for a **Disabled** AS group. When an AS group has an in-progress scaling action, the scaling action does not stop immediately after the AS group is disabled.

You can disable an AS group when its status is **Enabled** or **Abnormal**.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner to select a region and a project.
#. Under **Computing**, click **Auto Scaling**. In the navigation pane on the left, choose **Instance Scaling**. Then click the **AS Groups** tab.
#. In the AS group list, locate the row containing the target AS group and click **Disable** in the **Operation** column. You can also click the AS group name and then **Disable** to the right of **Status** on the **Basic Information** page to disable the AS group.
#. In the **Disable AS Group** dialog box, click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0210485079.png
