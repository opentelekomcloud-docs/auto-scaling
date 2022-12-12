:original_name: faq_443.html

.. _faq_443:

Will an Abrupt Change in Monitoring Metric Values Trigger an Unnecessary Scaling Action?
========================================================================================

No. Monitoring data used by AS is from Cloud Eye. The monitoring period can be set to 5 minutes, 20 minutes, or 1 hour, so an abrupt change in monitoring metric values will not impact scaling actions.

In addition, AS allows you to configure a cooldown period to prevent unnecessary scaling actions caused by frequently reported alarms. You can customize the cooldown period as needed.
