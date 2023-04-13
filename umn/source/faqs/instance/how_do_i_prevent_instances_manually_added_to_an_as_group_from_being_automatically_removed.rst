:original_name: as_faq_1904.html

.. _as_faq_1904:

How Do I Prevent Instances Manually Added to an AS Group from Being Automatically Removed?
==========================================================================================

If you have manually added N instances into an AS group and do not want these instances to be removed automatically, you can use either of the following methods to do this:

Method 1
--------

Perform following configurations in the AS group:

-  Set the minimum number of instances in the AS group to N or a larger value.
-  Set **Instance Removal Policy** to **Oldest instance created from oldest AS configuration** or **Newest instance created from oldest AS configuration**.

Based on the scaling rules, the manually added instances are not created based on the AS configuration used by the AS group. The instances automatically added using the AS configuration are removed at first. The manually added instances would not be removed until all of the automatically added instances have been removed first. Finally, since you have set the minimum number of instances to N or a larger value, those instances cannot be removed.

Note: If the instances manually added are stopped or if they malfunction, they are marked as unhealthy and removed from the AS group. This is because health checks ensure that all instances in the AS group are healthy.

Method 2
--------

Enable instance protection for these instances. For details, see :ref:`Configuring Instance Protection <as_04_0107>`.

You can enable instance protection for these instances at the same time. When the AS group scales in, protected instances will not be removed from the AS group as long as they do not fail health checks. Instances that fail health check will be removed even if they are protected.
