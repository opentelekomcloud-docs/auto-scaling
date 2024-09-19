:original_name: as_pro_0003.html

.. _as_pro_0003:

Constraints
===========

Function Restrictions
---------------------

AS has the following restrictions:

-  Only applications that are stateless and horizontally scalable can run on instances in an AS group.

   .. note::

      -  A stateless process or application can be understood in isolation. There is no stored knowledge of or reference to past transactions. Each transaction is made as if from scratch for the first time.

         ECS instances where stateless applications are running do not store data that needs to be persisted locally.

         Think of stateless transactions as a vending machine: a single request and a response.

      -  Stateful applications and processes, however, are those that can be returned to again and again. They are performed in the context of previous transactions and the current transaction may be affected by what happened during previous transactions.

         ECS instances where stateful applications are running store data that needs to be persisted locally.

         Stateful transactions are performed repeatedly, such as online banking or e-mail, which are performed in the context of previous transactions.

-  AS can release ECS instances in an AS group automatically, so the instances cannot be used to save application status information (such as session statuses) or related data (such as database data and logs). If the application status or related data must be saved, you can store the information on separate servers.

-  AS does not support capacity expansion or deduction of instance vCPUs and memory.

-  AS requires authentication provided by Identity and Access Management (IAM).

   AutoScaling Administrator requires permissions of Tenant Guest, Server Administrator, CES Administrator, and ELB Administrator.

   .. note::

      If the Cloud Eye administrator is not available, you can only use an existing alarm to create an alarm policy. If the ELB administrator is not available, you can still use existing load balancers.

Quotas
------

AS resources must comply with quota requirements listed in :ref:`Table 1 <as_pro_0003__en-us_topic_0190954113_en-us_topic_0026721513_d0e195>`.

.. _as_pro_0003__en-us_topic_0190954113_en-us_topic_0026721513_d0e195:

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
