:original_name: as_04_0103.html

.. _as_04_0103:

Manual Scaling
==============

Scenarios
---------

You can manually add or remove instances to or from an AS group, or changing the expected number of instances.

Procedure
---------

**Adding instances to an AS group**

If an AS group is enabled and has no ongoing scaling action, and the current number of instances is less than the maximum, you can manually add instances to the AS group.

Before adding instances to an AS group, ensure that the following conditions are met:

-  The instances are not in other AS groups.
-  The instances are in the same VPC as the AS group.
-  The instances are in the AZs used by the AS group.
-  After the instances are added, the total number of instances is less than or equal to the maximum number of instances allowed.
-  Up to 10 instances can be added at a time.

To add instances to an AS group, perform the following steps:

#. Under **Computing**, click **Auto Scaling**. In the navigation pane on the left, choose **Instance Scaling**.
#. Click the **AS Groups** tab and then the name of the target AS group.
#. On the AS group details page, click the **Instances** tab and then **Add**.
#. Select the instances to be added and click **OK**.

**Removing instances from an AS group**

You can remove an instance from an AS group, update the instance or fix an instance fault, and add the instance back to the AS group. An instance removed from the AS group no longer carries any application traffic.

You can modify the AS configuration for an AS group at any time, but the new configuration will not be applied to any instances that are running. To apply the new configuration, stop an instance, and the system will replace it with a new one that has the specifications specified in the new configuration. You can also remove the instance from the AS group, update the instance, and add then instance back to the AS group.

There are some restrictions on instance removal:

-  The AS group cannot have a scaling action in progress, the instances must be enabled, and the total number of instances after removal cannot be less than the minimum number of instances specified.
-  Instances can be removed from an AS group and deleted only if the AS group has no scaling action ongoing, and the instances are automatically created and enabled, and are not used by Storage Disaster Recovery Service (SDRS).
-  Instances manually added to an AS group can only be removed. They cannot be removed and deleted.
-  A maximum of 10 instances can be removed at a time.

To remove an instance from an AS group, perform the following steps:

#. Under **Computing**, click **Auto Scaling**. In the navigation pane on the left, choose **Instance Scaling**.
#. Click the **AS Groups** tab and then the name of the target AS group.
#. Click the **Instances** tab, locate the row containing the target instance, and click **Remove** or **Remove and Delete** in the **Operation** column.
#. To delete multiple instances from an AS group, select the check boxes in front of them and click **Remove** or **Remove and Delete**.

To delete all instances from an AS group, select the check box on the left of **Name** and click **Remove** or **Remove and Delete**.

**Changing the expected number of instances**

Manually change the expected number of instances to add or reduce the number of instances in an AS group for expanding resources.

For details, see :ref:`Modifying an AS Group <as_01_0106>`.
