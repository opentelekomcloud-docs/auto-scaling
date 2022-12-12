:original_name: as_faq_1204.html

.. _as_faq_1204:

What Is the Expected Number of Instances?
=========================================

The expected number of instances refers to the number of ECS instances that are expected to run in an AS group. It is between the minimum number of instances and the maximum number of instances. You can manually change the expected number of instances or change it based on the scheduled, periodic, or alarm policies.

You can set this parameter when creating an AS group. If this value is greater than 0, a scaling action is performed to add the required number of instances after the AS group is created. You can also change this value manually or by scaling policies after the AS group is created.

If you manually change this value, the current number of instances will be inconsistent with the expected number, and a scaling action will be performed to bring the number of instances in line with the expected number.

If a scaling policy is triggered to add two instances to an AS group, the system will increase the expected number of instances by 2. Then, a scaling action is performed to add two instances so that the number of instances in the AS group is the same as the expected number.
