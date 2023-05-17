:original_name: as_01_0104.html

.. _as_01_0104:

Enabling an AS Group
====================

Scenarios
---------

You can enable an AS group to automatically scale capacity in or out.

After an AS group is enabled, its status changes to **Enabled**. AS monitors the AS policy and triggers a scaling action for AS groups only in **Enabled** state. After an AS group is enabled, AS triggers a scaling action to automatically add or remove instances if the number of instances in the AS group is different from the expected number of instances.

-  Only AS groups in the **Disabled** state can be enabled.
-  Only AS groups in the **Abnormal** state can be forcibly enabled. You can choose **More** > **Forcibly Enable** to enable an abnormal AS group. Forcibly enabling an AS group does not have adverse consequences.
-  After you create an AS group and add an AS configuration to an AS group, the AS group is automatically enabled.


Enabling an AS Group
--------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner to select a region and a project.
#. Under **Computing**, click **Auto Scaling**. In the navigation pane on the left, choose **Instance Scaling**. Then click the **AS Groups** tab.
#. In the AS group list, locate the row containing the target AS group and click **Enable** in the **Operation** column. You can also click the AS group name and then **Enable** to the right of **Status** on the **Basic Information** page to enable the AS group.
#. In the **Enable AS Group** dialog box, click **Yes**.

Forcibly Enabling an AS Group
-----------------------------

#. Log in to the management console.
#. Click |image2| in the upper left corner to select a region and a project.
#. Under **Computing**, click **Auto Scaling**. In the navigation pane on the left, choose **Instance Scaling**. Then click the **AS Groups** tab.
#. In the AS group list, locate the row containing the target AS group and select **Forcibly Enable** from the **More** drop-down list in the **Operation** column. You can also click the AS group name and then **Forcibly Enable** to the right of **Status** on the **Basic Information** page to enable the AS group.
#. In the **Forcibly Enable AS Group** dialog box, click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0210485079.png
.. |image2| image:: /_static/images/en-us_image_0210485079.png
