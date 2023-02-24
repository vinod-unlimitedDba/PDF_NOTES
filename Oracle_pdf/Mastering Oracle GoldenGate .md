



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



Oracle GoldenGate 12 c is a new, improved, and enhanced version of Oracle GoldenGate. Listed here

• Support for Oracle Database 12 c multitenant architecture.
• Oracle Universal Installer support.
• Integrated replicat feature for Oracle databases.
• Coordinated replicat feature for non-Oracle databases.
• Inclusion of metadata in trail files via a table definition record (TDR). Thus, you are
no longer required to create definition files containing table metadata on the target
system.
• Ease of monitoring channel lags using an automatic heartbeat table.
• Improved trail file recovery. In the case of a bad trail file or missing trail files, you can
delete the bad trail files and bounce the extract process. It will automatically rebuild
the required trail files.
• Support for quick-and-easy logical design of GoldenGate solutions using
GoldenGate Studio.
• Nine-digit trail file sequence to support 1 billion files per trail.
• Expanded heterogeneous support.
• Enhanced security with the introduction of a wallet and master key.
• Support for Big Data.
• Support for private and public cloud systems.
• Repair capabilities in Oracle GoldenGate Veridata.


CHAPTER 2  Architecture
----------------------

Basic Oracle GoldenGate architecture. The extract process captures database
changes from the database transaction logs and writes them to the source trails. These source trails are
pumped (or passed) by data pumps to the target system where a dynamic collector process writes them
to disk as remote trails. A replicat reads these remote trails and writes the database changes on the target
system.

![image](https://user-images.githubusercontent.com/108070848/220599988-84b161c5-fff0-4291-8372-3a5a38fec28b.png)

Oracle GoldenGate consists of following components:
• Extract
• Data pump
• Replicat
• Trails
• Collector
• Manager
• Checkpoints


Extract
An extract is a capture process that captures an insert, update, or delete performed on a source schema. An
extract process can also be configured to capture DDL changes performed on the source DB and send them
across the target DB in the form of trails (or trail files) routed across a TCP/IP network.


There are primarily three types of extracts.
• Local extracts : This is the extract process that captures changes from database
transaction logs and writes the changes in local trail files.
• Data pumps : This is the extract process that reads the local trails generated from
the local extracts and sends them to the target server. Having a data pump in your
GoldenGate configuration is highly recommended. The advantages of having a data
pump are discussed in the following section.
• Initial load extracts : This type of extract process is configured for the initial load
of the data from the source to the target system. This extract is not configured to
capture changes from database transaction logs, but instead it captures all existing
data in the source table and loads it directly into the target table.


The extract process can be configured to capture changes as a single process to capture all tables or can
be divided into multiple extract processes with each extract process capturing changes for a set of tables. An
extract process can also be configured to capture changes for all tables in the entire schema in one single
extract using a wildcard.


Data Pump
---------
Data pumps are similar to GoldenGate extract processes. These are the secondary extract processes that
read from the source trails written by the local extract and pump them to the target over a TCP/IP network.

data pumps is not absolutely necessary but is highly recommended. 

If you do not have data pumps
configured, extracts must be configured to send the trails to the target system. The following are some of the
advantages of having a data pump:

• Protection against losing connectivity to target system : Assume that your target  system has gone down or there is a network connectivity issue. 
  In such a scenario,  not having a data pump will mean the extract process directly tries to send trails to an unreachable target host. 
  The extract process in this situation will abend since it is  no longer able to communicate and send trails to the target host.

Now assume that you have data pumps reading from source trails and pumping the trails to target over a TCP/IP network. 
In case of any connectivity issue to target system, the data pump will abend (stop working) as it will not be able to communicate to the target system. But you still have extracts running on the source and capturing and writing the changes in form of source trails on the source system.

• Filter and transformation : When you are filtering and transforming data, it is good to do this with the data pump as it may greatly reduce the unnecessary data being sent over the network and then later filtered at the target system.

• One-to-many replication: If you have multiple targets, you can configure individual data pumps for each target. When one target goes down, only the corresponding data pump is affected, and the other target systems continue to receive data.

• Many-to-one replication : In a configuration of data being consolidated from many sources to one target, data pumps allow you to store extracted     trails at the source database itself and send one trail at a time to the target.


Replicat
---------------
The extract process captures changes on the source system and writes them to local trail files. These trail files
are then sent to the target system over a TCP/IP network. A replicat is the delivery process that is configured
on the target system to read the trails and apply the changes to the target system. The changes are applied
in the database in same order as they were committed on the source system.

two types of extracts based on how and what changes are captured.

• Initial load replicat : An initial load replicat is a special replicat that is configured for the initial load of the target tables from the source tables. These replicats are used only one time during the initial load and can be deleted once their job is done.

• Replicat for change synchronization: These replicats are configured for reading changes from the remote trails and applying these changes to the target database by reconstructing the captured DML or DDL.


Trails
-------------

The extract process captures and writes the committed transactions sequentially into files called trails . These
trails are then sent across the network where they are written on the remote machine before being read by
the replicat.


There are two types of trails.
• Source trails : Trails written by the extract process on the local staging area are called source trails or local trails .

• Remote trails: Source trails are received on the target system by a background process called a collector and written to a similar trails called remote trails.These remote trails are the one that will be read by the replicat, and changes will be written to the target database.

Collector
-------------

The collector is a process that runs in the background on the target system,
receives trails from extracts, and writes them locally into remote trails for processing by the replicat.

dynamic port configuration, when identifying a connection request from the extract to the manager, the collector scans
an available port and sends this port information to the manager for establishing a connection with the extract process.

Manager
----------
The manager is the main process that runs and controls all other Oracle GoldenGate processes and components.
It contains control information for processes configured on the specific Oracle GoldenGate instance.

• Maintains the port number for communication over the network
• Starts and stops the extracts and replicat
• Generates reports for the processes
• Contains control parameters like “Purge old trails,” and so on
• Manages trail files


Checkpoints
--------------------------------------
Checkpoints are the way GoldenGate keeps track of which transaction it has replicated. GoldenGate extracts
create checkpoints for their position in the source database and trail.

extract captures only committed transactions, it tracks all the open transactions. Once a transaction is committed, extracts look behind the oldest
open transaction position. This information is written by the extract on the disk in the form of checkpoint files.

replicat, on the other hand, creates checkpoints for its position in the trail. This information is
more effectively stored in checkpoint tables created in the target database. GoldenGate also stores this
information on the disk in the form of checkpoint files.



The flexible and decoupled architecture of GoldenGate allows it to support a varied range of replication topologies. 
The following are some of the most common supported replication topologies:
• Unidirectional replication
• Bidirectional replication
• One-to-many replication
• Many-to-one replication
• Peer-to-peer replication

Unidirectional Replication
----------------------------
A unidirectional replication between a source and a target is the simplest replication topology. Any database
change on the source is replicated to the target. In this architecture, the target is read-only, and the changes
are made only at the source database.

![image](https://user-images.githubusercontent.com/108070848/220911954-260c2ae4-9442-4239-bc57-be0c47f8b0b0.png)


When to Use Unidirectional Replication?
The following are some of the business scenarios when you would need to implement a simple
unidirectional replication between two database systems.
• To maintain a hot standby database for failover purpose
• For query offloading on a standby database
• For zero-downtime database upgrades or migration


components of Oracle GoldenGate in a unidirectional replication configuration:


![image](https://user-images.githubusercontent.com/108070848/220912179-d745d104-79d8-458e-bcc6-049f459df733.png)


Bidirectional Replication
----------------------------------
In a bidirectional replication configuration, database changes may occur on either of the two systems. Either
of the two systems can be the source or the destination. This is also known as two-way replication or an
active-active replication since both the systems are active and receive transaction changes.

A bidirectional active-active configuration should have identical objects and data. 
Transactions can be performed on either database and are replicated to the other database by Oracle GoldenGate for consistency


![image](https://user-images.githubusercontent.com/108070848/220912420-7f2d1c07-c4a3-4c96-8bb2-99a22a8ab9bb.png)


Limitations of Bidirectional Configuration
----------------------
For data consistency, often one of the two sites is considered to be the master.
Truncates are not supported in bidirectional replication. This means you cannot allow truncate operations to replicated from any of the
two sites.


When to Use Bidirectional Replication?

• Active-active high availability system : In a high availability configuration, if one database server crashes because of software or hardware failure, the application can be restarted to point another database without having to wait for the crashed
database to be fixed. 

• Load sharing : This configuration is used for load sharing among the two databases. This boosts the overall database system performance to a higher
grade. To allow load sharing without any changes to the application and database configuration, the two databases participating in load sharing should
be identical.


• Disaster tolerance : A bidirectional replication configuration can be used for disaster tolerance as well. When one database goes down, the other database continues to support application. Once the failed database is back, it is synchronized and made consistent with the other database.

• Zero-downtime upgrades : A bidirectional replication configuration can be used for database upgrades with zero downtime involved. You can set up bidirectional replication between the existing and new databases.


![image](https://user-images.githubusercontent.com/108070848/220913967-55805036-9558-42e7-9bf7-99ebfff2a021.png)


One-to-Many Replication
---------------------
In this configuration, a source database is synchronized across multiple target databases. This can include
both homogeneous and heterogeneous systems. Data from the source is captured and manipulated if
required and is sent across multiple target databases. It is significantly important to use data pumps in this
configuration for fault tolerance. If one target goes down, the corresponding data pump will get affected,
but other data pumps can continue sending data to the remaining target systems.


![image](https://user-images.githubusercontent.com/108070848/220914201-ae799fc1-9d71-4739-9b1c-e70b2652e5ff.png)

When to Use One-to-Many Replication?

• For reporting purpose, when source data is to be distributed across multiple target databases
• For multiple standby database to serve as backups in case of the failure of production database

![image](https://user-images.githubusercontent.com/108070848/220914355-c61f0542-d73b-459e-8351-b1bcf6e7a7cf.png)



Many-to-One Replication
---------------------------
Data is sent from multiple source databases to one repository target database. This kind of many-to-one
replication can be between both homogeneous and heterogeneous databases. Figure 2-8 shows a simple
view of many-to-one replication between databases.

![image](https://user-images.githubusercontent.com/108070848/220914552-8c26e42f-2d9f-4d93-a58e-fdf65af3c86f.png)

When to Use Many-to-One Replication?
This configuration is primarily needed in a data warehousing system. Multiple source systems send data
to a single data warehouse system. This can be effectively achieved in real time using Oracle GoldenGate


![image](https://user-images.githubusercontent.com/108070848/220914696-9bc72f28-7beb-4362-a41e-802a32b81cb8.png)


Peer-to-Peer Replication
-------------------------
Peer-to-peer or multimaster replication contains multiple master sites. It is also called an update anywhere model, 
where changes made on one site are propagated to all other sites in the architecture. This ensures global transaction concurrency and data integrity


![image](https://user-images.githubusercontent.com/108070848/220914931-651613f7-4d74-49e3-bbc8-b827eee53d84.png)


When to Use Peer-to-Peer Replication?

• Localized data access : One major business application of peer-to-peer configuration
is for providing localized data access across geographical locations

• Disaster tolerance : Such a configuration can be used for disaster tolerance as well. When one database goes down,
the other databases continue to support the application.

• For an active-active high availability system : In a configuration where both the databases are active and have an identical set of objects and data, the application user can use either of the databases for business processing.

• Load sharing : This configuration is used for load sharing among each master site. This boosts the overall database system performance to a higher grade. 

![image](https://user-images.githubusercontent.com/108070848/220915324-bd33109d-4c5b-4f9a-b042-fadea170ebe3.png)



CHAPTER 3 Oracle GoldenGate Pre-installation Tasks
-------------------------------

##### Configuring Your Database and Server for Oracle GoldenGate

Minimum requirement 

Ram 100MB and also depends on How much bulk transaction are doing

DisK 500 MB

first step is to configure environment variables specific to your database and operating system.
If you have more than one database instance on the same server, then you would need to set ORACLE_ HOME and ORACLE_SID for each GoldenGate process using SETENV statements in parameter files of each Oracle GoldenGate process.
            
            SETENV (ORACLE_HOME = “oracle home directory path here”)
            SETENV (ORACLE_SID = “SID”)

Oracle GoldenGate processes use the database shared libraries. You will need to set the shared library variable for this purpose.

Set LD_LIBRARY_PATH if you are using HP-UX, Linux, or Sun Solaris OS and LIBPATH if you are using the IBM AIX operating system.
       
            export PATH=$PATH:/app/ggs/tiger/:.
            export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/app/oracle/product/orcl/lib/
            
 Enabling supplemental logging in Oracle databases creates a supplemental log group for each table; this log group contains the list of columns
for which supplemental logging will be captured.       

To check supplement logging hapenning or not in the database 

        SELECT supplemental_log_data_min, force_logging FROM v$database;

can only set supplemental minimal logging and add table/schema-level supplemental logging from the GoldenGate Software Command Interface (GGSCI).
This is especially recommended when only a few tables/schema are to be replicated
      SQL> ALTER DATABASE ADD SUPPLEMENTAL LOG DATA;
Optionally, you can enable force logging for the entire database.
      SQL> ALTER DATABASE FORCE LOGGING;
After changing logging option, either FORCE LOGGING or MINIMAL SUPPLEMENTAL LOGGING , you must switch log files, as follows:
      SQL> ALTER SYSTEM SWITCH LOGFILE;

You must enable GoldenGate replication before you can add supplemental logging information for Oracle GoldenGate. Run the following using the sysdba user:
      SQL> ALTER SYSTEM SET ENABLE_GOLDENGATE_REPLICATION=TRUE;
System altered.

Log in to GGSCI and enable supplemental logging for the GoldenGate table/schema, as follows:
            GGSCI> DBLOGIN USERID user_name, PASSWORD password
            GGSCI> ADD SCHEMATRANDATA schema_name ALLCOLS
or as follows:
            GGSCI> ADD SCHEMATRANDATA schema_name NOSCHEDULINGCOLS

To enable logging for particular tables, use ADD TRANDATA

      GGSCI> ADD TRANDATA schema_name.table_name
      
      
Enable Logging for Microsoft SQL Server Databases
----------------------------
If your source database is Microsoft SQL Server, make sure it is set to full recovery model. Log in to GGSCI and enable supplemental logging.
                  
                  GGSCI> DBLOGIN SOURCEDB <dsn>, USERID user_name, PASSWORD password
                  GGSCI> ADD TRANDATA owner_name.table_name      
previous command creates a secondary truncation log point in the SQL Server database.

Use the MANAGESECONDARYTRUNCATIONPOINT command for managing the secondary truncation log point
in the extract process.
      TRANLOGOPTIONS MANAGESECONDARYTRUNCATIONPOINT
      
 Define the interval for moving the secondary log point in SQL Server as shown here:
EXEC sp_repldone @xactid = NULL, @xact_segno = NULL, @numtrans = 0, @time = 0, @reset = 1

Enable logging for an IBM DB2 Database on the Linux/Unix/Windows platform.
The first step is to do one of the following; either enable USEREXIT or use LOGRETAIN RECOVERY :
            db2 update db cfg for database_name using USEREXIT ON
            or
            db2 update db cfg for database_name using LOGRETAIN RECOVERY
Next, set your source database to retain the transaction log for roll-forward recovery.
            db2 update db cfg for database_name using LOGARCHMETH1 LOGRETAIN
            db2 update db cfg for database_name using LOGARCHMETH2 OFF
            or
            db2 update db cfg for database_name using LOGARCHMETH1 DISK
            db2 update db cfg for database_name using LOGARCHMETH2 TSM
Verify the log retention parameters.
            db2 connect to database_name USER user_name using password
            db2 get db cfg for database_name
   
Before you restart extract process, ensure that you have taken a full backup of the database.
db2 backup db database_name to device_name
You will also need to set the OVERFLOWLOGPATH parameter to the archive log directory.
Log in to GGSCI and enable supplemental logging for the tables to be replicated.
GGSCI> DBLOGIN SOURCEDB dsn, USERID user_name , PASSWORD password


Supported Data Types for Oracle Databases

• Abstract data type
• BASICFILE Lob
• BINARY DOUBLE
• BINARY FLOAT
• BLOB
• CHAR
• CLOB
• Clustered table
• DATE
• DATETIME
• Index organized tables
• LONG
• LONG RAW
• Materialized view
• NCHAR
• NCLOB
• Nested tables
• NUMBER
• NVARCHAR2
• Object table
• PDML
• RAW
• SECUREFILE Lob
• Sequence
• TIMESTAMP
• Transparent data encryption
• VARCHAR2
• VARRAY
• XA
• XML stored as CLOB / Binary


Oracle GoldenGate supports DDL operations approximately up to 2 MB for the following Oracle
objects:
• Cluster                               • Sequence
• Function                              • Synonym
• Index                                 • Table
• Materialized view                     • Tablespace
• Package                               • Trigger
• Procedure                             • Type
• Role                                  • User
• View

Supported Data Types for SQL Server Databases
Oracle GoldenGate supports all SQL Server data types except SQL_VARIANT .
Supported Data Types for DB2 Databases on LUW
On the Linux, Unix, or Windows platform, Oracle GoldenGate supports all IBM DB2 data types except the
XML data type, user-defined data types, and negative dates.
Supported Data Types for DB2 Databases on z/OS
On a z/OS platform, Oracle GoldenGate supports all DB2 data types except XML, user-defined data types,
negative dates, and DECFLOAT .






Supported Data Types for SQL Server Databases
Oracle GoldenGate supports all SQL Server data types except SQL_VARIANT .
Supported Data Types for DB2 Databases on LUW
On the Linux, Unix, or Windows platform, Oracle GoldenGate supports all IBM DB2 data types except the
XML data type, user-defined data types, and negative dates.
Supported Data Types for DB2 Databases on z/OS
On a z/OS platform, Oracle GoldenGate supports all DB2 data types except XML, user-defined data types,
negative dates, and DECFLOAT .




SEQUENCES are supported in an active-passive replication structure. The source and target sequence
must have identical cache size and incremental interval values.
DDL operations approximately up to 2 MB are supported on the following Oracle objects:

The TRUNCATE statement is supported, however, in active-active bidirectional replication. TRUNCATES must always originate on the same server.
No DDL operations are supported on Oracle reserved schemas.

   
            


      

 


            
            











