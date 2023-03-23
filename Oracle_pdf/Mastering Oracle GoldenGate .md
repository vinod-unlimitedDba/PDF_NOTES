



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

Designing Your GoldenGate Replication Setup
------
An important pre-step of setting up Oracle GoldenGate replication is to understand the standard naming
conventions and best practices while designing your setup.   

PREMISSION REQUIRED FOR ogg USER 

SQL> exec dbms_goldengate_auth.grant_admin_privilege('ggsuser')

Optionally, you can specify whether you are providing the privilege to the capture or apply process as shown here:

SQL> exec dbms_goldengate_auth.grant_admin_privilege('ggsuser','capture');
SQL> exec dbms_goldengate_auth.grant_admin_privilege('ggsuser','apply');
      

OGG User Permissions in Sybase Databases In the Sybase ASE database, you can either grant system administration role sa_role to the GoldenGate user
or more specifically grant replication_role as shown here:

isql> sp_role 'grant', replication_role, ‘ggsuser’

or shown here:

isql> use database_name
isql> go
isql> grant role replication_role to ggsuser
isql> go
 

OGG User Permissions in IBM DB2 Databases Privileges required by the Oracle GoldenGate user are managed by the SYSADM or DBADM roles in the IBM DB2
database.
        
        SQL> grant DBADM to ggsuser;
        SQL> grant connect to ggsuser;
        SQL> grant select, insert, update, delete on table_name to ggsuser;
            
OGG User Permissions in MySQL Databases The Oracle GoldenGate user for MySQL databases requires read permission on the INFORMATION_SCHEMA
database. Apart from this, an extract requires the following privileges:
• SELECT ANY TABLE
• Read and Execute on the MySQL configuration file and its directory
• Read and Execute on binary logs
• Read and Execute on the tmp directory


##### CHAPTER 4 Installing Oracle GoldenGate
-------------------------------------------------

Setting Up Environmental Variables We discussed in the previous chapter setting up environment variables as a pre-installation step. Make sure
your Oracle database and Oracle GoldenGate environment variables are set as follows:

            export ORACLE_BASE=/app/oracle
            export ORACLE_HOME=$ORACLE_BASE/product/12.1.0.2/dbhome_1
            export ORACLE_SID=orcl1
            export PATH=$PATH:/app/ggs/tiger/:.
            export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$ORACLE_HOME/lib/

Supplemental logs are required only by extract processes to capture transactions for replication.
Enable minimal supplemental logging at the database level.
        
        SQL> ALTER DATABASE ADD SUPPLEMENTAL LOG DATA;
        
        
  Log in to GGSCI and enable supplemental logging for the GoldenGate table/schema.
            GGSCI> DBLOGIN USERID tiger, PASSWORD tiger123_
            Successfully logged into database
            GGSCI> ADD SCHEMATRANDATA tiger ALLCOLS      


Installing Oracle GoldenGate on Unix/Linux
--------------


Step 1: Log In as the Linux Superuser
              su - oracle
              
Step 2: Navigate to the GoldenGate Directory

              cd /u01/apps/ogg/appname/
Step 3: Copy or FTP the GoldenGate Software File from the Local System or Remote Server

      Place the .zip file in the /app/ggs/tiger directory where Oracle GoldenGate is to be installed. If you have a compressed .zip file, unzip the file. 
      You can issue following command to unzip the compressed GoldenGate software you downloaded from the Oracle web site:
        
              unzip 121200_fbo_ggs_Linux_x64_shiphome.zip
              
 Step 4: Locate the Installer
 
            For Oracle GoldenGate 12, Oracle has included a GUI installer that takes care of configuring your
            manager process and creating Oracle GoldenGate subdirectories.
            Navigate to Disk1 from the unzipped contents, as shown here:
                        [oracle@ravin-ravinpc tiger]$ cd /app/ggs/tiger/fbo_ggs_Linux_x64_shiphome/Disk1
                        [oracle@ravin-ravinpc Disk1]$ ls -lrt
                        total 12
                        drwxr-xr-x. 4 oracle oinstall 4096 Apr 29 17:15 install
                        drwxr-xr-x. 2 oracle oinstall 24 Apr 29 17:15 response
                        -rwxr-xr-x. 1 oracle oinstall 918 Apr 29 17:15 runInstaller
                        drwxr-xr-x. 11 oracle oinstall 4096 Apr 29 17:16 stage

Step 5: Begin Installation

      export DISPLAY=<your windows machine IP where X server is running>:0.0
      [oracle@ravin-ravinpc tiger]$ ./runInstaller
      
      Chose for ORacle GG for 12c or 11g  click next
      
 Step 6:  select software location
 
 click on install
 
 Once install completed successfull installation POPS UP.
 
 
 
 
 CONFIGURE MANAGER 
 ----------
 
from server export ORACLE_HOME,OGG_HOME , LIBARARY_PATH 

Oracle_server > ./ggsci

it will enter into the ggsci prompt you can golden gate commands

GGSCI>  Status all

GGSCI > EDIT PARAMS MGR
         PORT 7809
       AUTOSTART E*
       LAGINFOMINUTES 5
       LAGCRITICALMINUTES 5

Only the PORT 7809 part is mandatory for getting your manager process running.
LAGINFOMINUTES specifies how often lag information is reported to the error log file ggserror.log .
AUTOSTART automatically starts the specified extract/replicat process when the manager starts.
Here we have specified to start all processes (channels) starting with E when the manager starts


Step 7: Start/Stop the Manager
       
        GGSCI> START MGR
        GGSCI> STOP MGR
        GGSCT> view report mgr
      
      
Step 8: Check Supplemental Logging for the Database
 
SELECT supplemental_log_data_min, force_logging FROM v$database;

If both of the previous are already YES , your database is already configured for the logging needed by
Oracle GoldenGate. Setting up force logging is optional; you can only set supplemental minimal logging and
add table/schema-level supplemental logging from GGSCI.
 
       SQL> ALTER DATABASE ADD SUPPLEMENTAL LOG DATA;
Optionally, you can enable force logging for the entire database.
      SQL> ALTER DATABASE FORCE LOGGING

After changing the logging option, either FORCE logging or MINIMAL SUPPLEMENTAL LOGGING , you must switch log file.

      SQL> ALTER SYSTEM SWITCH LOGFILE;
      
      
Step 11: Add Extracts

            GGSCI> ADD EXTRACT ETTND001, TRANLOG, BEGIN NOW
            Or execute this
            GGSCI> ADD EXTRACT ETTND001, TRANLOG, BEGIN 2015-11-10 04:03
            
            
            GGSCI> ADD RMTTRAIL /u01/app/ggs/appname/t1, EXTRACT ETTND001, MEGABYTES 60
            
             GGSCI> EDIT PARAMS ETTND001

Add the following entries in the parameter file:
            EXTRACT ETTND001
            USERID TIGER, PASSWORD tiger123_
            RMTHOST node2.ravin-pc.com, MGRPORT 7809
            RMTTRAIL /app/ggs/fox/dirdat/f1
            TABLE TIGER.ORDER_DTL;   
            
            
Step 13: Add the Replicat
        GGSCI> ADD REPLICAT RFDLD001, EXTTRAIL /app/ggs/fox/dirdat/f1, NODBCHECKPOINT
            GGSCI> EDIT PARAMS RFDLD001
 Add the following entries in the parameter file for the replicat:
```
REPLICAT RFDLD001
PURGEOLDEXTRACTS
ASSUMETARGETDEFS
DISCARDFILE /app/ggs/fox/dirrpt/rfdld001.dsc, PURGE, MEGABYTES 599
USERID fox, PASSWORD fox123_
MAP TIGER.ORDER_DTL, TARGET FOX.ORDER_DTL;
 ```
 
 Step 14: Create the Definition File
 
If your source and target table structure and name are different, you need to create a definition file on your
source and transfer it to your target. This definition file is then referred to by the Oracle GoldenGate replicat
process for mapping the source and target tables and applying the replicated transactions.
            
            
 DEFSFILE /app/ggs/tiger/dirdef/rfdld001.def
USERID TIGER, PASSWORD tiger123_
TABLE TIGER.ORDER_DTL;


Run the following command from the OGG home directory /app/ggs/tiger . This will generate the definition file.

defgen paramfile dirprm/temp.prm


Copy /app/ggs/tiger/dirdef/rfdl001.def from the source machine to /app/ggs/fox/dirdef/rfdl001.def on the target machine.

Remove ASSUMETARGETDEFS and add the following to your replicat parameter file:
 SOURCEDEFS /app/ggs/fox/dirdef/rfdld001.def

  Step 15: Enable Supplemental Logging for Oracle GoldenGate

Log in to GGSCI on the source and enable supplemental logging for GoldenGate table/schema. This needs
to be done only on the capture side. Replicat processes do not need supplemental logging.    
      
      
                  GGSCI> DBLOGIN USERID tiger, PASSWORD tiger123_
                  GGSCI> ADD SCHEMATRANDATA tiger ALLCOLS
                  or
                  GGSCI> ADD SCHEMATRANDATA tiger NOSCHEDULINGCOLS      
      
for only specific table
      
      GGSCI> ADD TRANDATA tiger.order_dtl
      
 Step 16: Initial Data Synchronization
All the existing source data of tables to be replicated needs to be copied to the target database in order for
any replication to succeed. There is more than one way that data copying can be done. The copy method
used is dependent on the volume of data in the source database that needs to be copied over. 

Setting Up the Initial Extract Process on Source

initial load extract process by executing the following command. Here, SOURCEISTABLE informs
Oracle GoldenGate that the extract process is the initial load extract and the entire table


      GGSCI> ADD EXTRACT INITEXT1, SOURCEISTABLE

Edit the extract parameter file.
##### GGSCI> EDIT PARAMS INITEXT1
            EXTRACT INITEXT1
            RMTHOST node2.ravin-pc.com, MGRPORT 7809
            RMTTASK REPLICAT, GROUP INITREP1
            USERID tiger, PASSWORD tiger123_
            TABLE TIGER.ORDER_DTL;

Setting Up the Initial Replicat Process on the Target

initial load replicat on the target machine’s GoldenGate instance, SPECIALRUN informs GoldenGate
that the replicat process is the initial load replicat and will process trails received from an initial load extract

      GGSCI> ADD REPLICAT INITREP1, SPECIALRUN

##### GGSCI> EDIT PARAMS INITREP1
    
      REPLICAT INITREP1
      ASSUMETARGETDEFS
      DISCARDFILE /app/ggs/fox/dirrpt/initrep1.dsc, MEGABYTES 599, append
      USERID FOX, PASSWORD fox123_
      MAP TIGER.ORDER_DTL, TARGET FOX.ORDER_DTL;

Silent Installation
-----------------------

Before version 12. x of Oracle GoldenGate, there was the option to simply uncompress into the directory
where you want to install GoldenGate. OUI replaced this with a GUI installer that does a couple of
background pre- and post-setups to simply the overall installation.


This installation method will require you to configure a response file first. Once you unzip the
compressed installer binaries, go to the response directory to find the response file.

[oracle@ravin fox]$ unzip ./121200_fbo_ggs_Linux_x64_shiphome.zip –d ggate
[oracle@ravin fox]$ cd /app/ggs/fox/fbo_ggs_Linux_x64_shiphome/Disk1/response


The response file name provided with the installer is oggcore.rsp .

INSTALL_OPTION=
ORA12c or ORA11g

SOFTWARE_LOCATION=
Where to install the software

START_MANAGER=
TRUE or FALSE

MANAGER_PORT=
Any port number, default 7809

DATABASE_LOCATION=
Set to $ORACLE_HOME

INVENTORY_LOCATION=
Specify location for oraInventory

UNIX_GROUP_NAME=
Group that should own the installation of Golden Gate


../runInstaller -silent -responseFile /app/ggs/fox/fbo_ggs_Linux_x64_shiphome/Disk1/response/oggcore.rsp


Handling Character Set
----------

Oracle GoldenGate provides globalization support, which means data can be processed in its own native language.

Before discussing in detail how Oracle GoldenGate preserves character sets when out-of-sync source
and target database character sets are different,
which lists some of the Oracle
character sets. There are about 200 Oracle character sets currently supported by Oracle GoldenGate.


Using CHARSET
By default, the parameter files of Oracle GoldenGate are created using the character set of the operating
system. If you need to use a different character set to support characters not supported by the operating
system character set, you can specify the CHARSET parameter in your EXTRACT , REPLICAT , MANAGER , DEFGEN ,
and GLOBALS parameter files

CHARSET character_set_name


Using Escape Sequences
--
To use a character in your parameter file that is not supported by your operating system character set, you
can use an escape sequence in this format: \<escape sequence type>

• Unicode escape sequence : \uFFFF
• Octal escape sequence : \377
• Hexadecimal escape sequence : \xFF

TABLE TIGER."\u3000XYZ";


Using NLS_LANG
You can also use the NLS_LANG parameter in your extract or replicat parameter file to take care of the
character set conversion.
setenv (NLS_LANG="AMERICAN_AMERICA.AL32UTF8")


CHAPTER 5 Classic vs. Integrated Capture and Apply
-----------------

the role of the capture and delivery processes in Oracle GoldenGate replication. 
The capture process in Oracle GoldenGate is called extract , and the apply process is called replicat .

Until OGG version 11 you had only the classic capture and delivery modes. from 11.2 introduced an optional and efficient processing mode, namely, integrated capture. Later OGG 12 introduced integrated apply as well.

Integrated refers to the processing capability being integrated with database features. This is native to Oracle database, so if you are using any non-
Oracle database, then you will not be able to use integrated capture and apply.

![image](https://user-images.githubusercontent.com/108070848/223398180-d429b88f-ceca-4a54-8d9b-19437c9e70a3.png)


Classic Capture
-------

In the classic capture mode, data changes are captured from the Oracle redo logs/archive logs. This is
the initial capture mode developed and used by GoldenGate Software Inc. The classic capture process
is supported for all databases that are supported by Oracle GoldenGate


![image](https://user-images.githubusercontent.com/108070848/223398428-4916f8f5-12f3-4fa8-86d6-57f7d787f5b6.png)

Integrated Capture
--------
This capture mode is specific to Oracle Database 11.2 onward. In the integrated capture mode, the extract
process communicates with the database log mining server and receives information in the form of a logical
change record (LCR). The database log mining server mines redo log and captures changes in the form of an
LCR.


![image](https://user-images.githubusercontent.com/108070848/223398621-6ade76b6-a785-4655-a576-1386d3008c4a.png)


Integrated capture was recently introduced and is a more efficient mode of data capture.
Let’s discuss a few benefits of integrated capture mode compared to classic capture mode, as listed here:
• It supports more Oracle data types compared to classic capture mode.
• Interaction with the database log mining server allows you to switch automatically between copies of archived logs and mirror images of redo logs.
  This is useful in the case of disk block corruption of the archived/redo logs.
• It supports a multitenant container database containing multiple pluggable databases. This is not possible with classic capture.
• It has easy configuration for Oracle RAC and ASM.
• It requires Oracle Database 11.2.0.3 or higher.
• It requires more memory, and hence you need to increase the size of MEMORY_TARGET and STREAMS_POOL .


Integrated Capture Modes
Integrated capture supports two types of configuration:
• On-source capture : The capture process runs on the actual source database server.
Changes will be captured locally and routed to the target in real time.


• Downstream capture : The capture process runs on a remote database server. The Log
Writer (LGWR) or Archiver (ARCH) process is configured on the primary database,
and redo data is transferred to the standby database server. When using the Archiver
process, the redo data is archived whenever a log switch happens on the primary
server, whereas LGWR writes redo data to standby redo logs on the downstream server.
The changes are then mined from the standby redo logs on the downstream server.




Nonintegrated Apply
The replicat process makes use of standard SQL to apply DML or DDL changes to the target system. A
change is read from the trail, data conversion or filtering is applied, and a SQL statement is constructed that
is then applied on the target database.


![image](https://user-images.githubusercontent.com/108070848/223399773-f956c8f1-2ee6-4814-b8b2-58845b1b896a.png)





Integrated Apply
In this configuration, the Oracle internal apply process is used by the replicat. A change is read from the
trail, and the data conversion and filtering takes place. The apply process then constructs an LCR for the
DML change. The LCR is then applied to the target database by the inbound server. This mode makes use of
parallel apply while keeping intact the atomicity of the transaction. It thereby has higher/faster throughput.


let’s look at the advantages of using integrated apply over classic apply.
• The apply processes can be configured with the parameters PARALLELISM and
MAX_PARALLELISM to define the degree of parallelism. This allows the apply processes
to work in parallel for applying multiple transactions concurrently during heavy
workloads.
• Integrated apply is easier to configure when compared to classic apply.
• It supports pluggable databases.


Implementing Classic and Integrated Captures
-----------

To create a classic capture process named ETTND001 , issue the following command at the GGSCI prompt:
      GGSCI> ADD EXTRACT ETTND001, TRANLOG, BEGIN NOW
      
 assign a local trail to this extract.
      GGSCI> ADD EXTTRAIL /app/ggs/tiger/dirdat/t1, EXTRACT ETTND001

You can create an intermediate data pump called PFTND001 to read these local trails.
      GGSCI> ADD EXTRACT PFTXD001, EXTTRAILSOURCE /app/ggs/tiger/dirdat/t1     
      
      
 Creating an On-Source Integrated Capture
To create an integrated capture process, you need to specify INTEGRATED TRANLOG along with the ADD EXTRACT command.
      GGSCI> ADD EXTRACT ETTND001 INTEGRATED TRANLOG, BEGIN NOW
Then in the extract parameter file, you need to use the TRANLOGOPTIONS INTEGRATEDPARAMS parameter.
      TRANLOGOPTIONS INTEGRATEDPARAMS (max_sga_size 200, parallelism 2)     
      
 Here’s the parameter file for an integrated extract ETTND001 when the source database is the mining database.
            GGSCI> EDIT PARAMS ETTND001
            EXTRACT ETTND001
            USERID tiger, PASSWORD tiger123_
            LOGALLSUPCOLS
            UPDATERECORDFORMAT COMPACT
            ENCRYPTTRAIL AES192
            TRANLOGOPTIONS INTEGRATEDPARAMS (max_sga_size 200, parallelism 2)
            EXTTRAIL /app/ggs/tiger/dirdat/t1
            TABLE TIGER.*;

And here’s the corresponding data pump parameter file pftnd001.prm :
      GGSCI> EDIT PARAMS PFTND001
      EXTRACT PFTND001
      USERID tiger, PASSWORD tiger123_
      RMTHOST node2.ravin-pc.com, MGRPORT 7809 ENCRYPT AES192, KEYNAME mykey1
      RMTTRAIL /app/ggs/fox/dirdat/f1
      PASSTHRU
      TABLE TIGER.*;     


Creating an Integrated Capture Using a Downstream Mining Database

For integrated capture using downstream mining, the downstream database must be running in ARCHIVELOG
mode. Also, you need to set up standby redo log files, which receive redo logs from online redo log files on
the source database.
      
Add the extract integrated extract process on the mining database server.

GGSCI> ADD EXTRACT ETTND001 INTEGRATED TRANLOG BEGIN NOW
EXTRACT added.

GGSCI> ADD EXTTRAIL /app/ggs/tiger/dirdat/t1, EXTRACT ETTND001
EXTTRAIL added.


Log into the mining database to register the extract as follows:
      GGSCI> DBLOGIN USERID tiger@orcl1 PASSWORD tiger123_
Successfully logged into database.
      GGSCI> MININGDBLOGIN USERID tiger, PASSWORD tiger123_
Successfully logged into mining database.
      GGSCI> REGISTER EXTRACT ETTND001 DATABASE      
      
      
Add the following parameters to your extract and data pump processes’ parameter files.
      GGSCI> EDIT PARAMS ETTND001
      EXTRACT ETTND001
      USERID tiger, PASSWORD tiger123_
      TRANLOGOPTIONS MININGUSER tiger@orcl2 MININGPASSWORD tiger123_
      TRANLOGOPTIONS INTEGRATEDPARAMS (downstream_real_time_mine Y)
      EXTTRAIL /app/ggs/tiger/dirdat/t1
      TABLE TIGER.*;

The data pump parameter file configuration remains essentially the same as classic mode.
      GGSCI> EDIT PARAMS PFTND001
      EXTRACT PFTND001
      USERID tiger, PASSWORD tiger123_
      RMTHOST node2.ravin-pc.com, MGRPORT 7809 ENCRYPT AES192, KEYNAME mykey1
      RMTTRAIL /app/ggs/fox/dirdat/f1
      PASSTHRU
      TABLE TIGER.*;      

      
If you are using an Oracle 12 c multitenant database, your extract and data pump parameter file will have the following configuration:
      EXTRACT ETTND001
      USERIDALIAS tiger1
      TRANLOGOPTIONS MININGUSERALIAS tiger2
      TRANLOGOPTIONS INTEGRATEDPARAMS (MAX_SGA_SIZE 164, &
      DOWNSTREAM_REAL_TIME_MINE y)
      LOGALLSUPCOLS
      UPDATERECORDFORMAT COMPACT
      ENCRYPTTRAIL AES192
      EXTTRAIL /app/ggs/tiger/dirdat/t1
      SOURCECATALOG pdb1
      TABLE TIGER1.*;
      SOURCECATALOG pdb2
      TABLE TIGER2.*;

Here is the data pump parameter configuration for a multitenant database:
      EXTRACT PFTND001
      USERIDALIAS tiger
      RMTHOST node2.ravin-pc.com, MGRPORT 7809 ENCRYPT AES192, KEYNAME mykey1
      RMTTRAIL /app/ggs/fox/dirdat/f1
      SOURCECATALOG pdb1
      TABLE TIGER1.*;
      SOURCECATALOG pdb2
      TABLE TIGER2.*;      



Monitoring an Integrated Capture
----------

##### 1

      col CAPTURE_NAME for a20;
      col QUEUE_NAME for a15;
      col START_SCN for 9999999999;
      col STATUS for a10;
      col CAPTURED_SCN for 9999999999;
      col APPLIED_SCN for 9999999999;
      col SOURCE_DATABASE for a10;
      col LOGMINER_ID for 9999999;
      col REQUIRED_CHECKPOINTSCN for a30;
      col STATUS_CHANGE_TIME for a15;
      col ERROR_NUMBER for a15;
      col ERROR_MESSAGE for a10;
      col CAPTURE_TYPE for a10;
      col START_TIME for a30
      SELECT CAPTURE_NAME, QUEUE_NAME, START_SCN, STATUS,
      CAPTURED_SCN, APPLIED_SCN, SOURCE_DATABASE,
      LOGMINER_ID, REQUIRED_CHECKPOINT_SCN,
      STATUS_CHANGE_TIME, ERROR_NUMBER, ERROR_MESSAGE,
      CAPTURE_TYPE, START_TIME
      FROM DBA_CAPTURE;

You can also query the dynamic statistics from the GoldenGate views in the database.
      col state for a30;
      SELECT sid, serial#, capture#, CAPTURE_NAME, STARTUP_TIME, CAPTURE_TIME,
      state, SGA_USED, BYTES_OF_REDO_MINED,
      to_char(STATE_CHANGED_TIME, 'mm-dd-yy hh24:mi') STATE_CHANGED_TIME
      FROM V$GOLDENGATE_CAPTURE


The following query gives additional details about the capture message’s create time and its number:
      col capture_message_create_time for a30;
      col enqueue_message_create_time for a27;
      col available_message_create_time for a30;
      SELECT capture_name,
      to_char(capture_time, 'mm-dd-yy hh24:mi') capture_time,
      capture_message_number,
      to_char(capture_message_create_time ,'mm-dd-yy hh24:mi') capture_message_create_time,
      to_char(enqueue_time,'mm-dd-yy hh24:mi') enqueue_time,
      enqueue_message_number to_char(enqueue_message_create_time, 'mm-dd-yy hh24:mi') enqueue_message_create_time,
      available_message_number,
      to_char(available_message_create_time,'mm-dd-yy hh24:mi') available_message_create_time
      FROM GV$GOLDENGATE_CAPTURE;


LOGALLSUPCOLS tells the extract to capture a before image for all supplemental log columns for the
update and delete operations. By default before and after images are captured in a separate record, which
incurs processing overhead and disk I/O for both capture and apply processes, and also the overall trail files
size is larger.

Let’s take a look at how to add integrated replicat RFDLD001 .
      GGSCI> DBLOGIN USERID fox@orcl2, PASSWORD fox123_
Successfully logged into database.
Add replicat RFDLD001 with the INTEGRATED option.
      GGSCI> ADD REPLICAT RFDLD001 INTEGRATED EXTTRAIL /app/ggs/fox/dirdat/f1
REPLICAT (Integrated) added.
Configure the replicat parameter file to contain the following parameter:

GGSCI> edit params RFDLD001
      REPLICAT RFDLD001
      SETENV (ORACLE_SID='orcl3')
      DBOPTIONS INTEGRATEDPARAMS(parallelism 6)
      USERID fox@orcl3, PASSWORD fox123_
      ASSUMETARGETDEFS
      MAP TIGER. *, TARGET FOX. *;

Start the newly added replicat and run INFO on it.
      GGSCI> info replicat RFDLD001
      
 SQL> select REPLICAT_NAME,SERVER_NAME from DBA_GOLDENGATE_INBOUND;
SQL> select APPLY_NAME,QUEUE_NAME,status from dba_apply;
SQL> select apply_ame,state from V$GG_APPLY_COORDINATOR ;

In this example, we have set parallelism to 6 for the replicat, which means there will be six apply
processes that you can query from the database, as shown here:
SQL> select server_id,TOTAL_MESSAGES_APPLIED from V$GG_APPLY_SERVER where apply_name='OGG$RFDLD001';     
      
      
Coordinated Replicat
----------
The integrated capture and delivery processes are limited only to Oracle databases. With an Oracle
GoldenGate 12 c release, a new delivery process called coordinated replicat was introduced. This type of
replicat is multithreaded. They can read multiple trails independently and apply transactions in parallel

      
 In Oracle GoldenGate 12 c , a single replicat parameter file is created, and additional replicat groups
are added automatically with a coordinator process assigning workloads to individual replicat groups. This
partitioning is done using the THREADRANGE parameter, as in the following example:

      MAP TIGER.TABLEA, TARGET FOX.TABLEA, THREADRANGE (1-3, WORKID));

use either classic or integrated extract groups on the source that delivers trails to the target
with the coordinated replicat. The replicat you configure is called coordinator , and its name is limited to
five characters.


Add a coordinated replicat as shown next. Please note here the replicat group name is only five
characters; remaining characters are automatically assigned by the coordinated replicat process.
      GGSCI> add replicat RFDLD, coordinated, EXTTRAIL /app/ggs/fox/dirdat/f1, maxthreads 5
REPLICAT (Coordinated) added.
      
 
GGSCI> view params RFDLD
REPLICAT RFDLD
USERIDALIAS fox
ASSUMETARGETDEFS
MAP TIGER.TABLEA, TARGET FOX.TABLEA, THREADRANGE (1-5, WORKID));



CHAPTER 6 Capturing DDL Changes
----------------------

Oracle GoldenGate supports replication of DDL statements from one database to another database.
Currently, DDL replication is supported only for Oracle databases



What Is DDL Replication?
A change in the structure of an object or creating new object in an Oracle database is called Data Definition
Language (DDL). Oracle GoldenGate supports DDL on the following objects of Oracle databases:

• Clusters            • Functions
• Indexes             • Materialized views
• Packages            • Procedures
• Roles               • Sequences
• Synonyms            • Tables
• Tablespaces         • Triggers
• Types              • Users            • Views


Types of DDL Replication
-------
There are two types of DDL Replication supported by Oracle GoldenGate as listed the following:
• Trigger-based or classic DDL replication : This is the classic DDL capture method
supported for Oracle database versions earlier than 11.2.0.4. It requires you to install
triggers and supporting objects for capturing and applying DDL changes.
• Triggerless or native DDL replication : The triggerless, also called native, DDL
replication was introduced with Oracle Database 11.2.0.4. This type of replication
uses the database log mining server for capturing and applying DDL changes.

Limitations with DDL Replication
DDL replication is slightly trickier when compared to replicating data. Before setting up DDL replication
between two systems, you must be aware of the limitations with DDL replication.


• The maximum length of a DDL statement to be replicated is between 2 MB to 4 MB.
If the DDL length exceeds this size, the extract process will issue a warning message
and ignore the DDL statement. These ignored DDL statements will be stored in the
marker table.

• The source and target database objects on which the DDL replication will happen
should be identical.

• DDL replication is not supported on standby databases.
• DDL replication can be mapped to different object names only by the primary
extract process. Data pumps support DDL replication in as it is PASSTHRU mode.
• A DML/DDL operation within a DDL trigger is not captured.
• It is mandatory to use ASSUMETARGETDEFS instead of SOURCEDEFS in the replicat
configured for DDL replication.



DDL Scope
The DDL scope defines how a DDL operation is handled by Oracle GoldenGate. There are three DDL scopes
in which you can classify DDL operations to be replicated. These DDL scopes are as follows:

• Mapped : Objects are specified in the TABLE and MAP statements in the extract/replicat
process. Both DDL and DML changes are applicable using the instructions in the
TABLE and MAP statements.



Unmapped : The object name is not included in TABLE and MAP statements in the extract/replicat
process. Only DDL changes are replicated. DDL statements are applied to the same schema name as on
the source. The replicat automatically switches from the current schema to the source schema and then
after applying the DDL, it switches back to the current schema.
Here’s an example:

CREATE TABLE NEW_TABLE1
(
ID NUMBER,
DESCRIPTION VARCHAR2(30)
);


• Other : The object is not mapped to the MAPPED or UNMAPPED scope that comes under
this scope, such as CREATE USER , ALTER TABLESPACE , and so on. DDLs are applied at
the target with the same schema and object names as on the source.


![image](https://user-images.githubusercontent.com/108070848/223689237-01c41eae-bad1-40ae-b00f-bc81505f2ce6.png)


To set up your DDL replication, you must install DDL objects as follows:
1. Choose a schema (for example GGSUSER ) that will contain the GoldenGate DDL
objects.
2. Grant execute privileges on the utl_file package to the GoldenGate user. This
gives the GoldenGate user access to the operating system files in the UTL_FILE
directory.
      GRANT EXECUTE ON utl_file TO GGSUSER;

3. Set up a default tablespace for the previous schema you created ( GGSUSER ).
Make sure that this tablespace is solely used by the previous DDL schema and
no other objects are created in it. It is a good idea to keep AUTOEXTEND ON for this
tablespace as the DDL history and marker table may grow with time.
4. Create or edit the GLOBALS parameter file. You will need to specify the schema_name in the GLOBALS file.

      EDIT PARAMS ./GLOBALS
      GGSCHEMA ggsuser

5. To recognize Oracle invisible indexes for DDL replication, set al low_invisible_index_keys to TRUE in the params.sql file.
6. define allow_invisible_index_keys = 'TRUE'
7. Save and close the globals and params files and exit all Oracle sessions to proceed to the next step.
8. You now need to run some SQL files to set up your DDL replication environment. You should be logged in as the SYSDBA user for running these SQL files. These
SQL files are present in the GoldenGate installation directory where all the OGG software binaries are extracted during installation.


Execute the marker_setup.sql file. This will prompt for the Oracle GoldenGate schema. Provide GGSUSER when prompted.
      SQL>@marker_setup.sql

Next, execute the ddl_setup.sql file. This will prompt for the DDL schema. This will fail if the
tablespace you specified for this schema is shared by any other user.

SQL>@ddl_setup.sql

Set up the role by executing the role_setup.sql file. This will prompt for the DDL schema. This takes care of the role setup required for DDL synchronization.
`     SQL>@role_setup.sql
Use GRANT role (the default is GGS_GGSUSER_ROLE ) for the Oracle extract users.
      SQL>GRANT role TO ggsuser;
Enable the DDL trigger.

      SQL>@ddl_enable.sql

Optionally, to improve the performance of the DDL trigger, the script pins the PL/SQL package being
used by the trigger into the memory.

      SQL>@ddl_pin DDL_user

9. To replicate DDL operations on any new table, you can use wildcards in the
parameter files as follows:
• In the TABLE statement of the extract parameter file:
TABLE source_schema.*;
• In the MAP and TARGET statements of the replicat parameter file:
MAP source_schema.TAB*. TARGET target_schema.HIST_*;




Execute ddl_pin.sql , which pins DDL tracing, the DDL package, and the DDL trigger for performance improvements.
SQL> @ddl_pin.sql TIGER



Now, you can configure the parameter files for the extract process for DDL synchronization. Add the following entry to your extract process:
      DDL INCLUDE MAPPED
      
the parameters for the extract process ( ETTND001 ):
      
      EXTRACT ETTND001
            USERID tiger, PASSWORD tiger123_
            EXTTRAIL /app/ggs/tiger/dirdat/t1
            DDL INCLUDE ALL
            TABLE tiger.t*;     
   
the parameters for the data pump process ( PFTND001 ):
      
      EXTRACT PFTND001
      USERID tiger, PASSWORD tiger123_
      RMTHOST node2.ravin-pc.com, MGRPORT 7809
      RMTTRAIL /app/ggs/fox/dirdat/f1
      DDL INCLUDE ALL
      TABLE tiger.t*;
      
parameters for the replicat process ( RFDLD001 ):
      REPLICAT RFDLD001  
      USERID fox, PASSWORD fox123_
      ASSUMETARGETDEFS
      DISCARDFILE /app/ggs/fox/dirrpt/rfdld001.dsc, PURGE
      DDL INCLUDE ALL
      DDLERROR DEFAULT IGNORE
      MAP tiger.*, TARGET fox.*;
      
DDL Capture in Integrated Capture Mode
------------

The integrated capture and apply processes are exclusive to Oracle Database since they use the Oracle log
mining server for replication. If you have an integrated capture on an Oracle Database 11.2.0.4 or later, you
can configure DDL replication through the log mining server.     
      

Here’s an example of excluding some specific DDL statements from replication.
Exclude any DDL statement from the SYS user, as follows:
if ora_owner='SYS' then
retVal:='EXCLUDE';
end if;
Exclude DROP USER statements, as follows:
if ora_objtype='USER' and ora_optype ='DROP' then
retVal:='EXCLUDE';
end if;
Exclude DDL on TEMP% tables, as follows:
if ora_owner='TIGER' and ora_name like 'TEMP%' then
retVal:='EXCLUDE';
end if;



Selective DDL Replication Using the DDL Parameter
----------

DDL parameter with the INCLUDE and EXCLUDE option in the capture parameter. Only one DDL
parameter can be used in a parameter file. Please note that the DDL option can be used only in the primary
extract and not in a data pump extract.


DDL INCLUDE . Also, DDL EXCLUDE ALL does not require INCLUDE with it.
Here are some examples of DDL filters:
DDL INCLUDE ALL, EXCLUDE OBJNAME TIGER.*
DDL INCLUDE OBJNAME TIGER.* EXCLUDE OBJNAME TIGER.CNTRY
DDL INCLUDE OBJNAME TIGER.* ALLOWEMPTYOBJECT
DDL INCLUDE OBJNAME orcl.TIGER.* ALLOWEMPTYOWNER
DDL INCLUDE OBJNAME tiger.*
DDL INCLUDE OBJNAME tiger."cntry"
DDL INCLUDE OBJTYPE 'INDEX'
DDL INCLUDE OBJTYPE 'SNAPSHOT'
DDL INCLUDE OPTYPE ALTER
DDL INCLUDE ALL EXCLUDE INSTR 'CREATE INDEX'
DDL INCLUDE ALL EXCLUDE INSTRCOMMENTS 'NOT REPLICATED'

CHAPTER 7 ■ PERFORMING THE INITIAL LOAD
--------


|Parameter       |  Used In             |     Description   |
|SOURCEISTABLE   |   Extract            |     The extract is an initial load extract that extracts directly from the source table.|
|SPECIALRUN      |   Replicat           |     The replicat is a one-time run replicat that runs without using checkpoints.|
|BULKLOAD        |   Replicat           |     The replicat will directly interface with the Oracle SQLLOADER utility on the target to load data into the target tables.|
|GENLOAD         |   Replicat          |     This generates run and control files for the specified database utility.|
|RMTFILE         | Extract             |    This specifies the extract file name.
|FORMATASCII     |  Extract            |     This instructs the extract to write output in ASCII text in flat files. These can be used by the database utility on the                                           target machine to load data
                                             directly without setting up the replicat process.|
|SQLLOADER       |   Extract           |     This is used along with the FORMATASCII parameter to extract data into ASCII-format flat files.



Initial Load Using the Database Utility

replicat process should have the HANDLECOLLSION parameter to handle errors after the initial load.
Turn off HANDLECOLLISION once pending transactions from the extract have flown to the replicat.

remove the parameter from the replicat parameter file and bounce the
replicat or issue the following command in 

GGSCI. SEND REPLICAT RFDLD001 , NOHANDLECOLLISIONS

Initial Load Using SQLLOADER
---------
initial load using SQLLOADER is to capture data from the source database using the
initial load extract process into external ASCII-format flat files.


![image](https://user-images.githubusercontent.com/108070848/227124628-dfce18a6-bfe3-4868-95f2-c4a1fb298759.png)


1.Create an initial load extract on the source machine.
      GGSCI> ADD EXTRACT INITEXT1, SOURCEISTABLE
2.Configure the extract parameter file to have the following parameters:

GGSCI> EDIT PARAMS INITEXT1

            SOURCEISTABLE
            SETENV (NLS_LANG = "AMERICAN_AMERICA.AL32UTF8")
            userid tiger, password tiger123_
            FORMATASCII, SQLLOADER
            RMTHOST node2-ravinpc, MGRPORT 7809
            RMTFILE /app/ggs/tiger/dirdat/load_cntry.dat PURGE
            TABLE tiger.cntry;
            
            
 Create the initial load replicat on the target machine. This replicat only generates control and run files
to be used by the database utility for loading data.

GGSCI> ADD REPLICAT INITREP1, SPECIALRUN
      Configure the replicat parameter file.
GGSCI> EDIT PARAMS INITREP1

            SPECIALRUN
            END RUNTIME
            GENLOADFILES sqlldr.tpl
            userid fox, password fox123_
            extfile /app/ggs/fox/dirdat/load_cntry.dat
            assumetargetdefs
            MAP TIGER.CNTRY, TARGET FOX.CNTRY;
            
  GETLOADFILES specifies the name of the template that generates the control and run file
  
$ GGSCI> START EXTRACT ETLDT0001

report file to see whether the extraction has completed. The report file should have
similar to the following information indicating your flat file for the load has been extracted.

$ / app/ggs/tiger /extract paramfile dirprm/ initext1 .prm reportfile initext1.rpt
            


Initial Load Using the Direct Load Method
--------

initial load, special extract and replicat processes are created. The initial load extract
captures all of the source records and is sent to the initial load replicat task. The initial load replicat task is
dynamically started by the manager process



![image](https://user-images.githubusercontent.com/108070848/227127916-b5ad55bd-c3b9-401c-b7cc-cf926fb63dd6.png)


Let’s start with creating an initial load extract named INITEXT1 .
GGSCI> ADD EXTRACT INITEXT1, SOURCEISTABLE
GGSCI> EDIT PARAMS INITEXT1
      EXTRACT INITEXT1
      SOURCEISTABLE
      RMTHOST ravin-ravinpc, MGRPORT 7809
      RMTTASK REPLICAT, GROUP INITREP1
      USERID tiger, PASSWORD tiger123_
      TABLE TIGER.*;
Save and close the parameter file. Now, create an initial load replicat called INITREP1 on the target.

GGSCI> ADD REPLICAT INITREP1, SPECIALRUN
GGSCI> EDIT PARAMS INITREP1

      REPLICAT INITREP1
      --ASSUMETARGETDEFS
      SOURCEDEFS /app/ggs/fox/dirdef/INITREP1.def
      DISCARDFILE /app/ggs/fox/dirrpt/INITREP1.dsc, MEGABYTES 599, append
      USERID fox, PASSWORD fox123_
      MAP TIGER.*, TARGET FOX.*;
      
      
  Save and close the parameter file.
First start your regular extract process and then start your initial load extract process.

$ GGSCI> START EXTRACT ETLDT0001
$ / app/ggs/tiger /extract paramfile dirprm/ initext1 .prm reportfile initext1.rpt    


Once the initial load is complete, start your regular replicat processes that will load changes
captured during and after the initial load.
GGSCI> START REPLICAT RFDLD001
GGSCI> SEND REPLICAT RFDLD001 , NOHANDLECOLLISIONS


Initial Load Using BULKLOAD to sqlloader
------


initial load extract sends data to the initial load replicat. The replicat task then interfaces
with the sqlloader API to bulk-load data in the target Oracle database. Figure 7-3 shows the components of
Oracle GoldenGate when using the direct bulk load to sqlloader method for initial load.



GGSCI> ADD EXTRACT INITEXT1, SOURCEISTABLE
GGSCI> EDIT PARAMS INITEXT1
EXTRACT INITEXT1
RMTHOST node2-ravinpc, MGRPORT 7809
RMTTASK REPLICAT, GROUP INITREP1
USERID tiger, PASSWORD tiger123_
TABLE TIGER.*;
Create an initial load replicat called INITREP1 on the target as shown here:
GGSCI> ADD REPLICAT INITREP1, SPECIALRUN
GGSCI> EDIT PARAMS INITREP1
REPLICAT INITREP1
BULKLOAD
--ASSUMETARGETDEFS
SOURCEDEFS /app/ggs/fox/dirdef/INITREP1.def
DISCARDFILE /app/ggs/fox/dirrpt/INITREP1.dsc, MEGABYTES 599, append
USERID fox, PASSWORD fox123_
MAP TIGER.*, TARGET FOX.*;
Follow the similar process

Follow the similar process explained for the direct load method. Start the initial load extract named
INITEXT1 and let it complete.
$ / app/ggs/tiger /extract paramfile dirprm/ initext1 .prm reportfile initext1.rpt
Verify the report file to see whether the extraction has completed. Start the replicat process and verify
the load after it completes. You can send the INFO command on the replicat INITREP1 to see the progress.
GGSCI> START REPLICAT RFDLD001
GGSCI> SEND REPLICAT RFDLD001 , NOHANDLECOLLISIONS



Initial Load Example
-----------

example of performing the initial load on Oracle Database 12 c using integrated capture
and apply. In this example, you will perform the initial load from the TIGER schema on the orcl1 database to
the FOX schema on the orcl2 database using the direct load method.


Execute the following scripts on the FOX schema to disable table constraints.
--disable foreign key and check constraints before initial load
BEGIN
FOR c IN
(SELECT c.owner, c.table_name, c.constraint_name
FROM user_constraints c, user_tables t
WHERE t.table_name in (‘table_name1’,’table_name2’,’table_name3’)
AND c.table_name = t.table_name
AND c.constraint_type!='P'
AND c.status = 'ENABLED'
ORDER BY c.constraint_type DESC)
LOOP
dbms_utility.exec_ddl_statement('alter table "' || c.owner || '"."' || c.table_name ||
'" disable constraint ' || c.constraint_name);
END LOOP;
END;
/


Next, truncate tables from the FOX schema on the orcl2 database. If you are replicating only specific tables, you should truncate only those tables.
set serveroutput on size 1000000
spool truncate_wseprod_uat_20110914.log
BEGIN
FOR rec IN (select 'truncate '|| object_type || ' ' || object_name AS drop_sql
FROM user_objects WHERE object_type IN ('TABLE')
LOOP
DBMS_OUTPUT.PUT_LINE(rec.drop_sql);
EXECUTE IMMEDIATE(rec.drop_sql);
END LOOP;
END;
/


Add supplemental logging for tables to be replicated on the source. For this example, I have only the ORDER_DTL table in the TIGER schema.

GGSCI> DBLOGIN USERID tiger@orcl1 PASSWORD tiger123_
Successfully logged into database.

GGSCI> ADD TRANDATA TIGER.ORDER_DTL
Logging of supplemental redo data enabled for table TIGER.ORDER_DTL.
TRANDATA for scheduling columns has been added on table 'TIGER.ORDER_DTL'.

Add the extract on the source:

GGSCI> ADD EXTRACT ETTND001, integrated tranlog, begin now
GGSCI> add exttrail /app/ggs/tiger/dirdat/t1, extract ETTND001, megabytes 5
Add the following entries in the parameter file.

EXTRACT ETTND001
USERID TIGER, PASSWORD tiger123_
EXTTRAIL /app/ggs/tiger/dirdat/t1
LOGALLSUPCOLS
UPDATERECORDFORMAT compact
TABLE TIGER.ORDER_DTL;


Log in to the GoldenGate user from GGSCI and register the extract with the database.
GGSCI> DBLOGIN USERID tiger@orcl1 PASSWORD tiger123_
GGSCI> REGISTER EXTRACT ETTND001 DATABASE


Add the data pump to the pump trail files from the target to the fox GoldenGate instances.
GGSCI> add extract DTTND001, exttrailsource /app/ggs/tiger/dirdat/t1
GGSCI> add rmttrail /app/ggs/fox/dirdat/f1, extract DTTND001, megabytes 5


GGSCI> edit params DTTND001
EXTRACT DTTND001
PASSTHRU
RMTHOST node2-ravinpc, MGRPORT 7840
RMTTRAIL /app/ggs/fox/dirdat/f1
TABLE TIGER.ORDER_DTL;
Start the extract and data pump.
GGSCI> start extract *
Create a replicat group on the target machine’s FOX OGG instance.
GGSCI> edit params RFDLD001

REPLICAT RFDLD001
ASSUMETARGETDEFS
DISCARDFILE /app/ggs/fox/dirrpt/rfdld001.dsc, purge
USERIDALIAS DB2 domain admin
MAP hr.*, TARGET hr.*;
GGSCI> add replicat RFDLD001, integrated, exttrail /app/ggs/fox/dirdat/f1
Get the current SCN of the source database.


SQL> select current_scn from v$database;
CURRENT_SCN
-----------
1642141


set up your regular extract, data pump, and replicat processes for capturing and applying change, set up the initial load extract called INITEXT1 and the initial load replicat called INITREP1 .
      


GGSCI> edit params INITEXT1
EXTRACT INITEXT1
SOURCEISTABLE
USERID tiger@orcl1 PASSWORD tiger123_
RMTHOST node2-ravinpc, MGRPORT 7809
RMTFILE /app/ggs/fox/dirdat/initld, MEGABYTES 2, PURGE
TABLE TIGER.*, SQLPREDICATE 'AS OF SCN 1642141';
TABLEEXCLUDE TIGER.RAVIN_ORDERS;
Here, TABLEEXCLUDE will inform OGG not to capture the table RAVIN_ORDERS .
Next, create and start the INITEXT1 extract channel.
GGSCI> add extract INITEXT1, sourceistable
GGSCI> start extract INITEXT1
Sending START request to MANAGER …
EXTRACT INITLOAD starting


GGSCI> add replicat INITREP1, specialrun
REPLICAT INITREP1
USERID fox@orcl1 PASSWORD fox123_
SPECIALRUN
END RUNTIME
ASSUMETARGETDEFS
EXTFILE /app/ggs/fox/dirdat/initld
MAP TIGER.*, TARGET FOX.*;
Start the initial load replicat.

GGSCI> start replicat INITREP1

GGSCI> start replicat RFDLD001, aftercsn 1642141
