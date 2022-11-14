:original_name: as_04_0101.html

.. _as_04_0101:

Dynamic Scaling
===============

Before using AS to perform scaling actions, you must specify how to perform the scaling actions to dynamically expand resources.

If the demands change frequently, you can configure alarm-based policies to scale resources. When the conditions for invoking an AS policy are met, AS automatically changes the expected number of instances to trigger a scaling action to scale up or down resources. For details about how to create an alarm policy, see :ref:`Creating an AS Policy <as_03_0102>`.

Consider a train ticket booking application. If the CPU usage of the instances that run the application goes up to 90%, an instance needs to be added to ensure that services run properly. If the CPU usage drops down to 30%, an instance needs to be deleted to prevent resource waste. To meet the requirements, you can configure two alarm policies. One policy is used to add one instance if the maximum CPU usage exceeds 90%. The other policy is used to remove an instance if the minimum CPU usage drops below 30%.
