:original_name: as_faq_0035.html

.. _as_faq_0035:

What Is a Cooldown Period and Why Is It Required?
=================================================

A cooldown period specifies how long any alarm-triggered scaling action will be disallowed after a previous scaling action is complete. This cooldown period does not work for scheduled or periodic scaling actions.

Before an instance is put into use after it is added to the AS group, it takes 2 to 3 minutes to execute the configuration script to install and configure applications. The time varies depending on many factors, such as the instance specifications and startup scripts. If an instance is put into use without cooldown, the system will keep adding instances until the load decreases. As the new instances take over services, the system will detect that the load is too low and start removing instances from the AS group. A cooldown prevents the AS group from repeatedly triggering unnecessary scaling actions.

For example:

When a traffic peak occurs, an alarm policy is triggered and AS automatically adds an instance to the AS group to help handle the increased load. However, it takes time for the instance to start. After the instance is started, it takes time to receive requests from ELB. During this period, alarms may continue to be triggered and instances may continue to be added. If you set a cooldown time, after an instance is started, AS stops adding new instances in response to the alarms until the specified period of time (300 seconds by default) passes. That way the newly started instance has time to start processing application traffic. If an alarm is triggered again after the cooldown period elapses, AS starts another instance and the cooldown period starts up again.
