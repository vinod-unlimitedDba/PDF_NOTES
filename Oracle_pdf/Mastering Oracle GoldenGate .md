



Types of Replication
There are two types of replication based on whether it is performed in a synchronous or asynchronous way.
      
      • Synchronous replication : Data is replicated as soon as the change occurs on the
      source. This guarantees that at any point in time the target database is an almost
      identical copy of the source database. However, there will be some latency between
      the time the change happens on the source and the time it gets applied on the target.

      • Asynchronous replication : Transactions are written only to the primary database
      system and sent to the remote database at a later time. Because of this lag, the target
      database may not be an identical copy of the source.


some of the other popular replication solutions by non-Oracle vendors.
• Materialized views (snapshots) : A materialized view creates a copy of the source at a
single point in time on the target database. The advantage of creating materialized
views is that it enables local access to data and thus improves response time
and availability. 

The disadvantage of materialized views is that they are not real time. There is no
continuous availability. They can replicate only data and in one direction only.



• Oracle advanced replication : Oracle supports multimaster replication in which
replication happens via creating push jobs on each replication site.


• Oracle Streams replication : Oracle Streams allows movement of data, transactions, or
events in data streams either within a database or from one database to another. The
user can control what information to put into the stream, how the stream will flow
from one node to another, how the stream events behave when they move through
a node, and the termination of the streams.


• Oracle Data Guard : Oracle Data Guard provides a software infrastructure to manage,
monitor, and automate the creation of one or more standby databases. Data Guard is
a unique replication solution among other Oracle replication solutions as it supports
both synchronous and asynchronous configurations.
The switchover to a standby
database can be done manually or automatically in situations of disaster for missioncritical
applications. The standby database can be both physical and logical.

Pysical - exact copy
logical - sql apply little different from primary


• Oracle GoldenGate : Oracle GoldenGate is a real-time replication solution offering     by Oracle for heterogeneous environments.
  This is by far the best and most reliable replication solution that can be implemented across different types of databases.
  
  
  
  major benefits of Oracle GoldenGate:
  -------------------------------------
• Real time : Replication happens in real time. Changes flow from the source to the target within subseconds.
• High performance : It supports thousands of records flowing in batches with almost no performance impact on the source and target systems.
• Reliability : All committed records are delivered even in the event of a network disruption.
• Heterogeneity : It supports different database systems and platforms.
• Flexible topology support: It supports different database topologies like unidirectional, bi-directional, one to one, one to many, and multimaster.
• Conflict detection and resolution : In a multimaster configuration where multiple systems can modify separate instances of same table, conflicts may    occur. Oracle GoldenGate comes with the capability to handle such conflicts.
• Data encryption : Data can be encrypted at the source and sent over a TCP/IP network to a the target system where it is decrypted and then applied      to the target database.
• Routing and compression : Since Oracle GoldenGate uses TCP/IP network for routing information, it can compress and route information in different     database topologies irrespective of geographical distances.
• Deferred apply : The user has the option for both immediate and deferred application of transactional changes on the target system.

most popular business requirements where you can implement and take advantage of
Oracle GoldenGate:
• The business needs load balancing in a production environment. An active-active configuration of the source and the target can help balance the load     among multiple database systems.
• The business wants to implement query offloading. Long-running read-only transactions can be offloaded to an active standby database and thus           improve the overall performance of production systems.
• The business wants to create and manage a live, active standby database with up-to the-minute data. This minimizes recovery time for mission-          critical systems.
• The business needs to integrate an Oracle database with a non-Oracle database or a non-Oracle database with another non-Oracle database.
• The business requires zero downtime migrations and upgrades.


Oracle GoldenGate vs. Data Guard
------------------------


Oracle Data Guard is a popular replication solution implemented across industries. Oracle GoldenGate is
not a replacement for Oracle Data Guard and is sometimes used along with Oracle Data Guard to support
specific business needs such as downstream real-time replication

|oralce GG |vs Oracle DG|
---------- | ----------
|Oracle GoldenGate supports multiple replication topologies. | Oracle Data Guard supports simple one-way replication only.|
|The target database can be read-write. | The physical standby database is read-only when using an Active Data Guard configuration. In the rest of the                                            other cases, to make your standby database open and read-only|
|I/O overhead and capture processing overhead on primary databases.| There is no I/O overhead or capture processing overhead on the primary.|
|Few data types are not supported.| There is no restriction of data types.|
|Oracle GoldenGate comes as middleware installed separately from the Oracle database.| It is integrated with Oracle database software.|
|Oracle GoldenGate is a heterogeneous player supporting a wide range of database environments.| It supports replication only between Oracle databases.|
|The source and target databases can be of different versions.| The standby database used for replication should be the same version as the primaryOracle database.|
|The Oracle GoldenGate source and target databases can be on different OS platforms.|Oracle Data Guard requires both the primary and standby databases                                                                                      to be on the same OS platform.|




