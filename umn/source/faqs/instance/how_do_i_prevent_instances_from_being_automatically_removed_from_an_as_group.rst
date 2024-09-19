:original_name: as_faq_0028.html

.. _as_faq_0028:

How Do I Prevent Instances from Being Automatically Removed from an AS Group?
=============================================================================

You can enable instance protection for in-service instances in an AS group. After the configuration, the protected in-service instances will not be removed during scale-in events. You can also modify the minimum number of instances for an AS group and use an instance removal policy to ensure that the AS group always has some in-service instances.

Unhealthy instances are removed from an AS group and new instances are created automatically. Do not stop or delete instances that have been added to an AS group on the ECS console as they will be marked as unhealthy and automatically removed from the AS group. Even when an AS group is disabled, AS still checks the health of instances in the AS group, but does not remove unhealthy instances.
