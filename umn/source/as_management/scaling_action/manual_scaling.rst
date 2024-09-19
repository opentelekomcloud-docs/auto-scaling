:original_name: as_04_0103.html

.. _as_04_0103:

Manual Scaling
==============

Scenarios
---------

You can change the size of an AS group manually. You can either add or remove instances to or from the AS group, or modify the expected number of instances of the AS group.

Procedure
---------

**Adding an instance to an AS group**

Before you add an instance to an AS group, ensure that the conditions below are met.

.. table:: **Table 1** Conditions for manually adding an instance to an AS group

   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | Item                              | Condition                                                                                                                                   |
   +===================================+=============================================================================================================================================+
   | AS group                          | -  The AS group is in the **Enabled** status.                                                                                               |
   |                                   | -  The AS group does not have ongoing scaling actions.                                                                                      |
   |                                   | -  The number of instances to be added plus the expected number of instances cannot exceed the maximum number of instances of the AS group. |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+
   | Instance                          | -  The instance to be added is not a member of another AS group.                                                                            |
   |                                   | -  The instance is in the same VPC as the AS group.                                                                                         |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------+

.. note::

   -  A maximum of 10 instances can be added to an AS group at a time.
   -  If the AS group has an attached load balancer, the instances will be associated with the load balancer.

To add instances to an AS group, perform the following steps:

#. Under **Computing**, click **Auto Scaling**. In the navigation pane on the left, choose **Instance Scaling**.
#. Click the **AS Groups** tab and then the name of the target AS group.
#. On the AS group details page, click the **Instances** tab and then **Add**.
#. Select the instances to be added and click **OK**.

**Removing an instance from an AS group**

You can remove an instance from an AS group, update the instance or fix an instance fault, and add the instance back to the AS group. After the instance is removed from the AS group, it no longer processes any application traffic.

For example, you can change AS configuration for an AS group at any time. New instances will be created using the new configuration, but existing instances in the AS group are not affected. To update the existing instances, you can stop them so that they can be replaced automatically. You can also remove the instances from the AS group, update them, and then add them back to the AS group.

When you remove instances from an AS group, consider the restrictions below.

.. table:: **Table 2** Constraints on manually removing an instance from an AS group

   +-----------------------------------+-----------------------------------------------------------+
   | Item                              | Constraint                                                |
   +===================================+===========================================================+
   | AS group                          | -  The AS group is in the **Enabled** status.             |
   |                                   | -  The AS group does not have ongoing scaling actions.    |
   +-----------------------------------+-----------------------------------------------------------+
   | Instance                          | -  The instances are in the **Enabled** lifecycle status. |
   |                                   | -  The instances are not used by SDRS.                    |
   +-----------------------------------+-----------------------------------------------------------+

.. note::

   -  A maximum of 50 instances can be removed from to an AS group at a time.
   -  If the number of instances you are removing decreases the number of instances in the AS group below the minimum number of instances allowed, AS launches new instances to maintain the expected capacity.
   -  If you remove instances from an AS group that has an associated load balancer, the instances will be dissociated from the load balancer.

To remove instances from an AS group, perform the following steps:

#. Under **Computing**, click **Auto Scaling**. In the navigation pane on the left, choose **Instance Scaling**.

#. Click the **AS Groups** tab and then the name of the target AS group.

#. Click the **Instances** tab, locate the row containing the desired instance, and click **Remove** or **Remove and Delete** in the **Operation** column.

   To remove multiple instances from the AS group, select the check boxes in front of them and click **Remove** or **Remove and Delete**.

   To remove all instances from the AS group, select the check box on the left of **Name** and click **Remove** or **Remove and Delete**.

   .. note::

      -  If the instances you want to remove were automatically added to the AS group, they are billed on a pay-per-use basis by default. You can:

         -  Remove the instances from the AS group by choosing **Remove**.

         -  Remove the instances from the AS group and delete them by choosing **Remove and Delete**.

      -  If the instances were manually added to the AS group, they can only be removed. They cannot be removed and deleted.

**Changing the expected number of instances**

Manually change the expected number of instances to add or reduce the number of instances in an AS group for expanding resources.

For details, see :ref:`Modifying an AS Group <as_01_0106>`.
