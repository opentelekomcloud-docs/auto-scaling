:original_name: as_faq_0020.html

.. _as_faq_0020:

When an Instance Is Removed from an AS Group and Deleted, Is the Application Data Saved?
========================================================================================

No. You must ensure that instances in the AS group do not store application status information or other important data, such as sessions, databases, and logs, or the data will be lost when AS automatically releases them. If you want to store your application status, you can store it on an independent server (such as an ECS) or database (such as an RDS database).
