:original_name: as_faq_0015.html

.. _as_faq_0015:

What Monitoring Metrics for an AS Group Will Be Affected If OTC Tools Are Not Installed on the Instances in the Group?
======================================================================================================================

If OTC Tools have not been installed on ECS instances, Cloud Eye can monitor metrics Outband Incoming Rate and Outband Outgoing Rate. However, it cannot monitor metrics Memory Usage, Inband Incoming Rate, and Inband Outgoing Rate, which reduces data accuracy of CPU usage.

For details about monitoring metrics supported by AS, see :ref:`Table 1 <as_pro_0006__en-us_topic_0190954097_table1856812418720>`.

If OTC Tools are not installed on ECS instances, AS cannot obtain the memory usage, inband incoming rate, and inband outgoing rate.
