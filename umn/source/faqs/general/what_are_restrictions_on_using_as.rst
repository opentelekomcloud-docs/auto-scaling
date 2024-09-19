:original_name: as_faq_0003.html

.. _as_faq_0003:

What Are Restrictions on Using AS?
==================================

Only applications that are stateless and horizontally scalable can run on instances in an AS group. ECS instances in an AS group can be released automatically by AS, so they cannot be used to save application status information (such as session statuses) or related data (such as database data and logs).

If the application status or related data must be saved, you can store the information on separate servers.

.. table:: **Table 1** Quotas

   +--------------------------+---------------------------------------------------------------------+---------+
   | Item                     | Description                                                         | Default |
   +==========================+=====================================================================+=========+
   | AS group                 | Maximum number of AS groups per region per account                  | 25      |
   +--------------------------+---------------------------------------------------------------------+---------+
   | AS configuration         | Maximum number of AS configurations per region per account          | 100     |
   +--------------------------+---------------------------------------------------------------------+---------+
   | AS policy                | Maximum number of AS policies per AS group                          | 50      |
   +--------------------------+---------------------------------------------------------------------+---------+
   | Instance                 | Maximum number of instances per AS group                            | 200     |
   +--------------------------+---------------------------------------------------------------------+---------+
   | Bandwidth scaling policy | Maximum number of bandwidth scaling policies per region per account | 50      |
   +--------------------------+---------------------------------------------------------------------+---------+

-  AS requires authentication provided by Identity and Access Management (IAM).

   AutoScaling Administrator requires permissions of Tenant Guest, Server Administrator, CES Administrator, and ELB Administrator.

   .. note::

      If the CES Administrator role is not available, you cannot create alarm rules, but you can use existing alarm rules to create alarm-based scaling policies. If the ELB Administrator role is not available, you can only use existing load balancers.

-  AS resources must comply with quota requirements listed in :ref:`Table 2 <as_faq_0003__table18879114515369>`.

   .. _as_faq_0003__table18879114515369:

   .. table:: **Table 2** Quotas

      +--------------------------+---------------------------------------------------------------------+---------+
      | Item                     | Description                                                         | Default |
      +==========================+=====================================================================+=========+
      | AS group                 | Maximum number of AS groups per region per account                  | 25      |
      +--------------------------+---------------------------------------------------------------------+---------+
      | AS configuration         | Maximum number of AS configurations per region per account          | 100     |
      +--------------------------+---------------------------------------------------------------------+---------+
      | AS policy                | Maximum number of AS policies per AS group                          | 50      |
      +--------------------------+---------------------------------------------------------------------+---------+
      | Instance                 | Maximum number of instances per AS group                            | 200     |
      +--------------------------+---------------------------------------------------------------------+---------+
      | Bandwidth scaling policy | Maximum number of bandwidth scaling policies per region per account | 50      |
      +--------------------------+---------------------------------------------------------------------+---------+
