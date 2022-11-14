:original_name: as_01_0103.html

.. _as_01_0103:

Changing the AS Configuration for an AS Group
=============================================

Scenarios
---------

If you need to change the specifications of ECS instances in an AS group, changing the AS configuration used by the AS group is an easy way to help you get there.

Effective Time of New AS Configuration
--------------------------------------

After you change the AS configuration for an AS group, the new AS configuration will not be used until any ongoing scaling actions are complete.

For example, if there is a scaling action ongoing for an AS group, and you change the AS configuration of the AS group from **as-config-A** to **as-config-B**, **as-config-A** is still used for the instances that are being added in the ongoing scaling action.

**as-config-B** will take effect in the next scaling action.


.. figure:: /_static/images/en-us_image_0282829283.png
   :alt: **Figure 1** Changing the AS configuration

   **Figure 1** Changing the AS configuration

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner to select a region and a project.

#. Under **Computing**, click **Auto Scaling**. In the navigation pane on the left, choose **Instance Scaling**. Then click the **AS Groups** tab.

#. Click the name of the AS group for which you want to change the AS configuration. On the **Basic Information** page, click **Change Configuration** to the right of **Configuration Name**.

   You can also locate the row containing the target AS group and choose **More** > **Change Configuration** in the **Operation** column.

#. In the displayed **Change AS Configuration** dialog box, select another AS configuration to be used by the AS group.

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0210485079.png
