:original_name: as_06_0101.html

.. _as_06_0101:

Health Check
============

A health check removes abnormal instances from an AS group. Then, AS adds new instances to the AS group so that the number of instances is the same as the expected number. There are two types of AS group health check.

-  **ECS health check**: checks ECS instance running status. If an instance is stopped or deleted, it is considered as abnormal. **ECS health check** is the default health check mode for an AS group. The AS group periodically uses the check result to determine the running status of every instance in the AS group. If the health check results show that an instance is unhealthy, AS removes the instance from the AS group.
-  **ELB health check**: determines ECS instance running status using a load balancing listener. If the AS group uses load balancers, the health check method can also be **ELB health check**. If you add multiple load balancers to an AS group, an ECS instance is considered to be healthy only when all load balancers detect that the instance status is healthy. If any load balancer detects that an instance is unhealthy, the instance will be removed from the AS group.

In both **ECS health check** and **ELB health check** methods, AS removes unhealthy instances from AS groups. However, the removed instances are processed differently in the following two scenarios:

For instances automatically added to an AS group during scaling actions, AS removes and deletes them. For instances manually added to an AS group, AS only removes them from the AS group.

When an AS group is disabled, checking instance health status continues. However, AS will not remove instances.
