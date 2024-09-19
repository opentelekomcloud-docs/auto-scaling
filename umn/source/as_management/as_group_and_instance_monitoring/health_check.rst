:original_name: as_06_0101.html

.. _as_06_0101:

Health Check
============

Health Check Methods
--------------------

A health check removes unhealthy instances from an AS group. Then, AS adds new instances to the AS group so that the number of instances is the same as the expected number. There are two types of AS group health checks.

-  **ECS health check**: checks the ECS instance running status. If an instance is stopped or deleted, it is considered abnormal. **ECS health check** is the default health check mode for an AS group. The AS group periodically uses the check result to determine the running status of every instance in the AS group. If the health check results show that an instance is unhealthy, AS removes the instance from the AS group.

-  **ELB health check**: determines ECS running status using a load balancing listener. If the AS group uses load balancers, the health check method can also be **ELB health check**.

   If you add multiple load balancers to an AS group, an ECS instance is considered to be healthy only when all load balancers detect that the instance is healthy. If any load balancer detects that an instance is unhealthy, the instance will be removed from the AS group.

In both **ECS health check** and **ELB health check** modes, AS removes unhealthy instances from the AS group. Whether a removed instance will be deleted depends on how the instance is added to the AS group.

If the instance is automatically added to the AS group during a scaling action, AS removes and deletes it. If the instance is manually added to the AS group, AS only removes it from the AS group.

Constraints
-----------

-  Even when an AS group is disabled, AS still checks the health of instances in the AS group, but does not remove unhealthy instances.
