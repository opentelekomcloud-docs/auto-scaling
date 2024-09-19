:original_name: as_01_0106.html

.. _as_01_0106:

Modifying an AS Group
=====================

Scenarios
---------

You can modify an AS group if needed. The values of the following parameters can be changed: **Name**, **Max. Instances**, **Min. Instances**, **Expected Instances**, **Cooldown Period**, **Health Check Method**, **Enterprise project**, **Instance Removal Policy**, **EIP**, **Notification Mode**, and **Health Check Interval**.

.. note::

   Changing the value of **Expected Instances** will trigger a scaling action. AS will automatically increase or decrease the number of instances to the value of **Expected Instances**.

If the AS group is not enabled, contains no instances, and has no scaling action ongoing, you can modify **Subnet** and **Load Balancing** configurations.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner to select a region and a project.
#. Under **Computing**, click **Auto Scaling**. In the navigation pane on the left, choose **Instance Scaling**. Then click the **AS Groups** tab.

4. In the AS group list, locate the AS group you want to modify and choose **More** > **Modify** in the **Operation** column.

   You can also click the AS group name to switch to the **Overview** page, and click **Modify** in the upper right corner.

5. In the **Modify AS Group** dialog box, modify related data, for example, the expected number of instances.

6. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0210485079.png
