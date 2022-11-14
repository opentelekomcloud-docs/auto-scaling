:original_name: as_faq_0019.html

.. _as_faq_0019:

How Do I Delete an ECS Instance Created in a Scaling Action?
============================================================

Handling Methods
----------------

Method 1

#. Log in to the management console.
#. Under **Computing**, click **Auto Scaling**. In the navigation pane on the left, choose **Instance Scaling**.
#. Click the AS group name on the **AS Groups** page.
#. On the AS group details page, click the **Instances** tab.
#. Locate the row that contains the instance and click **Remove and Delete** in the **Operation** column.

   .. note::

      To delete multiple instances, select the check boxes in front of them and click **Remove and Delete**.

Method 2

#. Log in to the management console.
#. Under **Computing**, click **Auto Scaling**. In the navigation pane on the left, choose **Instance Scaling**.
#. Click the AS group name on the **AS Groups** page.
#. On the AS group details page, click the **AS Policies** tab.
#. Click **Add AS Policy**. In the displayed **Add AS Policy** dialog box, add an as policy to remove instances as needed or maintain a specified number of instances.

Method 3

#. Log in to the management console.

#. Under **Computing**, click **Auto Scaling**. In the navigation pane on the left, choose **Instance Scaling**.
#. Click the AS group name on the **AS Groups** page.
#. On the AS group details page, click **Modify** in the upper right corner.
#. In the displayed **Modify AS Group** dialog box, change the value of **Expected Instances**.
