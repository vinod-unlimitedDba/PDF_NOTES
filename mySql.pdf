
MySQL Database Administration
 1 
MySQL DBA
1. Introduction…………................................................................................................................................................3
1.1. Overview of MySQL..............................................................................................................................................3
1.2. History of MySQL..................................................................................................................................................3
1.3. The Main Features of MySQL...............................................................................................................................3
1.4. Architecture...........................................................................................................................................................4
2. MySQL Installation..................................................................................................................................................7
2.1. Installing MySQL from RPM Packages on Linux...................................................................................................7
2.2. Installing MySQL from a Source Distribution.........................................................................................................7
2.3. Installing MySQL from Generic Binaries...............................................................................................................8
2.4. Setting Environment Variables.............................................................................................................................9
3. MySQL Installation related Programs.......................................................................................................................9
3.1. mysql_fix_privilege_tables....................................................................................................................................9
3.2. mysql_install_db....................................................................................................................................................9
3.3. mysql_secure_installation.....................................................................................................................................9
3.4. mysql_tzinfo_to_sql...............................................................................................................................................9
4. MySQL Server and Server-Startup Programs..........................................................................................................9
4.1. mysqld — The MySQL Server...............................................................................................................................9
4.2. mysqld_safe — MySQL Server Startup Script....................................................................................................10
4.3. mysql.server — MySQL Server Startup Script....................................................................................................11
4.4. mysqld_multi — Manage Multiple MySQL Servers.............................................................................................11
5. User Account Management....................................................................................................................................11
6. Storage Engines.....................................................................................................................................................15
6.1. Transaction and Nontransaction Engines...........................................................................................................15
6.2. Setting the Storage Engine.................................................................................................................................16
6.3. The MyISAM Storage Engine..............................................................................................................................16
6.3.1. MyISAM Startup Options..........................................................................................................................17
6.3.2. MyISAM Table Storage Formats..............................................................................................................19
6.3.3. MyISAM Table Problems..........................................................................................................................20
6.4. The InnoDB Storage Engine…………………………………………………………………………...........................21
6.4.1. Configuring InnoDB..................................................................................................................................21
6.4.2. InnoDB Table and Index Structures.........................................................................................................22
 6.4.3. Managing InnoDB Data and Log Files.....................................................................................................22
6.4.4. InnoDB Startup Options...........................................................................................................................25
6.4.5. InnoDB Multi-Versioning..........................................................................................................................28
6.4.6. InnoDB Isolation Levels...........................................................................................................................29
6.4.7. InnoDB Lock Modes.................................................................................................................................30
6.4.8. InnoDB Error Handling.............................................................................................................................32
6.4.9. InnoDB Performance Tuning....................................................................................................................32
6.4.10. Restrictions on InnoDB Tables...............................................................................................................34
6.5. The MERGE Storage Engine..............................................................................................................................34
6.6. MERGE Table Problems.....................................................................................................................................36
6.7. The EXAMPLE Storage Engine..........................................................................................................................38
6.8. The FEDERATED Storage Engine......................................................................................................................38
6.8.1. FEDERATED Storage Engine Overview..................................................................................................38
6.8.2. How to Create FEDERATED Tables........................................................................................................39
6.8.3. FEDERATED Storage Engine Notes and Tips.........................................................................................41
6.9. The ARCHIVE Storage Engine............................................................................................................................41
6.10. The CSV Storage Engine..................................................................................................................................42
6.10.1. Repairing and Checking CSV Tables.....................................................................................................42
6.10.2. CSV Limitations......................................................................................................................................43
6.11. The BLACKHOLE Storage Engine....................................................................................................................43
7. MySQL Client Programs........................................................................................................................................44
7.1. mysql — The MySQL Command-Line Tool.........................................................................................................44
7.2. mysqladmin — Client for Administering MySQL Server……………………………………………………………...46
7.3. mysqlcheck — A Table Maintenance Program....................................................................................................47
7.4. mysqldump — A Database Backup Program......................................................................................................48
7.5. mysqlimport — A Data Import Program...............................................................................................................48
7.6. mysqlshow — Display Database, Table and Column Information………………………......................................48
7.7. mysqlslap — Load Emulation Client...................................................................................................................49
8. MySQL Administrative and Utility Programs..........................................................................................................51
8.1. myisamchk — MyISAM Table-Maintenance Utility..............................................................................................51
MySQL Database Administration
 2 
8.2. myisampack — Compress MyISAM Tables........................................................................................................52
8.3. mysql_convert_table_format...............................................................................................................................53
9. MySQL Server Administration................................................................................................................................53
9.1. Server System Variables.....................................................................................................................................53
9.2. Server Status Variables.......................................................................................................................................54
9.3. Server SQL Modes..............................................................................................................................................55
10. MySQL Server Logs.............................................................................................................................................57
10.1. The Error Log....................................................................................................................................................57
10.2. The General Query Log....................................................................................................................................57
10.3. The Binary Log..................................................................................................................................................58
10.4. The Slow Query Log.........................................................................................................................................60
11. Backup and Recovery..........................................................................................................................................61
11.1. Backup and Recovery Types.............................................................................................................................61
11.2. Database Backup Methods...............................................................................................................................62
11.3. Using mysqldump for Backups..........................................................................................................................63
11.3.1. Dumping Data in SQL Format................................................................................................................63
11.3.2. Dumping Data in Delimited-Text Format with mysqldump......................................................................65
11.3.3. Reloading SQL-Format Backups............................................................................................................65
12. Running Multiple MySQL Instances on One Machine..........................................................................................67
12.1. Setting Up Multiple Data Directories.................................................................................................................67
12.2. Running Multiple MySQL Instances on Unix.....................................................................................................68
12.3. Using mysqld_multi for Managing Multiple MySQL Servers.............................................................................69
13. General Security Guidelines................................................................................................................................70
14. Optimization.........................................................................................................................................................70
14.1. Optimization Overview......................................................................................................................................70
14.2. Obtaining Query Execution Plan Information....................................................................................................71
14.2.1. Optimizing Queries with EXPLAIN.........................................................................................................71
14.2.2. Optimizing SELECT Statements............................................................................................................71
14.3. Tuning Server Parameters................................................................................................................................72
15. Partitioning...........................................................................................................................................................75
15.1. Overview of Partitioning in MySQL...................................................................................................................75
15.1. Partitioning Types..............................................................................................................................................75
16. INFORMATION_SCHEMA Tables........................................................................................................................81
17. Buffering and Caching..........................................................................................................................................86
17.1. The MyISAM Key Cache...................................................................................................................................86
17.2. The InnoDB Buffer Pool....................................................................................................................................87
18. Locking Issues.....................................................................................................................................................88
18.1. Internal Locking Methods..................................................................................................................................88
18.2. Table Locking Issues.........................................................................................................................................89
18.3. Concurrent Inserts.............................................................................................................................................89
18.4. External Locking................................................................................................................................................90
19. High Availability and Scalability............................................................................................................................90
19.1. Replication........................................................................................................................................................90
19.1.1. Replication Configuration.......................................................................................................................91
19.2. Replication Solutions.........................................................................................................................................99
20. Upgrading MySQL..............................................................................................................................................103
MySQL Database Administration
 3 
1. Introduction
1.1. Overview of MySQL Database Management System:
MySQL is a database management system
A database is a structured collection of data. It may be anything from a simple shopping list to a picture gallery 
or the vast amounts of information in a corporate network. To add, access, and process data stored in a computer 
database, you need a database management system such as MySQL Server.
MySQL is a relational database management system
A relational database stores data in separate tables rather than putting all the data in one big storeroom. This 
adds speed and flexibility. SQL is the most common standardized language used to access databases and is 
defined by the ANSI/ISO SQL Standard. The SQL standard has been evolving since 1986 and several versions 
exist. In this manual, “SQL-92” refers to the standard released in 1992, “SQL:1999” refers to the standard released 
in 1999, and “SQL:2003” refers to the current version of the standard. We use the phrase “the SQL standard” to 
mean the current version of the SQL Standard at any time.
MySQL software is Open Source
Open Source means that it is possible for anyone to use and modify the software. Anybody can download the 
MySQL software from the Internet and use it without paying anything. If you wish, you may study the source code 
and change it to suit your needs.
1.2. History of MySQL
They started out with the intention of using the mSQL database system to connect to our tables using our own 
fast low-level (ISAM) routines. However, after some testing, we came to the conclusion that mSQL was not fast 
enough or flexible enough for our needs. This resulted in a new SQL interface to our database but with almost the 
same API interface as mSQL.
MySQL is named after co-founder Monty Widenius's daughter, My.
The name of the MySQL Dolphin (our logo) is “Sakila,” which was chosen from a huge list of names 
suggested by users in our “Name the Dolphin” contest. The winning name was submitted by Ambrose Twebaze, an 
Open Source software developer from Swaziland, Africa. According to Ambrose, the feminine name Sakila has its 
roots in SiSwati, the local language of Swaziland. Sakila is also the name of a town in Arusha, Tanzania, near 
Ambrose's country of origin, Uganda.
1.3. The Main Features of MySQL
− Written in C and C++.
− Tested with a broad range of different compilers.
− Works on many different platforms.
− Designed to be fully multi-threaded using kernel threads, to easily use multiple CPUs if they are available
− Provides transactional and nontransactional storage engines.
− Implements in-memory hash tables, which are used as temporary tables.
− Works in cross platform.
Why companies prefer MySQL?
Before MySQL don’t a supported stored procedure, functions, triggers, views, subqueries and partitioning. But 
now they are supported. Small and middle level companies are relied on MySQL because it is opensource. 
Supports replication and clustering for High Availability.
MySQL Database Administration
 4 
1.4. Architecture:
Client/Server Overview:
The MySQL database system operates using a client/server architecture. The server is a central program that 
manages database contents, and client programs connect to the server to retrieve or modify the data. MySQL also 
includes non-client utility programs and scripts.
MySQL Server: This is the mysqld program that manages database and tables. Most users choose binary MySQL 
distribution that includes a server ready to run with the capabilities they need, but it's also possible to compile 
MySQL from source.
Client Programs: These are programs that communicate with the server by sending requests to it over a network 
connection. The server acts on each request and returns a response to the client. For example you can use the 
mysql client to send queries to the server, and the server returns the query results. A client program can connect 
locally to a server running on the same machine or remotely to a server running on a different machine.
Non-client utility programs: These are programs that generally used for special purposes and do not acts as 
MySQL Database Administration
 5 
clients of the server. They do not connect to the server, for example mysqld_safe is a script for starting and 
stopping the server. Myisamchk is a standalone utility for table check and repair.
Application layer:
This is where the client interact with the RDBMS. This layer is used by three users:
Administrator.
client.
User.
i) Administrative Interface and Utilities :
This layer is used by Administrator. This includes utilities such as mysqladmin, myisamchk, mysqldump etc.
ii) Client Interface and Utilities:
This layer is used by the clients to communicate with RBDMS. The client interface uses MySQL APIs for 
various different programming languages such as the PHP API, Java API, etc.
iii) Query Interface:
This use the mysql as a “interactive tool” that issue sql statements to the server and displays results to the screen.
Logical layer:
All ths DML statements that are sent from the application layer are parsed and optimized in the query processor. 
It is again sub-divided into following layers:
i) embedded DML precompiler:
When a request is received from a client in the application layer, it is the responsibility of the embedded DML 
(Data Manipulation Language) precompiler to extract the relevant SQL statements embedded in the client API 
commands, or to translate the client commands into the corresponding SQL statements. 
ii) DDL Compiler:
− Request received from the administrator are processed by the DDL Compiler.
− The administrative utility does not expose any interface and hence executed directly by the server.
iii) Query Preprocessor :
− The query preprocessor parses the query. The parsing is of 2 types
 1) syntactical 
 2) semantical
− If the query syntax is right then it is sent to the next pipe . Else it inform to the client with an a error 
message.
iv) Query Optimizer:
− Query optimizer is the brain of the MySQL.
− Once client has permission to execute query, the query is optimized by the query optimizer. The task of 
the query optimizer is analyze the processed query to see if it can take advantage of any optimizations 
that will allow it to process the query more quickly.MySQL query optimizer uses indexes.
v) Execution Engine:
− Once the MySQL query optimizer has optimized the MySQL query, the query can then be executed 
against the database. This is performed by the query execution engine, which then proceeds to 
execute the SQL statements and access the physical layer. As well the database administrator can 
execute commands on the database to perform specific tasks such as repair, recovery, copying and 
MySQL Database Administration
 6 
backup, which it receives from the DDL compiler.
Transaction Management:
i) Transaction Manager:
A transaction is a single unit of work that has one or more MySQL commands in it. The transaction manager is 
responsible for making sure that the transaction is logged and executed atomically. And also prevents from 
deadlocks. Furthermore, the transaction manager is responsible for issuing the COMMIT and the ROLLBACK SQL 
commands. The COMMIT command commits to performing a transaction. Thus, a transaction is incomplete until it 
is committed to. The ROLLBACK command is used when a crash occurs during the execution of a transaction. If a 
transaction were left incomplete, the ROLLBACK command would undo all changes made by that transaction. The 
result of executing this command is restoring the database to its last stable state. 
− Ensures Atomicity
− Avoids Deadlocks
− Responsible for Commit & Rollback
ii) Concurrency- Control Manager 
The concurrency-control manager is responsible for making sure that transactions are executed separately 
and independently. It does so by acquiring locks. Once the lock is acquired, only the operations in one transaction 
can manipulate the data. If a different transaction tries to manipulate the same locked data, the concurrencycontrol manager rejects the request until the first transaction is complete .
Recovery Management 
iii) Log Manager:
The log manager is responsible for logging every operation executed in the database. It does so by storing the 
log on disk through the buffer manager. The operations in the log are stored as MySQL commands. Thus, in the 
case of a system crash, executing every command in the log will bring back the database to its last stable state. 
iv) Recovery Manager
The recovery manager is responsible for restoring the database to its last stable state. It does so by using the 
log for the database, which is acquired from the buffer manager, and executing each operation in the log. Since the 
log manager logs all operations performed on the database, executing each command in the log file would recover 
the database to its last stable state. 
Storage Management:
 Storage is physically done on some type of secondary storage, however dynamic access of this medium is not 
practical. Thus, all work is done through a number of buffers. The buffers reside in main and virtual memory and 
are managed by a Buffer Manager. 
i) Resource Manager:
The purpose of the Resource Manager is to accept requests from the execution engine, put them into table 
requests, and request the tables from the Buffer Manager. The Resource Manager receives references to data 
within memory from the Buffer Manager and returns this data to the upper layers. 
− Mediator between Execution Engine and Buffer Manager.
ii) Buffer Manager:
The role of the Buffer Manager is to allocate memory resources for the use of viewing and manipulating data. 
The Buffer Manager takes in formatted requests and decides how much memory to allocate per buffer and how 
many buffers to allocate per request. All requests are made from the Resource Manager. 
(key_buffer, sort_buffer, myisam_sort_buffer)
iii) Storage Manager:
MySQL Database Administration
 7 
The storage manager acts as a mediator to send request between buffer manager and secondary storage.
2. MySQL Installation
2.1. Installing MySQL from RPM Packages on Linux
For non-RPM Linux distributions, you can install MySQL using a .tar.gz package.
MySQL-server-VERSION.glibc23.i386.rpm 
The MySQL server. You need this unless you only want to connect to a MySQL server running on another machine. 
MySQL-client-VERSION.glibc23.i386.rpm 
The standard MySQL client programs. You probably always want to install this package to connect to the servers. 
MySQL-devel-VERSION.glibc23.i386.rpm 
The libraries and include files that are needed if you want to compile other MySQL clients, such as the Perl 
modules. 
MySQL-shared-VERSION.glibc23.i386.rpm 
This package contains the shared libraries (libmysqlclient.so*) that certain languages and applications need to 
dynamically load and use MySQL. It contains single-threaded and thread-safe libraries. If you install this package, 
do not install the MySQL-shared-compat package. 
MySQL-shared-compat-VERSION.glibc23.i386.rpm 
This package includes the shared libraries for MySQL 3.23, 4.0, and so on, up to the current release. It contains 
single-threaded and thread-safe libraries. Install this package instead of MySQL-shared if you have applications 
installed that are dynamically linked against older versions of MySQL but you want to upgrade to the current 
version without breaking the library dependencies. 
2.2. Installing MySQL from a Standard Source Distribution
Directory Contents of Directory
bin Client programs and scripts
Var Log files, databases
docs Manual in Info format
man Unix manual pages
Include/mysql Include (header) files
Lib/mysql Libraries
Libexec The mysqld server
share/mysql Miscellaneous support files, including error messages, sample 
configuration files, SQL for database installation
sql-bench Benchmarks
# Preconfiguration setup
shell> groupadd mysql
shell> useradd -g mysql mysql
# Beginning of source-build specific instructions
shell> tar zxvf mysql-VERSION.tar.gz
shell> cd mysql-VERSION
shell> ./configure --prefix=/usr/local/mysql
shell> make
shell> make install
MySQL Database Administration
 8 
# End of source-build specific instructions
# Postinstallation setup
shell> cd /usr/local/mysql
shell> chown -R mysql .
shell> chgrp -R mysql .
shell> bin/mysql_install_db --user=mysql
shell> chown -R root .
shell> chown -R mysql var
# Next command is optional
shell> cp support-files/my-medium.cnf /etc/my.cnf
shell> bin/mysqld_safe --user=mysql &
# Next command is optional
shell> cp support-files/mysql.server /etc/init.d/mysql.server
2.3. Installing MySQL from Generic Binaries on Unix/Linux
Directory Contents of Directory
bin Client programs and the mysqld server
data Log files, databases
docs Manual in Info format
man Unix manual pages
include Include (header) files
Lib Libraries
scripts mysql_install_db
share Miscellaneous support files, including error messages, sample 
configuration files, SQL for database installation
sql-bench Benchmarks
shell> groupadd mysql
shell> useradd -r -g mysql mysql
shell> cd /usr/local
shell> tar zxvf /path/to/mysql-VERSION-OS.tar.gz
shell> ln -s full-path-to-mysql-VERSION-OS mysql
shell> cd mysql
shell> chown -R mysql .
shell> chgrp -R mysql .
shell> scripts/mysql_install_db --user=mysql
shell> chown -R root .
shell> chown -R mysql data
# Next command is optional
shell> cp support-files/my-medium.cnf /etc/my.cnf
shell> bin/mysqld_safe --user=mysql &
# Next command is optional
MySQL Database Administration
 9 
shell> cp support-files/mysql.server /etc/init.d/mysql.server
2.4 Setting Environment Variables
# vi .bash_profile
export MySQL_HOME=/usr/local/mysql
#PATH=$PATH:$HOME/bin
PATH=$PATH:$HOME/bin:$MySQL_HOME
export MYSQL_HOME='localhost'
export USER='localhost' Only on Win and Netware
export MYSQL_PWD='localhost'
3. MySQL Installation related Programs
3.1. mysql_fix_privilege_tables is an older script that previously was used to uprade the system tables in the 
mysql database after a MySQL upgrade. 
As of MySQL 5.0.19, mysql_fix_privilege_tables is superseded by mysql_upgrade, which should be used 
instead. Before running mysql_fix_privilege_tables, make a backup of your mysql database. 
On Unix or Unix-like systems, update the system tables by running the mysql_fix_privilege_tables script: 
shell> mysql_fix_privilege_tables --password=XXX
3.2. mysql_install_db initializes the MySQL data directory and creates the system tables that it contains, if they do 
not exist. 
shell> bin/mysql_install_db --user=mysql --basedir=/opt/mysql/mysql –datadir=/opt/mysql/mysql/data
bootstrap This option is used by the mysql_install_db script to create the MySQL privilege tables without having to 
start a full MySQL server
3.3. mysql_secure_installation
This program enables you to improve the security of your MySQL installation in the following ways: 
− You can set a password for root accounts.
− You can remove root accounts that are accessible from outside the local host. 
− You can remove anonymous-user accounts. 
− You can remove the test database (which by default can be accessed by all users, even anonymous 
users)
shell> mysql_secure_installation
3.4. mysql_tzinfo_to_sql
The mysql_tzinfo_to_sql program loads the time zone tables in the mysql database. It is used on systems that 
have a zoneinfo database (the set of files describing time zones). Examples of such systems are Linux, FreeBSD, 
Solaris, and Mac OS X. One likely location for these files is the “/usr/share/zoneinfo” directory
shell> mysql_tzinfo_to_sql /usr/share/zoneinfo | mysql -u root mysql
4. MySQL Server and Server-Startup Programs:
4.1. mysqld — The MySQL Server
mysqld, also known as MySQL Server, is the main program that does most of the work in a MySQL installation. 
MySQL Server manages access to the MySQL data directory that contains databases and tables. The data 
directory is also the default location for other information such as log files and status files. 
When MySQL server starts, it listens for network connections from client programs and manages access to 
databases on behalf of those clients. 
The mysqld program has many options that can be specified at startup. For a complete list of options, run this 
command: 
MySQL Database Administration
 10 
shell> mysqld --verbose –help
Command to start mysql
shell> mysqld –user=mysql // (--console)
MySQL Server also has a set of system variables that affect its operation as it runs. System variables can be set at 
server startup, and many of them can be changed at runtime to effect dynamic server reconfiguration. MySQL 
Server also has a set of status variables that provide information about its operation. You can monitor these status 
variables to access runtime performance characteristics. 
4.2. mysqld_safe — MySQL Server Startup Script
mysqld_safe is the recommended way to start a mysqld server on Unix and NetWare. mysqld_safe adds some 
safety features such as restarting the server when an error occurs and logging runtime information to an error log 
file.
mysqld_safe reads all options from the [mysqld], [server], and [mysqld_safe] sections in option files. 
The mysqld_safe script is written so that it normally can start a server that was installed from either a source or a 
binary distribution of MySQL, even though these types of distributions typically install the server in slightly different 
locations. (See Section 2.7, “Installation Layouts”.) mysqld_safe expects one of the following conditions to be true:
The server and databases can be found relative to the working directory (the directory from 
which mysqld_safe is invoked). For binary distributions, mysqld_safe looks under its working directory 
for bin and data directories. For source distributions, it looks for libexec and var directories. This condition should 
be met if you execute mysqld_safe from your MySQL installation directory (for example, /usr/local/mysql for a 
binary distribution).
If the server and databases cannot be found relative to the working directory, mysqld_safe attempts to locate 
them by absolute path names. Typical locations are /usr/local/libexec and /usr/local/var. The actual locations are 
determined from the values configured into the distribution at the time it was built. They should be correct if 
MySQL is installed in the location specified at configuration time.
--basedir=path
The path to the MySQL installation directory.
--help
Display a help message and exit
--defaults-extra-file=path
The name of an option file to be read in addition to the usual option files.
--log-error=file_name
Write the error log to the given file
--ledir=path
If mysqld_safe cannot find the server, use this option to indicate the path name to the directory where 
the server is located
--no-defaults
Do not read any option files. This must be the first option on the command line if it is used.
--defaults-file=file_name
The name of an option file to be read instead of the usual option files. This must be the first option on the 
command line if it is used.
--mysqld-version=suffix
This option is similar to the --mysqld option, but you specify only the suffix for the server program name. The 
basename is assumed to be mysqld. For example, if you use --mysqld-version=debug, mysqld_safe starts 
the mysqld-debug program in the ledir directory. If the argumentto --mysqld-version is 
empty,mysqld_safe uses mysqld in the ledir directory.
--open-files-limit=count
MySQL Database Administration
 11 
The number of files that mysqld should be able to open. The option value is passed to ulimit -n. Note that you 
need to start mysqld_safe as root for this to work properly!
--pid-file=file_name
The path name of the process ID file.
--port=port_num
The port number that the server should use when listening for TCP/IP connections. The port number must be 
1024 or higher unless the server is started by the root system user.
--socket=path
The Unix socket file that the server should use when listening for local connections.
4.3. mysql.server — MySQL Server Startup Script
MySQL distributions on Unix include a script named mysql.server. It can be used on systems such as Linux 
and Solaris that use System V-style run directories to start and stop system services. It is also used by the Mac OS 
X Startup Item for MySQL. mysql.server can be found in the support-files directory under your MySQL installation 
directory or in a MySQL source distribution.
--basedir=path
The path to the MySQL installation directory.
--datadir=path
The path to the MySQL data directory.
--pid-file=file_name
The path name of the file in which the server should write its process ID.
--service-startup-timeout=file_name
How long in seconds to wait for confirmation of server startup. If the server does not start within this time, 
mysql.server exits with an error. The default value is 900. A value of 0 means not to wait at all for startup. Negative 
values mean to wait forever (no timeout). This option was added in MySQL 5.1.17. Before that, a value of 900 is 
always used.
--use-mysqld_safe
Use mysqld_safe to start the server. This is the default.
--user=user_name
The login user name to use for running mysqld.
4.4. mysqld_multi ― Manage Multiple MySQL Servers
We will go through this in Chapter 12.
5. User Account Management
We can create User Accounts in two ways.
 1. By using CREATE USER or GRANT statements. (Recommended Method)
 2. By manipulating the mysql grant tables with statements like INSERT and DELETE.
Using CREATE USER and GRANT statements:
Creating a User:
By using CREATE USER statement we can just create users and we cannot grant privileges to the user. To 
use this statement you should have CREATE USER privilege.
For Single user:
Syntax: CREATE USER <username> IDENTIFIED BY <password> ;
MySQL Database Administration
 12 
For Multiple user:
Syntax: CREATE USER <username> IDENTIFIED BY <password>, <username> 
IDENTIFIED BY <password>, <username> IDENTIFIED BY <password>........... ;
Using GRANT statement we can create users and as well as we can grant privileges to the users. For using 
this statement you should have GRANT privilege and you should have privileges that you are granting for others.
This statement can be used in many ways. Some examples of them are:
 1. mysql> GRANT ALL PRIVILEGES ON *.* TO 'username'@'hostname' IDENTIFIED BY <password> WITH 
GRANT OPTION;
The above statement grants all privileges on all databases to specified user name and host name.
If the use name doesn't exists it create a user and grants privileges and if the user exists the password is also 
changed.
If you do not want to change the password use the below query
 mysql> GRANT ALL PRIVILEGES ON *.* TO 'username'@'hostname' ;
 2. mysql> GRANT SELECT, INSERT, UPDATE ON *.* TO 'username'@'hostname' IDENTIFIED BY 
<password>;
The above statement grants SELECT, INSERT, UPDATE privileges on all databases to specified user name and 
host name.
 3. mysql> GRANT SELECT, INSERT, UPDATE ON DB1.* TO 'username'@'hostname';
The above statement grants SELECT, INSERT, UPDATE privileges on DB1 database to specified user name and 
host name.
 4. mysql> GRANT ALL PRIVILEGES ON DB1.TBL1 TO 'username'@'hostname';
The above statement grants SELECT, INSERT, UPDATE privileges on DB1.TBL1 table to specified user name and 
host name.
 5. mysql> GRANT ALL PRIVILEGES ON *.* TO 'username'@'hostname' WITH 
MAX QUERIES PER HOUR 50
MAX UPDATES PER HOUR 15
MAX CONNECTIONS PER HOUR 3
MAX USER CONNECTIONS 2;
The above statement grants all privileges on all databases to specified user name and host name and restricts user 
resources. By the above query the user can only execute 50 queries per hour, 15 update queries per hour, and can 
connect max 3 times in an hour and the user can have only 2 simultaneous connections.
Renaming a User:
To rename a user you must have global CREATE USER privilege. Renaming a user does not automatically migrate 
all the objects that the user has created.
For Single user:
Syntax: RENAME USER <old_username> TO <new_username> ;
For Multiple user:
Syntax: RENAME USER <old_username> TO <new_username>, <old_username> TO <new_username>, 
<old_username> TO <new_username>.......;
Revoking Privileges:
MySQL Database Administration
 13 
mysql> REVOKE ALL PRIVILEGES FROM <username>;
The above statement revokes all privileges for the specified user.
mysql> REVOKE ALL PRIVILEGES ON DB1.* FROM <username>;
The above statement revokes all privileges on DB1 database for the specified user.
mysql> REVOKE ALL PRIVILEGES ON DB1.TBL1 FROM <username>;
The above statement revokes all privileges on DB1.TBL1 table database for the specified user.
Setting Password:
The below statement is used to set/update user password. In case if the user forgets his password we can use this 
statement to reset the password.
Syntax: SET PASSWORD FOR '<username>'@'<host name>' = PASSWORD('<password>');
Removing User:
To drop a user you should have global CREATE USER privilege. Dropping a user does not automatically close any 
opened sessions and it does not automatically delete the objects created by the user.
Syntax: DROP USER username;
IMP: After every DML Command on grant tables we need to issue FLUSH PRIVILEGES Command. Otherwise 
the permission will not effect until the MySQL Server is restarted.
To execute FLUSH PRIVILEGES you need to have the RELOAD privilege.
Once the MySQL Server is started it will store all the grant tables in the memory. After every GRANT, 
REVOKE statements it will reload the grant tables. But by using the DML commands it doesn't reload the tables. 
This may be the reason DML commands on grant tables are not recommended.
Creating a User:
If you want just to create a user, insert a row in mysql.user table providing values for host and user. For this you 
need to have a INSERT privilege on mysql.user table.
Syntax: INSERT INTO user (host, user) VALUES ('<host name>', '<user name>');
Granting Global Privileges:
To grant all privileges on all the databases insert a row into the mysql.user table. 
Syntax: INSERT INTO user (host, user, password, Select_priv, Insert_priv, Update_priv, Delete_priv, 
Create_priv, Drop_priv, Reload_priv, Shutdown_priv, Process_priv, File_priv, Grant_priv, References_priv, 
Index_priv, Alter_priv, Show_db_priv, Super_priv, Create_tmp_table_priv, Lock_tables_priv, Execute_priv, 
Repl_slave_priv, Repl_client_priv, Create_view_priv, Show_view_priv, Create_routine_priv, Alter_routine_priv, 
Create_user_priv) VALUES ('<hostname>', '<username>', password('<password>', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 
'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y', 'Y'));
In the above statement if you doesn't want to give any privileges we can set the flag as 'N'.
Also we can set below values in the same table.
max_questions --> Defines max queries for the user per hour.
max_updates --> Defines max updates for the user per hour.
max_connections --> Defines max connections for the user per hour.
max_user_connections --> Defines max simultaneous connections by the user . 
Granting Database Level Privileges:
If you want to grant privileges on database level we need to insert a row in mysql.db table. For this the user need 
to have INSERT privilege on mysql.db table.
Before Inserting a row in this table a row in mysql.user table need to be inserted for the respective user with all the 
privileges as “N”.
MySQL Database Administration
 14 
Granting Table Level Privileges:
If you want to grant privileges on table level we need to insert a row in mysql.tables_priv table. For this the user 
need to have INSERT privilege on mysql.tables_priv table.
Before Inserting a row in this table a row in mysql.user table need to be inserted for the respective user with all the 
privileges as “N”.
Revoking Privileges:
If you want to revoke global privileges for user just set value as 'N' in mysql.user table for respective 
privilege. 
 If you want to revoke some database level privileges for a user just set value as 'N' in mysql.db table for 
respective privilege or if you want to revoke entire privileges on a particular database just delete the row from 
mysql.db table for specified user and db.
If you want to revoke some table level privileges for a user update table_priv field on mysql.tables_priv table 
or if you want to revoke entire privileges on a particular table just delete the row from mysql.tables_priv table for 
specified user, db and table.
Setting Password:
If you want set/update a password execute the below statement.
Syntax: mysql> UPDATE mysql.user SET password = PASSWORD('<password>'); 
Removing User:
Deleting a user need to remove rows from three tables.
1. Delete a record from mysql.user table.
2. Delete records from mysql.db table.
3. Delete records from mysql.tables_priv table.
 
Syntax: mysql> DELETE FROM mysql.user WHERE user = '<username>';
 mysql> DELETE FROM mysql.db WHERE user = '<username>';
 mysql> DELETE FROM mysql.tables_priv WHERE user = '<username>';
Resetting Administrator Password:
If the administrator forgets the password restart the MySQL Server with --skip-grant-tables option.
By this the MySQL stops loading the grant tables and we can login to the MySQL without any password. There you 
can update password in mysql.user table and start MySQL Server as usual.
Follow below steps:
[shell]# /etc/init.d/mysqld stop
[shell]# /etc/init.d/mysqld start --skip-grant-tables
[shell]# mysql
mysql> UPDATE mysql.user SET password = PASSWORD('new password') WHERE user = '<username>' AND 
host = '<host name>';
mysql> \q
[shell]# /etc/init.d/mysqld restart
MySQL Database Administration
 15 
6. Storage Engines
6.1 Comparing Transaction and Nontransaction Engines
− Transaction-safe tables (TSTs) have several advantages over nontransaction-safe tables (NTSTs):
− They are safer. Even if MySQL crashes or you get hardware problems, the database will be in a 
consistency form.
− You can combine many statements and accept them all at the same time with the COMMIT statement 
(if autocommit is disabled).
− You can execute ROLLBACK to ignore your changes (if autocommit is disabled).
− If an update fails, all of your changes are reverted. (With nontransaction-safe tables, all changes that 
have taken place are permanent.)
− Transaction-safe storage engines can provide better concurrency for tables that get many updates 
concurrently with reads.
− You can combine transaction-safe and nontransaction-safe tables in the same statements to get the 
best result. However, although MySQL supports several transaction-safe storage engines, for best 
results, you should not mix different storage engines within a transaction with autocommit disabled. For 
example, if you do this, changes to nontransaction-safe tables still are committed immediately and 
cannot be rolled back.
Nontransaction-safe tables have several advantages of their own, all of which occur because there is no 
transaction overhead:
− Much faster
− Lower disk space requirements
− Less memory required to perform updates
6.2 Setting the Storage Engine
Privilege Type Table Priv Function
CREATE Create_priv databases, tables, or indexes
DROP Drop_priv databases, tables, or views
GRANT OPTION Grant_priv databases, tables, or stored routines
REFERENCES References_priv UNUSED
EVENT Event_priv databases
ALTER Alter_priv tables
DELETE Delete_priv tables
INDEX Index_priv tables
INSERT Insert_priv tables or columns
SELECT Select_priv tables or columns
UPDATE Update_priv tables or columns
CREATE TEMPORARY TABLES Create_tmp_table_priv tables
LOCK TABLES Lock_tables_priv tables
TRIGGER Trigger_priv tables
CREATE VIEW Create_view_priv views
SHOW VIEW Show_view_priv views
ALTER ROUTINE Alter_routine_priv stored routines
CREATE ROUTINE Create_routine_priv stored routines
EXECUTE Execute_priv To execute stored routines
FILE File_priv OUTFILE, INFILE
CREATE TABLESPACE Create_tablespace_priv server administration
CREATE USER Create_user_priv server administration
PROCESS Process_priv SHOW PROCESSLIST
RELOAD Reload_priv FLUSH STATEMENTS
REPLICATION CLIENT Repl_client_priv SHOW MASTER & SLAVE
REPLICATION SLAVE Repl_slave_priv REPLICATION
SHOW DATABASES Show_db_priv server administration
SHUTDOWN Shutdown_priv server administration
SUPER Super_priv CHANGE MASTER, KILL, PURGE, SET GLOBAL 
USAGE To connect to MySQL
MySQL Database Administration
 16 
When you create a new table, you can specify which storage engine to use by adding an ENGINE table option to 
the CREATE TABLE statement:
mysql> CREATE TABLE t (i INT) ENGINE = INNODB;
If you omit the ENGINE option, the default engine is used. Normally, this is MyISAM, but you can change it by using 
the --default-storage-engine server startup option, or by setting the default-storage-engine option in the my.cnf 
configuration file.
You can set the default storage engine to be used during the current session by setting the storage_engine 
variable:
mysql> SET storage_engine=MYISAM;
To convert a table from one storage engine to another, use an ALTER TABLE statement that indicates the new 
engine:
mysql> ALTER TABLE t ENGINE = MYISAM;
If you try to use a storage engine that is not compiled in or that is compiled in but deactivated, MySQL instead 
creates a table using the default storage engine. This behavior is convenient when you want to copy tables 
between MySQL servers that support different storage engines. (For example, in a replication setup, perhaps your 
master server supports transactional storage engines for increased safety, but the slave servers use only nontransactional storage engines for greater speed.)
A warning is generated whenever a storage engine is automatically changed. To prevent this from happening 
if the desired engine is unavailable, enable the NO_ENGINE_SUBSTITUTION SQL mode. In this case, an error 
occurs instead of a warning and the table is not created or altered if the desired engine is unavailable.
A database may contain tables of different types. That is, tables need not all be created with the same storage 
engine.
6.3. The MyISAM Storage Engine
MyISAM is the default storage engine still 5.1.X version, from 5.5.X InnoDB is the default storage engine. It is 
based on the older (and no longer available) ISAM storage engine but has many useful extensions.
Each MyISAM table is stored on disk in three files. The files have names that begin with the table name and have 
an extension to indicate the file type. An .frm file stores the table format. The data file has an .MYD (MYData) 
extension. The index file has an .MYI (MYIndex) extension.
To specify explicitly that you want a MyISAM table, indicate that with an ENGINE table option:
mysql> CREATE TABLE t (i INT) ENGINE = MYISAM;
You can check or repair MyISAM tables with the mysqlcheck client or myisamchk utility. You can also compress 
MyISAM tables with myisampack to take up much less space.
MyISAM tables have the following characteristics:
− There is a limit of 232 (~4.295E+09) rows in a MyISAM table. If you build MySQL with the --with-bigtables option, the row limitation is increased to (232)2 (1.844E+19) rows.
− The maximum number of indexes per MyISAM table is 64. This can be changed by recompiling. 
Beginning with MySQL 5.1.4, you can configure the build by invoking configure with the --with-maxindexes=N option, where N is the maximum number of indexes to permit per MyISAM table. N must be 
less than or equal to 128. 
 The maximum number of columns per index is 16.
− The maximum key length is 1000 bytes. This can also be changed by changing the source and 
recompiling.
− There is a flag in the MyISAM index file that indicates whether the table was closed correctly. If mysqld 
is started with the --myisam-recover option, MyISAM tables are automatically checked when opened, 
and are repaired if the table wasn't closed properly. 
MySQL Database Administration
 17 
− Tables can be repaired.
− You can put the data file and index file in different directories on different physical devices to get more 
speed with the DATA DIRECTORY and INDEX DIRECTORY table options to CREATE TABLE.
6.3.1. MyISAM Startup Options
The following options to mysqld can be used to change the behavior of MyISAM tables.
bulk_insert_buffer_size
MyISAM uses a special tree-like cache to make bulk inserts faster for INSERT ... SELECT, INSERT ... 
VALUES (...), (...), ..., and LOAD DATA INFILE when adding data to nonempty tables. This variable limits the size of 
the cache tree in bytes per thread. Setting it to 0 disables this optimization. The default value is 8MB. 
Allocated per each session.
concurrent_insert
If 1 (the default), MySQL permits INSERT and SELECT statements to run concurrently for MyISAM tables that 
have no free blocks in the middle of the data file. If you start mysqld with --skip-new, this variable is set to 0. 
This variable can take three integer values. 
Value Description
0 Disables concurrent inserts
1 (Default) Enables concurrent insert for MyISAM tables that do not have holes
2
Enables concurrent inserts for all MyISAM tables, even those that have holes. For a table with a hole, new 
rows are inserted at the end of the table if it is in use by another thread. Otherwise, MySQL acquires a 
normal write lock and inserts the row into the hole.
delay_key_write
This option applies only to MyISAM tables. It can have one of the following values to affect handling of the 
DELAY_KEY_WRITE table option that can be used in CREATE TABLE statements. 
Option Description
OFF DELAY_KEY_WRITE is ignored.
ON MySQL honors any DELAY_KEY_WRITE option specified in CREATE TABLE statements. This is the 
default value.
ALL All new opened tables are treated as if they were created with the DELAY_KEY_WRITE option enabled.
If DELAY_KEY_WRITE is enabled for a table, the key buffer is not flushed for the table on every index update, 
but only when the table is closed. This speeds up writes on keys a lot, but if you use this feature, you should add 
automatic checking of all MyISAM tables by starting the server with the –myisam-recover.
key_buffer_size
Index blocks for MyISAM tables are buffered and are shared by all threads. key_buffer_size is the size of the 
buffer used for index blocks. The key buffer is also known as the key cache. 
The maximum permissible setting for key_buffer_size is 4GB on 32-bit platforms. As of MySQL 5.1.23, values 
larger than 4GB are permitted for 64-bit platforms, except 64-bit Windows prior to MySQL 5.1.31, for which large 
values are truncated to 4GB with a warning. As of MySQL 5.1.31, values larger than 4GB are also permitted for 64-
bit Windows. The effective maximum size might be less, depending on your available physical RAM and perprocess RAM limits imposed by your operating system or hardware platform
25% of the machine's total memory is an acceptable value for this variable. However, you should be aware 
that, if you make the value too large (for example, more than 50% of the machine's total memory), your system 
might start to page and become extremely slow. This is because MySQL relies on the operating system to perform 
file system caching for data reads, so you must leave some room for the file system cache. You should also 
consider the memory requirements of any other storage engines that you may be using in addition to MyISAM. 
MySQL Database Administration
 18 
It is possible to create multiple MyISAM key caches. The size limit of 4GB applies to each cache individually, not as 
a group.
key_cache_block_size
The size in bytes of blocks in the key cache. The default value is 1024.
(Range 512-16384)
myisam_max_sort_file_size
The maximum size of the temporary file that MySQL is permitted to use while re-creating a MyISAM index 
(during REPAIR TABLE, ALTER TABLE, or LOAD DATA INFILE). If the file size would be larger than this value, the 
index is created using the key cache instead, which is slower. The value is given in bytes. 
The default value is 2GB (Max valve depends on ur disk size). If MyISAM index files exceed this size and disk 
space is available, increasing the value may help performance. The space must be available in the file system 
containing the directory where the original index file is located. 
--myisam-recover
Set the MyISAM storage engine recovery mode. The option value is any combination of the values of 
DEFAULT, BACKUP, FORCE, or QUICK. If you specify multiple values, separate them by commas. Specifying the 
option with no argument is the same as specifying DEFAULT, and specifying with an explicit value of "" disables 
recovery (same as not giving the option). If recovery is enabled, each time mysqld opens a MyISAM table, it checks 
whether the table is marked as crashed or was not closed properly. (The last option works only if you are running 
with external locking disabled.) If this is the case, mysqld runs a check on the table. If the table was corrupted, 
mysqld attempts to repair it. 
The following options affect how the repair works. 
Option Description
DEFAULT Recovery without backup, forcing, or quick checking.
BACKUP If the data file was changed during recovery, save a backup of the tbl_name.MYD file as tbl_namedatetime.BAK.
FORCE Run recovery even if we would lose more than one row from the .MYD file.
QUICK Do not check the rows in the table if there are not any delete blocks.
Before the server automatically repairs a table, it writes a note about the repair to the error log. If you want to 
be able to recover from most problems without user intervention, you should use the options BACKUP,FORCE. 
This forces a repair of a table even if some rows would be deleted, but it keeps the old data file as a backup so that 
you can later examine what happened. 
If the recovery wouldn't be able to recover all rows from previously completed statements and you didn't 
specify FORCE in the value of the --myisam-recover option, automatic repair aborts with an error message in the 
error log:
Error: Couldn't repair table: db.table
If you specify FORCE, a warning like this is written instead:
Warning: Found 344 of 354 rows when repairing ./db/table
myisam_repair_threads
If this value is greater than 1, MyISAM table indexes are created in parallel (each index in its own thread) during the 
Repair by sorting process. The default value is 1. 
Note: Multi-threaded repair is still beta-quality code.
tmp_table_size
The maximum size of internal in-memory temporary tables. (The actual limit is determined as the minimum of 
tmp_table_size and max_heap_table_size.) If an in-memory temporary table exceeds the limit, MySQL 
automatically converts it to an on-disk MyISAM table. Increase the value of tmp_table_size (and 
max_heap_table_size if necessary) if you do many advanced GROUP BY queries and you have lots of memory. 
MySQL Database Administration
 19 
This variable does not apply to user-created MEMORY tables. 
You can compare the number of internal on-disk temporary tables created to the total number of internal temporary 
tables created by comparing the values of the Created_tmp_disk_tables and Created_tmp_tables variables. 
Space Needed for Keys:
MyISAM tables use B-tree indexes. You can roughly calculate the size for the index file as (key_length+4)/0.67, 
summed over all keys. This is for the worst case when all keys are inserted in sorted order and the table doesn't 
have any compressed keys.
6.3.2. MyISAM Table Storage Formats:
MyISAM supports three different storage formats. Two of them, fixed and dynamic format, are chosen 
automatically depending on the type of columns you are using. The third, compressed format, can be created only 
with the myisampack utility.
When you use CREATE TABLE or ALTER TABLE for a table that has no BLOB or TEXT columns, you can force the 
table format to FIXED or DYNAMIC with the ROW_FORMAT table option.
You can decompress (unpack) compressed MyISAM tables using myisamchk --unpack
6.3.2.1. Static (Fixed-Length) Table Characteristics:
Static format is the default for MyISAM tables. It is used when the table contains no variable-length columns 
(VARCHAR, VARBINARY, BLOB, or TEXT). Each row is stored using a fixed number of bytes. Of the three 
MyISAM storage formats, static format is the simplest and most secure (least subject to corruption). It is also the 
fastest of the on-disk formats due to the ease with which rows in the data file can be found on disk: To look up a 
row based on a row number in the index, multiply the row number by the row length to calculate the row position. 
Also, when scanning a table, it is very easy to read a constant number of rows with each disk read operation.
The security is evidenced if your computer crashes while the MySQL server is writing to a fixed-format MyISAM file. 
In this case, myisamchk can easily determine where each row starts and ends, so it can usually reclaim all rows 
except the partially written one. Note that MyISAM table indexes can always be reconstructed based on the data 
rows.
Note: Fixed-length row format is only available for tables without BLOB or TEXT columns. Creating a table with 
these columns with an explicit ROW_FORMAT clause will not raise an error or warning; the format specification will 
be ignored.
Static-format tables have these characteristics:
− CHAR and VARCHAR columns are space-padded to the specified column width, although the column 
type is not altered. BINARY and VARBINARY columns are padded with 0x00 bytes to the column 
width.
− Very quick.
− Easy to cache.
− Easy to reconstruct after a crash, because rows are located in fixed positions.
− Reorganization is unnecessary unless you delete a huge number of rows and want to return free disk 
space to the operating system. To do this, use OPTIMIZE TABLE or myisamchk -r.
− Usually require more disk space than dynamic-format tables.
6.3.2.2. Dynamic Table Characteristics:
Dynamic storage format is used if a MyISAM table contains any variable-length columns (VARCHAR, 
VARBINARY, BLOB, or TEXT), or if the table was created with the ROW_FORMAT=DYNAMIC table option.
Dynamic format is a little more complex than static format because each row has a header that indicates how 
long it is. A row can become fragmented (stored in noncontiguous pieces) when it is made longer as a result of an 
update.
You can use OPTIMIZE TABLE or myisamchk -r to defragment a table. If you have fixed-length columns that 
you access or change frequently in a table that also contains some variable-length columns, it might be a good idea 
to move the variable-length columns to other tables just to avoid fragmentation.
MySQL Database Administration
 20 
Dynamic-format tables have these characteristics:
- All string columns are dynamic except those with a length less than four.
− Each row is preceded by a bitmap that indicates which columns contain the empty string (for string 
columns) or zero (for numeric columns). Note that this does not include columns that contain NULL 
values. If a string column has a length of zero after trailing space removal, or a numeric column has a 
value of zero, it is marked in the bitmap and not saved to disk. Nonempty strings are saved as a length 
byte plus the string contents.
− Much less disk space usually is required than for fixed-length tables.
− Each row uses only as much space as is required. However, if a row becomes larger, it is split into as 
many pieces as are required, resulting in row fragmentation. For example, if you update a row with 
information that extends the row length, the row becomes fragmented. In this case, you may have to 
run OPTIMIZE TABLE or myisamchk -r from time to time to improve performance. Use myisamchk -ei 
to obtain table statistics.
− More difficult than static-format tables to reconstruct after a crash, because rows may be fragmented 
into many pieces and links (fragments) may be missing.
− The expected row length for dynamic-sized rows is calculated using the following expression:
3+ (number of columns + 7) / 8
+ (number of char columns)
+ (packed size of numeric columns)
+ (length of strings)
+ (number of NULL columns + 7) / 8
There is a penalty of 6 bytes for each link. A dynamic row is linked whenever an update causes an 
enlargement of the row. Each new link is at least 20 bytes, so the next enlargement probably goes in the same link. 
If not, another link is created. You can find the number of links using myisamchk -ed. All links may be removed with 
OPTIMIZE TABLE or myisamchk -r.
6.3.3. MyISAM Table Problems:
The file format that MySQL uses to store data has been extensively tested, but there are always 
circumstances that may cause database tables to become corrupted. The following discussion describes how this 
can happen and how to handle it.
− The mysqld process is killed in the middle of a write.
− An unexpected computer shutdown occurs (for example, the computer is turned off).
− Hardware failures.
− You are using an external program (such as myisamchk) to modify a table that is being modified by the 
server at the same time.
− A software bug in the MySQL or MyISAM code.
Typical symptoms of a corrupt table are:
You get the following error while selecting data from the table:
Incorrect key file for table: '...'. Try to repair it
Queries don't find rows in the table or return incomplete results.
You can check the health of a MyISAM table using the CHECK TABLE statement, and repair a corrupted 
MyISAM table with REPAIR TABLE. When mysqld is not running, you can also check or repair a table with the 
myisamchk command.
If your tables become corrupted frequently, you should try to determine why this is happening. The most important 
thing to know is whether the table became corrupted as a result of a server crash. You can verify this easily by 
looking for a recent restarted mysqld message in the error log. If there is such a message, it is likely that table 
corruption is a result of the server dying. Otherwise, corruption may have occurred during normal operation. This is 
a bug. You should try to create a reproducible test case that demonstrates the problem.
Problems from Tables Not Being Closed Properly:
Each MyISAM index file (.MYI file) has a counter in the header that can be used to check whether a table has been 
MySQL Database Administration
 21 
closed properly. If you get the following warning from CHECK TABLE or myisamchk, it means that this counter has 
gone out of sync:
clients are using or haven't closed the table properly
This warning doesn't necessarily mean that the table is corrupted, but you should at least check the table.
The counter works as follows:
− The first time a table is updated in MySQL, a counter in the header of the index files is incremented.
− The counter is not changed during further updates.
− When the last instance of a table is closed (because a FLUSH TABLES operation was performed or 
because there is no room in the table cache), the counter is decremented if the table has been updated 
at any point.
− When you repair the table or check the table and it is found to be okay, the counter is reset to zero.
− To avoid problems with interaction with other processes that might check the table, the counter is not 
decremented on close if it was zero.
In other words, the counter can become incorrect only under these conditions:
− A MyISAM table is copied without first issuing LOCK TABLES and FLUSH TABLES.
− MySQL has crashed between an update and the final close. (Note that the table may still be okay, 
because MySQL always issues writes for everything between each statement.)
− A table was modified by myisamchk --recover or myisamchk --update-state at the same time that it was 
in use by mysqld.
− Multiple mysqld servers are using the table and one server performed a REPAIR TABLE or CHECK 
TABLE on the table while it was in use by another server. In this setup, it is safe to use CHECK TABLE, 
although you might get the warning from other servers. However, REPAIR TABLE should be avoided 
because when one server replaces the data file with a new one, this is not known to the other servers.
In general, it is a bad idea to share a data directory among multiple servers.
6.4. The InnoDB Storage Engine
InnoDB is a transaction-safe (ACID compliant) storage engine for MySQL that has commit, rollback, and 
crash-recovery capabilities to protect user data. InnoDB row-level locking (without escalation to coarser granularity 
locks) and Oracle-style consistent nonlocking reads increase multi-user concurrency and performance. To maintain 
data integrity, InnoDB also supports FOREIGN KEY referential-integrity constraints. You can freely mix InnoDB 
tables with tables from other MySQL storage engines, even within the same statement.
To determine whether your server supports InnoDB use the SHOW ENGINES statement.
The InnoDB storage engine maintains its own buffer pool for caching data and indexes in main memory. 
InnoDB stores its tables and indexes in a tablespace, which may consist of several files (or raw disk partitions). 
This is different from, for example, MyISAM tables where each table is stored using separate files. InnoDB tables 
can be very large even on operating systems where file size is limited to 2GB.
6.4.1. Configuring InnoDB
The first decisions to make about InnoDB configuration involve how to lay out InnoDB data files, and how 
much memory to allocate for the InnoDB storage engine. You record these choices either by recording them in a 
configuration file that MySQL reads at startup, or by specifying them as command-line options in a startup script.
Two important disk-based resources managed by the InnoDB storage engine are its tablespace data files and 
its log files. If you specify no InnoDB configuration options, MySQL creates an auto-extending 10MB data file 
named ibdata1 and two 5MB log files named ib_logfile0 and ib_logfile1 in the MySQL data directory. To get good 
performance, explicitly provide InnoDB parameters.
Considerations for Storage Devices:
Database performance improves if the data is not all placed on the same physical disk. Putting log files on a 
different disk from data is very often beneficial for performance. The example illustrates how to do this. It places the 
two data files on different disks and places the log files on the third disk. InnoDB fills the tablespace beginning with 
the first data file. You can also use raw disk partitions (raw devices) as InnoDB data files, which may speed up I/O.
MySQL Database Administration
 22 
6.4.2. InnoDB Table and Index Structures
MySQL stores its data dictionary information for tables in .frm files in database directories. This is true for all 
MySQL storage engines, but every InnoDB table also has its own entry in the InnoDB internal data dictionary inside 
the tablespace. When MySQL drops a table or a database, it has to delete one or more .frm files as well as the 
corresponding entries inside the InnoDB data dictionary. Consequently, you cannot move InnoDB tables between 
databases simply by moving the .frm files.
6.4.3. Managing InnoDB Data and Log Files
To set up the InnoDB tablespace files, use the innodb_data_file_path option in the [mysqld] section of the 
my.cnf option file. On Windows, you can use my.ini instead. The value of innodb_data_file_path should be a list of 
one or more data file specifications. If you name more than one data file, separate them by semicolon (“;”) 
characters:
innodb_data_file_path=datafile_spec1[;datafile_spec2]...
For example, the following setting explicitly creates a tablespace having the same characteristics as the 
default:
[mysqld]
innodb_data_file_path=ibdata1:10M:autoextend
This setting configures a single 10MB data file named ibdata1 that is auto-extending. No location for the file is 
given, so by default, InnoDB creates it in the MySQL data directory. Sizes are specified using K, M, or G suffix 
letters to indicate units of KB, MB, or GB.
A tablespace containing a fixed-size 50MB data file named ibdata1 and a 50MB auto-extending file named 
ibdata2 in the data directory can be configured like this:
[mysqld]
innodb_data_file_path=ibdata1:50M;ibdata2:50M:autoextend
The autoextend and max attributes can be used only for the last data file in the innodb_data_file_path line. If 
you specify the autoextend option for the last data file, InnoDB extends the data file if it runs out of free space in the 
tablespace.
The increment is 8 MB at a time by default, To modify the increment, change the innodb_autoextend_increment
system variable.
InnoDB is not aware of the file system maximum file size, so be cautious on file systems where the maximum 
file size is a small value such as 2GB. To specify a maximum size for an auto-extending data file, use the max 
attribute following the autoextend attribute. Use the max attribute only in cases where constraining disk usage is of 
critical importance, because exceeding the maximum size causes a fatal error, possibly including a crash. The 
following configuration permits ibdata1 to grow up to a limit of 500MB.
[mysqld]
innodb_data_file_path=ibdata1:10M:autoextend:max:500M
InnoDB creates tablespace files in the MySQL data directory by default. To specify a location explicitly, use the 
innodb_data_home_dir option. For example, to use two files named ibdata1 and ibdata2 but create them in the 
/ibdata directory, configure InnoDB like this:
[mysqld]
innodb_data_home_dir = /ibdata
innodb_data_file_path=ibdata1:50M;ibdata2:50M:autoextend
Note: InnoDB does not create directories, so make sure that the /ibdata directory exists before you start the server. 
This is also true of any log file directories that you configure. Use the Unix or DOS mkdir command to create any 
neces-sary directories. Make sure that the MySQL server has the proper access rights to create files in the data 
directory. More generally, the server must have access rights in any directory where it needs to create data files or 
log files.
MySQL Database Administration
 23 
InnoDB forms the directory path for each data file by textually concatenating the value of 
innodb_data_home_dir to the data file name, adding a path name separator (slash or backslash) between values if 
necessary. If the innodb_data_home_dir option is not mentioned in my.cnf at all, the default value is the “dot” 
directory ./, which means the MySQL data directory. (The MySQL server changes its current working directory to its 
data directory when it begins executing.)
If you specify innodb_data_home_dir as an empty string, you can specify absolute paths for the data files 
listed in the innodb_data_file_path value. The following example is equivalent to the preceding one:
[mysqld]
innodb_data_home_dir =
innodb_data_file_path=/ibdata/ibdata1:50M;/ibdata/ibdata2:50M:autoextend
When you add a new file to the tablespace configuration, make sure that it does not exist. InnoDB will create 
and initialize the file when you restart the server.
Currently, you cannot remove a data file from the tablespace. To decrease the size of your tablespace, use 
this procedure:
1. Use mysqldump to dump all your InnoDB tables.
2. Stop the server.
3. Remove all the existing tablespace files, including the ibdata and ib_log files. If you want to keep a backup copy 
of the information, then copy all the ib* files to another location before the removing the files in your MySQL 
installation.
4. Remove any .frm files for InnoDB tables.
5. Configure a new tablespace.
6. Restart the server.
7. Import the dump files.
If you want to change the number or the size of your InnoDB log files, use the following instructions. The procedure 
to use depends on the value of innodb_fast_shutdown:
If innodb_fast_shutdown is not set to 2: Stop the MySQL server and make sure that it shuts down without errors (to 
ensure that there is no information for outstanding transactions in the log). Copy the old log files into a safe place in 
case something went wrong during the shutdown and you need them to recover the tablespace. Delete the old log 
files from the log file directory, edit my.cnf to change the log file configuration, and start the MySQL server again. 
mysqld sees that no InnoDB log files exist at startup and creates new ones.
If innodb_fast_shutdown is set to 2: Set innodb_fast_shutdown to 1:
mysql> SET GLOBAL innodb_fast_shutdown = 1;
Then follow the instructions in the previous item.
Determining the Maximum Memory Allocation for InnoDB:
On 32-bit GNU/Linux x86, be careful not to set memory usage too high. glibc may permit the process heap to 
grow over thread stacks, which crashes your server. It is a risk if the value of the following expression is close to or 
exceeds 2GB.
innodb_buffer_pool_size
+ key_buffer_size
+ max_connections*(sort_buffer_size+read_buffer_size+binlog_cache_size)
+ max_connections*2MB
Turning Off InnoDB:
If you do not want to use InnoDB tables, start the server with the --innodb=OFF or --skip-innodb option to disable 
the InnoDB storage engine. In this case, the server will not start if the default storage engine is set to InnoDB. Use -
-default-storage-engine to set the default to some other engine if necessary.
Using Per-Table Tablespaces:
MySQL Database Administration
 24 
You can store each InnoDB table and its indexes in its own file. This feature is called “multiple tablespaces” 
because in effect each table has its own tablespace.
To enable multiple tablespaces, start the server with the --innodb_file_per_table option. For example, add a 
line to the [mysqld] section of my.cnf.
[mysqld]
innodb_file_per_table
With multiple tablespaces enabled, InnoDB stores each newly created table into its own tbl_name.ibd file in 
the database directory where the table belongs. This is similar to what the MyISAM storage engine does, but 
MyISAM divides the table into a tbl_name.MYD data file and an tbl_name.MYI index file. For InnoDB, the data and 
the indexes are stored together in the .ibd file. The tbl_name.frm file is still created as usual.
You cannot freely move .ibd files between database directories as you can with MyISAM table files. This is 
because the table definition that is stored in the InnoDB shared tablespace includes the database name, and 
because InnoDB must preserve the consistency of transaction IDs and log sequence numbers.
If you remove the innodb_file_per_table line from my.cnf and restart the server, InnoDB creates tables inside 
the shared tablespace files again.
The --innodb_file_per_table option affects only table creation, not access to existing tables. If you start the 
server with this option, new tables are created using .ibd files, but you can still access tables that exist in the 
shared tablespace. If you start the server without this option, new tables are created in the shared tablespace, but 
you can still access any tables that were created using multiple tablespaces.
Note: InnoDB always needs the shared tablespace because it puts its internal data dictionary and undo logs there. 
The .ibd files are not sufficient for InnoDB to operate.
To move an .ibd file and the associated table from one database to another, use a RENAME TABLE 
statement:
mysql> RENAME TABLE db1.tbl_name TO db2.tbl_name;
Using Raw Devices for the Shared Tablespace:
You can use raw disk partitions as data files in the shared tablespace. By using a raw disk, you can perform 
nonbuffered I/O on Windows and on some Unix systems without file system overhead. This may improve 
performance, but you are advised to perform tests with and without raw partitions to verify whether this is actually 
so on your system.
When you create a new data file, put the keyword newraw immediately after the data file size in 
innodb_data_file_path. The partition must be at least as large as the size that you specify. Note that 1MB in InnoDB 
is 1024 × 1024 bytes, whereas 1MB in disk specifications usually means 1,000,000 bytes.
[mysqld]
innodb_data_home_dir=
innodb_data_file_path=/dev/hdd1:3Gnewraw;/dev/hdd2:2Gnewraw
The next time you start the server, InnoDB notices the newraw keyword and initializes the new partition. 
However, do not create or change any InnoDB tables yet. Otherwise, when you next restart the server, InnoDB 
reinitializes the partition and your changes are lost. (As a safety measure InnoDB prevents users from modifying 
data when any partition with newraw is specified.)
After InnoDB has initialized the new partition, stop the server, change newraw in the data file specification to raw:
[mysqld]
innodb_data_home_dir=
innodb_data_file_path=/dev/hdd1:3Graw;/dev/hdd2:2Graw
Then restart the server and InnoDB permits changes to be made.
When you use a raw disk partition, be sure that it has permissions that enable read and write access by the 
MySQL Database Administration
 25 
account used for running the MySQL server. For example, if you run the server as the mysql user, the partition must 
permit read and write access to mysql. If you run the server with the --memlock option, the server must be run as 
root, so the partition must permit access to root.
Dealing with InnoDB Initialization Problems:
If InnoDB prints an operating system error during a file operation, usually the problem has one of the following 
causes:
− You did not create the InnoDB data file directory or the InnoDB log directory.
− mysqld does not have access rights to create files in those directories.
− mysqld cannot read the proper my.cnf or my.ini option file, and consequently does not see the options 
that you specified.
− The disk is full or a disk quota is exceeded.
− You have created a subdirectory whose name is equal to a data file that you specified, so the name 
cannot be used as a file name.
− There is a syntax error in the innodb_data_home_dir or innodb_data_file_path value.
If something goes wrong when InnoDB attempts to initialize its tablespace or its log files, delete all files 
created by InnoDB. This means all ibdata files and all ib_logfile files. In case you have already created some 
InnoDB tables, delete the corresponding .frm files for these tables (and any .ibd files if you are using multiple 
tablespaces) from the MySQL database directories as well. Then you can try the InnoDB database creation again. 
It is best to start the MySQL server from a command prompt so that you see what is happening.
6.4.4. InnoDB Startup Options and System Variables
innodb
Enables the InnoDB storage engine, if the server was compiled with InnoDB support. 
innodb-status-file 
Controls whether InnoDB creates a file named innodb_status.<pid> in the MySQL data directory. If enabled, 
InnoDB periodically writes the output of SHOW ENGINE INNODB STATUS to this file. 
By default, the file is not created. To create it, start mysqld with the --innodb-status-file=1 option. The file is deleted 
during normal shutdown. 
skip-innodb
Disable the InnoDB storage engine.
innodb_additional_mem_pool_size 
The size in bytes of a memory pool InnoDB uses to store data dictionary information and other internal data 
structures. The more tables you have in your application, the more memory you need to allocate here. If InnoDB 
runs out of memory in this pool, it starts to allocate memory from the operating system, and writes warning 
messages to the MySQL error log. The default value is 1MB. 
innodb_autoextend_increment 
The increment size (in MB) for extending the size of an auto-extending shared tablespace file when it 
becomes full. The default value is 8. This variable does not affect the per-table tablespace files that are created if 
you use innodb_file_per_table=1.
innodb_buffer_pool_size 
The size in bytes of the memory buffer InnoDB uses to cache data and indexes of its tables. The default value 
is 8MB. The larger you set this value, the less disk I/O is needed to access data in tables. On a dedicated database 
server, you may set this to up to 80% of the machine physical memory size. However, do not set it too large 
because competition for physical memory might cause paging in the operating system. Also, the time to initialize 
the buffer pool is roughly proportional to its size.
innodb_data_file_path 
The paths to individual data files and their sizes. The full directory path to each data file is formed by 
concatenating innodb_data_home_dir to each path specified here. The file sizes are specified in KB, MB, or GB 
(1024MB) by appending K, M, or G to the size value. The sum of the sizes of the files must be at least 10MB. If you 
do not specify On some operating systems, files must be less than 2GB. If you do not specify 
innodb_data_file_path, the default behavior starting from 4.0 is to create a single 10MB auto-extending data file 
MySQL Database Administration
 26 
named ibdata1. Starting from 3.23.44, you can set the file size larger than 4GB on those operating systems that 
support big files. You can also use raw disk partitions as data files.
innodb_data_home_dir 
The common part of the directory path for all InnoDB data files in the shared tablespace. This setting does not 
affect the location of per-file tablespaces when innodb_file_per_table is enabled. The default value is the MySQL 
data directory. If you specify the value as an empty string, in which case you can use absolute file paths in 
innodb_data_file_path. 
innodb_file_per_table
If innodb_file_per_table is disabled (the default), InnoDB creates tables in the shared tablespace. If
innodb_file_per_table is enabled, InnoDB creates each new table using its own .ibd file for storing data and 
indexes, rather than in the shared tablespace.
innodb_flush_log_at_trx_commit 
If the value of innodb_flush_log_at_trx_commit is 0, the log buffer is written out to the log file once per second 
and the flush to disk operation is performed on the log file, but nothing is done at a transaction commit. When the 
value is 1, the log buffer is written out to the log file at each transaction commit and the flush to disk operation is 
performed on the log file. When the value is 2, the log buffer is written out to the file at each commit, but the flush to 
disk operation is not performed on it. However, the flushing on the log file takes place once per second also when 
the value is 2. Note that the once-per-second flushing is not 100% guaranteed to happen every second, due to 
process scheduling issues. 
The default value of this variable is 1 (prior to MySQL 4.0.13, the default is 0). 
A value of 1 is required for ACID compliance. You can achieve better performance by setting the value 
different from 1, but then you can lose at most one second worth of transactions in a crash. With a value of 0, any 
mysqld process crash can erase the last second of transactions. With a value of 2, then only an operating system 
crash or a power outage can erase the last second of transactions. However, InnoDB's crash recovery is not 
affected and thus crash recovery does work regardless of the value. 
For the greatest possible durability and consistency in a replication setup using InnoDB with transactions, use 
innodb_flush_log_at_trx_commit = 1 and sync_binlog = 1 in your master server my.cnf file. 
sync_binlog
If the value of this variable is greater than 0, the MySQL server synchronizes its binary log to disk after every 
sync_binlog writes to the binary log. There is one write to the binary log per statement if autocommit is enabled, 
and one write per transaction otherwise. The default value of sync_binlog is 0, which does no synchronizing to disk. 
A value of 1 is the safest choice, because in the event of a crash you lose at most one statement or transaction 
from the binary log. However, it is also the slowest choice
innodb_fast_shutdown
The InnoDB shutdown mode. By default, the value is 1, which causes a “fast” shutdown (the normal type of 
shutdown). If the value is 0, InnoDB does a full purge and an insert buffer merge before a shutdown. These 
operations can take minutes, or even hours in extreme cases. If the value is 1, InnoDB skips these operations at 
shutdown. If the value is 2, InnoDB will just flush its logs and then shut down cold, as if MySQL had crashed; no 
committed transaction will be lost, but crash recovery will be done at the next startup.
innodb_lock_wait_timeout
The timeout in seconds an InnoDB transaction may wait for a lock before being rolled back. The default is 50 
seconds. A transaction that tries to access a row that is locked by another InnoDB transaction will hang for at most 
this many seconds before issuing the following error: 
ERROR 1205 (HY000): Lock wait timeout exceeded; try restarting transaction
When a lock wait timeout occurs, the current statement is not executed. The current transaction is not rolled 
back. (To have the entire transaction roll back, start the server with the --innodb_rollback_on_timeout option, 
available as of MySQL 5.1.15.
innodb_rollback_on_timeout
In MySQL 5.1, InnoDB rolls back only the last statement on a transaction timeout by default. If --
innodb_rollback_on_timeout is specified, a transaction timeout causes InnoDB to abort and roll back the entire 
transaction. This variable was added in MySQL 5.1.15. 
innodb_log_buffer_size 
MySQL Database Administration
 27 
The size in bytes of the buffer that InnoDB uses to write to the log files on disk. The default value is 1MB. 
Sensible values range from 1MB to 8MB. A large log buffer enables large transactions to run without a need to write 
the log to disk before the transactions commit. Thus, if you have big transactions, making the log buffer larger 
saves disk I/O. 
innodb_log_file_size 
The size in bytes of each log files in a log group. The combined size of log files must be less than 4GB. The 
default value is 5MB. Sensible values range from 1MB to 1/N-th of the size of the buffer pool, where N is the 
number of log files in the group. The larger the value, the less checkpoint flush activity is needed in the buffer pool, 
saving disk I/O. But larger log files also mean that recovery is slower in case of a crash. 
innodb_log_files_in_group 
The number of log files in the log group. InnoDB writes to the files in a circular fashion. The default (and 
recommended) value is 2. 
innodb_log_group_home_dir 
The directory path to the InnoDB log files. If you do not specify any InnoDB log variables, the default is to 
create two 5MB files names ib_logfile0 and ib_logfile1 in the MySQL data directory. 
innodb_open_files 
This variable is relevant only if you use multiple tablespaces in InnoDB. It specifies the maximum number of 
.ibd files that InnoDB can keep open at one time. The minimum value is 10. The default value is 300. This variable 
is available as of MySQL 4.1.1. 
The file descriptors used for .ibd files are for InnoDB only. They are independent of those specified by the --
open-files-limit server option, and do not affect the operation of the table cache. 
innodb-safe-binlog 
If this option is given, then after a crash recovery by InnoDB, mysqld truncates the binary log after the last notrolled-back transaction in the log. The option also causes InnoDB to print an error if the binary log is smaller or 
shorter than it should be.
foreign_key_checks
If set to 1 (the default), foreign key constraints for InnoDB tables are checked. If set to 0, they are ignored. 
Disabling foreign key checking can be useful for reloading InnoDB tables in an order different from that required by 
their parent/child relationships.
Setting foreign_key_checks to 0 also affects data definition statements: DROP SCHEMA drops a schema 
even if it contains tables that have foreign keys that are referred to by tables outside the schema, and DROP 
TABLE drops tables that have foreign keys that are referred to by other tables. 
Note: Setting foreign_key_checks to 1 does not trigger a scan of the existing table data. Therefore, rows added to 
the table while foreign_key_checks = 0 will not be verified for consistency. 
innodb_commit_concurrency
The number of threads that can commit at the same time. A value of 0 (the default) permits any number of 
transactions to commit simultaneously. 
As of MySQL 5.1.36, the value of innodb_commit_concurrency cannot be changed at runtime from zero to 
nonzero or vice versa. The value can still be changed from one nonzero value to another. 
innodb_force_recovery
The crash recovery mode. Possible values are from 0 to 6. This variable should be set greater than 0 only in 
an emergency situation when you want to dump your tables from a corrupt database! As a safety measure, InnoDB 
prevents any changes to its data when this variable is greater than 0
innodb_stats_on_metadata
When this variable is enabled (which is the default, as before the variable was created), InnoDB updates 
statistics during metadata statements such as SHOW TABLE STATUS or SHOW INDEX, or when accessing the 
INFORMATION_SCHEMA tables TABLES or STATISTICS. (These updates are similar to what happens for 
ANALYZE TABLE.) When disabled, InnoDB does not updates statistics during these operations. Disabling this 
variable can improve access speed for schemas that have a large number of tables or indexes. It can also improve 
the stability of execution plans for queries that involve InnoDB tables. 
MySQL Database Administration
 28 
Creating and Using InnoDB Tables:
To create an InnoDB table, specify an ENGINE = InnoDB option in the CREATE TABLE statement:
mysql> CREATE TABLE customers (a INT, b CHAR (20), INDEX (a)) ENGINE=InnoDB;
The statement creates a table and an index on column a in the InnoDB tablespace that consists of the data 
files that you specified in my.cnf. In addition, MySQL creates a file customers.frm in the test directory under the 
MySQL database directory. Internally, InnoDB adds an entry for the table to its own data dictionary. The entry 
includes the database name. For example, if test is the database in which the customers table is created, the entry 
is for 'test/customers'. This means you can create a table of the same name customers in some other database, 
and the table names do not collide inside InnoDB.
You can query the amount of free space in the InnoDB tablespace by issuing a SHOW TABLE STATUS 
statement for any InnoDB table. The amount of free space in the tablespace appears in the Data_free section in the 
output of SHOW TABLE STATUS (or the Comment section prior to MySQL 5.1.24). For example:
mysql> SHOW TABLE STATUS FROM test LIKE 'customers'
How to Use Transactions in InnoDB with Different APIs:
By default, each client that connects to the MySQL server begins with autocommit mode enabled, which 
automatically commits every SQL statement as you execute it. To use multiple-statement transactions, you can 
switch autocommit off with the SQL statement SET autocommit = 0 and end each transaction with either COMMIT 
or ROLLBACK. If you want to leave autocommit on, you can begin your transactions within START TRANSACTION 
and end them with COMMIT or ROLLBACK. The following example shows two transactions. The first is committed; 
the second is rolled back.
shell> mysql test
mysql> CREATE TABLE customer (a INT, b CHAR (20), INDEX (a))
-> ENGINE=InnoDB;
Query OK, 0 rows affected (0.00 sec)
mysql> START TRANSACTION;
Query OK, 0 rows affected (0.00 sec)
mysql> INSERT INTO customer VALUES (10, 'Heikki');
Query OK, 1 row affected (0.00 sec)
mysql> COMMIT;
Query OK, 0 rows affected (0.00 sec)
mysql> SET autocommit=0;
Query OK, 0 rows affected (0.00 sec)
mysql> INSERT INTO customer VALUES (15, 'John');
Query OK, 1 row affected (0.00 sec)
mysql> ROLLBACK;
Query OK, 0 rows affected (0.00 sec)
mysql> SELECT * FROM customer;
+------+--------+
| a | b |
+------+--------+
| 10 | Heikki |
+------+--------+
1 row in set (0.00 sec)
mysql>
Converting Tables from Other Storage Engines to InnoDB:
To convert a non-InnoDB table to use InnoDB use ALTER TABLE:
mysql> ALTER TABLE t1 ENGINE=InnoDB;
Note: Do not convert MySQL system tables in the mysql database (such as user or host) to the InnoDB type. This 
is an unsupported operation. The system tables must always be of the MyISAM type.
MySQL Database Administration
 29 
6.4.5. InnoDB Multi-Versioning:
InnoDB is a multi-versioned storage engine: it keeps information about old versions of changed rows, to 
support transactional features such as concurrency and rollback. This information is stored in the tablespace in a 
data structure called a rollback segment (after an analogous data structure in Oracle). InnoDB uses the information 
in the rollback segment to perform the undo operations needed in a transaction rollback. It also uses the 
information to build earlier versions of a row for a consistent read. Internal Details of Multi-Versioning Internally, 
InnoDB adds three fields to each row stored in the database. A 6-byte DB_TRX_ID field indicates the transaction 
identifier for the last transaction that inserted or updated the row. Also, a deletion is treated internally as an update 
where a special bit in the row is set to mark it as deleted. Each row also contains a 7-byte DB_ROLL_PTR field 
called the roll pointer. The roll pointer points to an undo log record written to the rollback segment. If the row was 
updated, the undo log record contains the information necessary to rebuild the content of the row before it was 
updated. A 6-byte DB_ROW_ID field contains a row ID that increases monotonically as new rows are inserted. If 
InnoDB generates a clustered index automatically, the index contains row ID values. Otherwise, the DB_ROW_ID 
column does not appear in any index.
Undo logs in the rollback segment are divided into insert and update undo logs. Insert undo logs are needed 
only in transaction rollback and can be discarded as soon as the transaction commits. Update undo logs are used 
also in consistent reads, but they can be discarded only after there is no transaction present for which InnoDB has 
assigned a snapshot that in a consistent read could need the information in the update undo log to build an earlier 
version of a database row.
Guidelines for Managing Rollback Segments Commit:
your transactions regularly, including those transactions that issue only consistent reads. Otherwise, InnoDB 
cannot discard data from the update undo logs, and the rollback segment may grow too big, filling up your 
tablespace.
In the InnoDB multi-versioning scheme, a row is not physically removed from the database immediately when 
you delete it with an SQL statement. InnoDB only physically removes the corresponding row and its index records 
when it discards the update undo log record written for the deletion. This removal operation is called a purge, and it 
is quite fast, usually taking the same order of time as the SQL statement that did the deletion.
Clustered and Secondary Indexes:
Every InnoDB table has a special index called the clustered index where the data for the rows is stored:
If you define a PRIMARY KEY on your table, InnoDB uses it as the clustered index.
If you do not define a PRIMARY KEY for your table, MySQL picks the first UNIQUE index that has only 
NOT NULL columns as the primary key and InnoDB uses it as the clustered index.
If the table has no PRIMARY KEY or suitable UNIQUE index, InnoDB internally generates a hidden clustered 
index on a synthetic column containing row ID values. The rows are ordered by the ID that InnoDB assigns to the 
rows in such a table. The row ID is a 6-byte field that increases monotonically as new rows are inserted. Thus, the 
rows ordered by the row ID are physically in insertion order.
Accessing a row through the clustered index is fast because the row data is on the same page where the 
index search leads. If a table is large, the clustered index architecture often saves a disk I/O operation when 
compared to storage organizations that store row data using a different page from the index record. (For example, 
MyISAM uses one file for data rows and another for index records.)
In InnoDB, the records in nonclustered indexes (also called secondary indexes) contain the primary key 
columns for the row that are not in the secondary index. InnoDB uses this primary key value to search for the row in 
the clustered index. If the primary key is long, the secondary indexes use more space, so it is advantageous to 
have a short primary key.
6.4.6. InnoDB Isolation Levels:
In the InnoDB transaction model, the goal is to combine the best properties of a multi-versioning database 
with traditional two-phase locking. InnoDB does locking on the row level and runs queries as nonlocking consistent 
reads by default, in the style of Oracle. The lock table in InnoDB is stored so space-efficiently that lock escalation is 
not needed: Typically, several users are permitted to lock every row in InnoDB tables, or any random subset of the 
rows, without causing InnoDB memory exhaustion. 
In InnoDB, all user activity occurs inside a transaction. If autocommit mode is enabled, each SQL statement 
MySQL Database Administration
 30 
forms a single transaction on its own. By default, MySQL starts the session for each new connection with 
autocommit enabled, so MySQL does a commit after each SQL statement if that statement did not return an error. If 
a statement returns an error, the commit or rollback behavior depends on the error.
A session that has autocommit enabled can perform a multiple-statement transaction by starting it with an explicit 
START TRANSACTION or BEGIN statement and ending it with a COMMIT or ROLLBACK statement.
If autocommit mode is disabled within a session with SET autocommit = 0, the session always has a transaction 
open. A COMMIT or ROLLBACK statement ends the current transaction and a new one starts. 
Syntax:
SET [GLOBAL | SESSION] TRANSACTION ISOLATION LEVEL
 {
 READ UNCOMMITTED
 | READ COMMITTED
 | REPEATABLE READ
 | SERIALIZABLE
 }
With the GLOBAL keyword, the statement sets the default transaction level globally for all subsequent sessions. 
Existing sessions are unaffected. 
With the SESSION keyword, the statement sets the default transaction level for all subsequent transactions 
performed within the current session. 
Without any SESSION or GLOBAL keyword, the statement sets the isolation level for the next (not started) 
transaction performed within the current session. 
A change to the global default isolation level requires the SUPER privilege. Any session is free to change its 
session isolation level (even in the middle of a transaction), or the isolation level for its next transaction. 
The following list describes how MySQL supports the different transaction levels: 
READ UNCOMMITTED: SELECT statements are performed in a nonlocking fashion, but a possible earlier version 
of a row might be used. Thus, using this isolation level, such reads are not consistent. This is also called a “dirty 
read.
READ COMMITTED: Read committed guarantees that any data read was committed at the moment is read. It 
simply restricts the reader from seeing any intermediate, uncommitted, 'dirty' read. IT makes no promise 
whatsoever that if the transaction re-issues the read, will find the Same data, data is free to change after it was 
read.
REPEATABLE READ: Repeatable read is a higher isolation level, that in addition to the guarantees of the read 
committed level, it also guarantees that any data read cannot change, if the transaction reads the same data again, 
it will find the previously read data in place, unchanged, and available to read.
SERIALIZABLE: serializable, makes an even stronger guarantee: in addition to everything repeatable read 
guarantees, it also guarantees that no new data can be seen by a subsequent read.
Say you have a table T with a column C with one row in it, say it has the value '1'. And consider you have a simple 
task like following:
BEGIN TRANSACTION;
SELECT * FROM T;
WAITFOR DELAY '00:01:00'
SELECT * FROM T;
COMMIT;
That is a simple task that issue two reads from table T, with a delay of 1 minute between them.
− under READ COMITTED, the second SELECT may return any data. A concurrent transaction may 
update the record, delete it, insert new records. The second select will always see the new data.
− under REPEATABLE READ the second SELECT is guaranteed to see the rows that has seen at first 
MySQL Database Administration
 31 
select unchanged. New rows may be added by a concurrent transaction in that one minute, but the 
existing rows cannot be deleted nor changed.
− under SERIALIZABLE reads the second select is guaranteed to see exactly the same rows as the first. 
No row can change, nor deleted, nor new rows could be inserted by a concurrent transaction.
6.4.7. InnoDB Lock Modes:
InnoDB implements standard row-level locking where there are two types of locks: 
1.A shared (S) lock permits a transaction to read a row.
2.An exclusive (X) lock permits a transaction to update or delete a row.
If transaction T1 holds a shared (S) lock on row r, then requests from some distinct transaction T2 for a lock on row 
r are handled as follows: 
1.A request by T2 for an S lock can be granted immediately. As a result, both T1 and T2 hold an S lock on r.
2.A request by T2 for an X lock cannot be granted immediately. 
If a transaction T1 holds an exclusive (X) lock on row r, a request from some distinct transaction T2 for a lock 
of either type on r cannot be granted immediately. Instead, transaction T2 has to wait for transaction T1 to release 
its lock on row r.
In addition InnoDB supports two types of locking reads: 
− SELECT ... LOCK IN SHARE MODE sets a shared mode lock on the rows read. A shared mode lock enables 
other sessions to read the rows but not to modify them. The rows read are the latest available, so if they 
belong to another transaction that has not yet committed, the read blocks until that transaction ends.
− SELECT ... FOR UPDATE blocks other sessions from doing SELECT ... LOCK IN SHARE MODE or from 
reading in certain transaction isolation levels. Consistent reads will ignore any locks set on the records that 
exist in the read view.
Locks set by LOCK IN SHARE MODE and FOR UPDATE reads are released when the transaction is committed or 
rolled back. 
As an example of a situation in which a locking read is useful, suppose that you want to insert a new row into a 
table child, and make sure that the child row has a parent row in table parent. The following discussion describes 
how to implement referential integrity in application code. 
Suppose that you use a consistent read to read the table parent and indeed see the parent row of the to-beinserted child row in the table. Can you safely insert the child row to table child? No, because it is possible for some 
other session to delete the parent row from the table parent in the meantime without you being aware of it. 
The solution is to perform the SELECT in a locking mode using LOCK IN SHARE MODE: 
mysql> SELECT * FROM parent WHERE NAME = 'Jones' LOCK IN SHARE MODE;
A read performed with LOCK IN SHARE MODE reads the latest available data and sets a shared mode lock on the 
rows read. A shared mode lock prevents others from updating or deleting the row read. Also, if the latest data 
belongs to a yet uncommitted transaction of another session, we wait until that transaction ends. After we see that 
the LOCK IN SHARE MODE query returns the parent 'Jones', we can safely add the child record to the child table 
and commit our transaction. 
Defragmenting a Table:
If there are random insertions into or deletions from the indexes of a table, the indexes may become 
fragmented. Fragmentation means that the physical ordering of the index pages on the disk is not close to the 
index ordering of the records on the pages, or that there are many unused pages in the 64-page blocks that were 
allocated to the index.
One symptom of fragmentation is that a table takes more space than it “should” take. How much that is 
exactly, is difficult to determine. All InnoDB data and indexes are stored in B-trees, and their fill factor may vary from 
50% to 100%. Another symptom of fragmentation is that a table scan such as this takes more time than it “should” 
take:
mysql> SELECT COUNT(*) FROM t WHERE a_non_indexed_column <> 12345;
MySQL Database Administration
 32 
(In the preceding query, we are “fooling” the SQL optimizer into scanning the clustered index rather than a 
secondary index.) Most disks can read 10MB/s to 50MB/s, which can be used to estimate how fast a table scan 
should be.
It can speed up index scans if you periodically perform a “null” ALTER TABLE operation, which causes MySQL 
to rebuild the table: 
mysql> ALTER TABLE tbl_name ENGINE=INNODB;
Another way to perform a defragmentation operation is to use mysqldump to dump the table to a text file, drop 
the table, and reload it from the dump file.
If the insertions into an index are always ascending and records are deleted only from the end, the InnoDB 
filespace management algorithm guarantees that fragmentation in the index does not occur.
6.4.8. InnoDB Error Handling
Error handling in InnoDB is not always the same as specified in the SQL standard. According to the standard, 
any error during an SQL statement should cause rollback of that statement. InnoDB sometimes rolls back only part 
of the statement, or the whole transaction. The following items describe how InnoDB performs error handling:
− If you run out of file space in the tablespace, a MySQL Table is full error occurs and InnoDB rolls back 
the SQL statement.
− A transaction deadlock causes InnoDB to roll back the entire transaction. Retry the whole transaction 
when this happens.
− A duplicate-key error rolls back the SQL statement, if you have not specified the IGNORE option in 
your statement.
During implicit rollbacks, as well as during the execution of an explicit ROLLBACK SQL statement, SHOW 
PROCESSLIST displays Rolling back in the State column for the relevant connection.
InnoDB Error Codes:
1005 (ER_CANT_CREATE_TABLE)
Cannot create table. If the error message refers to error 150, table creation failed because a foreign key constraint 
was not correctly formed. If the error message refers to error –1, table creation probably failed because the table 
includes a column name that matched the name of an internal InnoDB table.
1016 (ER_CANT_OPEN_FILE)
Cannot find the InnoDB table from the InnoDB data files, although the .frm file for the table exists.
1114 (ER_RECORD_FILE_FULL)
InnoDB has run out of free space in the tablespace. Reconfigure the tablespace to add a new data file.
1205 (ER_LOCK_WAIT_TIMEOUT)
Lock wait timeout expired. Transaction was rolled back.
1216 (ER_NO_REFERENCED_ROW)
You are trying to add a row but there is no parent row, and a foreign key constraint fails. Add the parent row first.
1217 (ER_ROW_IS_REFERENCED)
You are trying to delete a parent row that has children, and a foreign key constraint fails. Delete the children first.
6.4.9. InnoDB Performance Tuning and Troubleshooting
− innodb_buffer_pool_size specifies the size of the buffer pool. If your buffer pool is small and you have 
sufficient memory, making the pool larger can improve performance by reducing the amount of disk I/O 
needed as queries access InnoDB tables.
− Beware of big rollbacks of mass inserts: InnoDB uses the insert buffer to save disk I/O in inserts, but no 
such mechanism is used in a corresponding rollback. A disk-bound rollback can take 30 times as long 
to perform as the corresponding insert. Killing the database process does not help because the 
rollback starts again on server startup. The only way to get rid of a runaway rollback is to increase the 
buffer pool so that the rollback becomes CPU-bound and runs fast, or to use a special procedure.
MySQL Database Administration
 33 
− Beware also of other big disk-bound operations. Use DROP TABLE and CREATE TABLE to empty a 
table, not DELETE FROM tbl_name.
− Place tablespaces in different locations.
− Make your log files big, even as big as the buffer pool. When InnoDB has written the log files full, it 
must write the modified contents of the buffer pool to disk in a checkpoint. Small log files cause many 
unnecessary disk writes. The disadvantage of big log files is that the recovery time is longer.
− When importing data into InnoDB, make sure that MySQL does not have autocommit mode enabled 
because that requires a log flush to disk for every insert. To disable autocommit during your import 
operation, surround it with SET autocommit and COMMIT statements:
SET autocommit=0;
... SQL import statements ...
 COMMIT;
− If you have UNIQUE constraints on secondary keys, you can speed up table imports by temporarily 
turning off the uniqueness checks during the import session:
SET unique_checks=0;
... SQL import statements ...
SET unique_checks=1;
− If you have FOREIGN KEY constraints in your tables, you can speed up table imports by turning the 
foreign key checks off for the duration of the import session:
SET foreign_key_checks=0;
... SQL import statements ...
SET foreign_key_checks=1;
− Use the multiple-row INSERT syntax to reduce communication overhead between the client and the 
server if you need to insert many rows:
mysql> INSERT INTO yourtable VALUES (1,2), (5,5), ...;
This tip is valid for inserts into any table, not just InnoDB tables.
SHOW ENGINE INNODB STATUS and the InnoDB Monitors:
InnoDB Monitors provide information about the InnoDB internal state. This information is useful for 
performance tuning. Each Monitor can be enabled by creating a table with a special name, which causes InnoDB to 
write Monitor output periodically. Also, output for the standard InnoDB Monitor is available on demand through the 
SHOW ENGINE INNODB STATUS SQL statement.
There are several types of InnoDB Monitors:
1.TRANSACTIONS
2.BACKGROUND THREAD
3.BUFFER POOL AND MEMORY
4.ROW OPERATIONS
5.About Log Files
6.FILE I/O
TRANSACTIONS
If this section reports lock waits, your applications might have lock contention. The output can also help to trace the 
reasons for transaction deadlocks.
BACKGROUND THREAD
The srv_master_thread lines shows work done by the main background thread. This section is displayed only by 
InnoDB Plugin.
BUFFER POOL AND MEMORY
This section gives you statistics on pages read and written. You can calculate from these numbers how many data 
file I/O operations your queries currently are doing.
ROW OPERATIONS
MySQL Database Administration
 34 
This section shows what the main thread is doing, including the number and performance rate for each type of row 
operation.
About LOG Files
This section displays information about the InnoDB log. The contents include the current log sequence number, 
how far the log has been flushed to disk, and the position at which InnoDB last took a checkpoint.
FILE I/O
This section provides information about threads that InnoDB uses to perform various types of I/O. The first few of 
these are dedicated to general InnoDB processing. The contents also display information for pending I/O 
operations and statistics for I/O performance.
6.4.10. Restrictions on InnoDB Tables:
Do not convert MySQL system tables in the mysql database from MyISAM to InnoDB tables! This is an 
unsupported operation. If you do this, MySQL does not restart until you restore the old system tables from a backup 
or regenerate them with the mysql_install_db script.
Maximums and Minimums:
− A table cannot contain more than 1000 columns.
− The InnoDB internal maximum key length is 3500 bytes, but MySQL itself restricts this to 3072 bytes.
− The combined size of the InnoDB log files must be less than 4GB.
− The minimum tablespace size is 10MB. The maximum tablespace size is 64TB. This is also the 
maximum size for a table.
6.5. The MERGE Storage Engine
The MERGE storage engine, also known as the MRG_MyISAM engine, is a collection of identical MyISAM 
tables that can be used as one. “Identical” means that all tables have identical column and index information. You 
cannot merge MyISAM tables in which the columns are listed in a different order, do not have exactly the same 
columns, or have the indexes in different order.
An alternative to a MERGE table is a partitioned table, which stores partitions of a single table in separate 
files. Partitioning enables some operations to be performed more efficiently and is not limited to the MyISAM 
storage engine.
When you create a MERGE table, MySQL creates two files on disk. The files have names that begin with the 
table name and have an extension to indicate the file type. An .frm file stores the table format, and an .MRG file 
contains the names of the underlying MyISAM tables that should be used as one. The tables do not have to be in 
the same database as the MERGE table.
You can use SELECT, DELETE, UPDATE, and INSERT on MERGE tables. You must have SELECT, 
DELETE, and UPDATE privileges on the MyISAM tables that you map to a MERGE table.
Note: The use of MERGE tables entails the following security issue: If a user has access to MyISAM table t, that 
user can create a MERGE table m that accesses t. However, if the user's privileges on t are subsequently revoked, 
the user can continue to access t by doing so through m.
Use of DROP TABLE with a MERGE table drops only the MERGE specification. The underlying tables are not 
affected.
To create a MERGE table, you must specify a UNION=(list-of-tables) option that indicates which MyISAM 
tables to use. You can optionally specify an INSERT_METHOD option to control how inserts into the MERGE table 
take place. Use a value of FIRST or LAST to cause inserts to be made in the first or last underlying table, 
respectively. If you specify no INSERT_METHOD option or if you specify it with a value of NO, inserts into the 
MERGE table are not permitted and attempts to do so result in an error.
The following example shows how to create a MERGE table:
mysql> CREATE TABLE t1 (
-> a INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
-> message CHAR(20)) ENGINE=MyISAM;
MySQL Database Administration
 35 
mysql> CREATE TABLE t2 (
-> a INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
-> message CHAR(20)) ENGINE=MyISAM;
mysql> INSERT INTO t1 (message) VALUES ('Testing'),('table'),('t1');
mysql> INSERT INTO t2 (message) VALUES ('Testing'),('table'),('t2');
mysql> CREATE TABLE total (
-> a INT NOT NULL AUTO_INCREMENT,
-> message CHAR(20), INDEX(a))
-> ENGINE=MERGE UNION=(t1,t2) INSERT_METHOD=LAST;
Note that column a is indexed as a PRIMARY KEY in the underlying MyISAM tables, but not in the MERGE 
table. There it is indexed but not as a PRIMARY KEY because a MERGE table cannot enforce uniqueness over the 
set of underlying tables. (Similarly, a column with a UNIQUE index in the underlying tables should be indexed in the 
MERGE table but not as a UNIQUE index.)
After creating the MERGE table, you can use it to issue queries that operate on the group of tables as a whole:
mysql> SELECT * FROM total;
+---+---------+
| a | message |
+---+---------+
| 1 | Testing |
| 2 | table |
| 3 | t1 |
| 1 | Testing |
| 2 | table |
| 3 | t2 |
+---+---------+
To remap a MERGE table to a different collection of MyISAM tables, you can use one of the following 
methods:
− DROP the MERGE table and re-create it.
− Use ALTER TABLE tbl_name UNION=(...) to change the list of underlying tables.
Beginning with MySQL 5.1.24, it is also possible to use ALTER TABLE ... UNION=() (that is, with an empty 
UNION clause) to remove all of the underlying tables.
MERGE TABLE Limitations:
− The underlying table and the MERGE table must have the same number of columns.
If you ALTER the MERGE table and add a column and after that if your trying to fetch the table you will get the 
below error.
Unable to open underlying table which is differently defined or of non-MyISAM type or doesn't exist
− The column order in the underlying table and the MERGE table must match.
− The column type in the underlying table and the MERGE table must be equal.
− The column length in the underlying table and the MERGE table must be equal.
Unable to open underlying table which is differently defined or of non-MyISAM type or doesn't exist
− The underlying table may have more indexes than the MERGE table, but cannot have fewer.
− The index type of the underlying table and the MERGE table must be the same.
− The number of index parts (that is, multiple columns within a compound index) in the index definition 
for the underlying table and the MERGE table must be the same.
MERGE Table Advantages and Disadvantages:
MERGE tables can help you solve the following problems:
− Obtain more speed. You can split a large read-only table based on some criteria, and then put 
individual tables on different disks. A MERGE table structured this way could be much faster than using 
a single large table.
MySQL Database Administration
 36 
− Perform more efficient searches. If you know exactly what you are looking for, you can search in just 
one of the underlying tables for some queries and use a MERGE table for others. You can even have 
many different MERGE tables that use overlapping sets of tables.
− Perform more efficient repairs. It is easier to repair individual smaller tables that are mapped to a 
MERGE table than to repair a single large table.
− Exceed the file size limit for the operating system. Each MyISAM table is bound by this limit, but a 
collection of MyISAM tables is not.
− You can create an alias or synonym for a MyISAM table by defining a MERGE table that maps to that 
single table. There should be no really notable performance impact from doing this
The disadvantages of MERGE tables are:
− You can use only identical MyISAM tables for a MERGE table.
− Some MyISAM features are unavailable in MERGE tables. For example, you cannot create FULLTEXT 
indexes on MERGE tables. (You can create FULLTEXT indexes on the underlying MyISAM tables, but 
you cannot search the MERGE table with a full-text search.)
− Index reads are slower. When you read an index, the MERGE storage engine needs to issue a read on 
all underlying tables to check which one most closely matches a given index value. To read the next 
index value, the MERGE storage engine needs to search the read buffers to find the next value. Only 
when one index buffer is used up does the storage engine need to read the next index block.
6.6. MERGE Table Problems:
− If you use ALTER TABLE to change a MERGE table to another storage engine, the mapping to the 
underlying tables is lost. Instead, the rows from the underlying MyISAM tables are copied into the 
altered table, which then uses the specified storage engine.
− The INSERT_METHOD table option for a MERGE table indicates which underlying MyISAM table to 
use for inserts into the MERGE table. However, use of the AUTO_INCREMENT table option for that 
MyISAM table has no effect for inserts into the MERGE table until at least one row has been inserted 
directly into the MyISAM table.
− A MERGE table cannot maintain uniqueness constraints over the entire table. When you perform an 
INSERT, the data goes into the first or last MyISAM table (as determined by the INSERT_METHOD 
option). MySQL ensures that unique key values remain unique within that MyISAM table, but not over 
all the underlying tables in the collection.
The MEMORY Storage Engine:
The MEMORY storage engine creates tables with contents that are stored in memory. Formerly, these were 
known as HEAP tables. MEMORY is the preferred term, although HEAP remains supported for backward 
compatibility.
However, MEMORY performance is constrained by contention resulting from single-thread execution and 
table lock overhead when processing updates. This limits scalability when load increases, particularly for statement 
mixes that include writes. Also, MEMORY does not preserve table contents across server restarts.
To specify that you want to create a MEMORY table, indicate that with an ENGINE table option: 
mysql> CREATE TABLE t (i INT) ENGINE = MEMORY;
As indicated by the engine name, MEMORY tables are stored in memory. They use hash indexes by default, 
which makes them very fast, and very useful for creating temporary tables. However, when the server shuts down, 
all rows stored in MEMORY tables are lost. The tables themselves continue to exist because their definitions are 
stored in .frm files on disk, but they are empty when the server restarts. 
MEMORY tables have the following characteristics:
− Space for MEMORY tables is allocated in small blocks. Tables use 100% dynamic hashing for inserts. 
No overflow area or extra key space is needed. No extra space is needed for free lists. Deleted rows 
are put in a linked list and are reused when you insert new data into the table. MEMORY tables also 
have none of the problems commonly associated with deletes plus inserts in hashed tables.
− MEMORY tables can have up to 64 indexes per table, 16 columns per index and a maximum key 
MySQL Database Administration
 37 
length of 3072 bytes.
− MEMORY tables use a fixed-length row-storage format. Variable-length types such as VARCHAR are 
stored using a fixed length.
− MEMORY tables cannot contain BLOB or TEXT columns.
− Non-TEMPORARY MEMORY tables are shared among all clients, just like any other nonTEMPORARY table.
− MEMORY table contents are stored in memory, which is a property that MEMORY tables share with 
internal temporary tables that the server creates on the fly while processing queries. However, the two 
types of tables differ in that MEMORY tables are not subject to storage conversion.
− MEMORY tables are never converted to disk tables. If an internal temporary table becomes too large, 
the server automatically converts it to on-disk storage.
− The maximum size of MEMORY tables is limited by the max_heap_table_size system variable, which 
has a default value of 16MB. To have larger (or smaller) MEMORY tables, you must change the value 
of this variable. The value in effect for CREATE TABLE is the value used for the life of the table. (If you 
use ALTER TABLE or TRUNCATE TABLE, the value in effect at that time becomes the new maximum 
size for the table. A server restart also sets the maximum size of existing MEMORY tables to the global 
max_heap_table_size value.)
− The server needs sufficient memory to maintain all MEMORY tables that are in use at the same time.
− Memory is not reclaimed if you delete individual rows from a MEMORY table. Memory is reclaimed only 
when the entire table is deleted. Memory that was previously used for rows that have been deleted will 
be re-used for new rows only within the same table. To free up the memory used by rows that have 
been deleted, use ALTER TABLE ENGINE=MEMORY to force a table rebuild.
− As mentioned earlier, the max_heap_table_size system variable sets the limit on the maximum size of 
MEMORY tables. To control the maximum size for individual tables, set the session value of this 
variable before creating each table. (Do not change the global max_heap_table_size value unless you 
intend the value to be used for MEMORY tables created by all clients.) The following
 example creates two MEMORY tables, with a maximum size of 1MB and 2MB, respectively:
mysql> SET max_heap_table_size = 1024*1024;
Query OK, 0 rows affected (0.00 sec)
mysql> CREATE TABLE t1 (id INT, UNIQUE(id)) ENGINE = MEMORY;
Query OK, 0 rows affected (0.01 sec)
mysql> SET max_heap_table_size = 1024*1024*2;
Query OK, 0 rows affected (0.00 sec)
mysql> CREATE TABLE t2 (id INT, UNIQUE(id)) ENGINE = MEMORY;
Query OK, 0 rows affected (0.00 sec)
 Both tables will revert to the server's global max_heap_table_size value if the server restarts.
You can also specify a MAX_ROWS table option in CREATE TABLE statements for MEMORY tables to 
provide a hint about the number of rows you plan to store in them. This does not enable the table to grow beyond 
the max_heap_table_size value, which still acts as a constraint on maximum table size. For maximum flexibility in 
being able to use MAX_ROWS, set max_heap_table_size at least as high as the value to which you want each 
MEMORY table to be able to grow.
6.7. The EXAMPLE Storage Engine
MySQL Database Administration
 38 
The EXAMPLE storage engine is a stub engine that does nothing. Its purpose is to serve as an example in the 
MySQL source code that illustrates how to begin writing new storage engines. As such, it is primarily of interest to 
developers.
To enable the EXAMPLE storage engine if you build MySQL from source, invoke configure with the -
-with-example-storage-engine option.
To examine the source for the EXAMPLE engine, look in the storage/example directory of a MySQL source 
distribution.
When you create an EXAMPLE table, the server creates a table format file in the database directory. The file 
begins with the table name and has an .frm extension. No other files are created. No data can be stored into the 
table. Retrievals return an empty result.
mysql> CREATE TABLE test (i INT) ENGINE = EXAMPLE;
Query OK, 0 rows affected (0.78 sec)
mysql> INSERT INTO test VALUES(1),(2),(3);
ERROR 1031 (HY000): Table storage engine for 'test' doesn't »
have this option
mysql> SELECT * FROM test;
Empty set (0.31 sec)
The EXAMPLE storage engine does not support indexing.
6.8. The FEDERATED Storage Engine
The FEDERATED storage engine enables data to be accessed from a remote MySQL database on a local 
server without using replication or cluster technology. When using a FEDERATED table, queries on the local server 
are automatically executed on the remote (federated) tables. No data is stored on the local tables.
To include the FEDERATED storage engine if you build MySQL from source, invoke configure with the -
-with-federated-storage-engine option.
Beginning with MySQL 5.1.26, the FEDERATED storage engine is not enabled by default in the running 
server; to enable FEDERATED, you must start the MySQL server binary using the --federated option.
To examine the source for the FEDERATED engine, look in the storage/federated directory of a MySQL 
source distribution.
6.8.1 FEDERATED Storage Engine Overview:
When you create a table using one of the standard storage engines (such as MyISAM, CSV or InnoDB), the 
table consists of the table definition and the associated data. When you create a FEDERATED table, the table 
definition is the same, but the physical storage of the data is handled on a remote server.
A FEDERATED table consists of two elements:
− A remote server with a database table, which in turn consists of the table definition (stored in the .frm 
file) and the associated table. The table type of the remote table may be any type supported by the 
remote mysqld server, including MyISAM or InnoDB.
− A local server with a database table, where the table definition matches that of the corresponding table 
on the remote server. The table definition is stored within the .frm file. However, there is no data file on 
the local server. Instead, the table definition includes a connection string that points to the remote table.
When executing queries and statements on a FEDERATED table on the local server, the operations that 
would normally insert, update or delete information from a local data file are instead sent to the remote server for 
execution, where they update the data file on the remote server or return matching rows from the remote server.
The basic structure of a FEDERATED table setup is shown below:
MySQL Database Administration
 39 
1.The storage engine looks through each column that the FEDERATED table has and constructs an 
appropriate SQL statement that refers to the remote table.
2.The statement is sent to the remote server using the MySQL client API.
3.The remote server processes the statement and the local server retrieves any result that the statement 
produces (an affectedrows count or a result set).
4.If the statement produces a result set, each column is converted to internal storage engine format that the 
FEDERATED engine expects and can use to display the result to the client that issued the original 
statement. The local server communicates with the remote server using MySQL client C API functions.
6.8.2. How to Create FEDERATED Tables:
To create a FEDERATED table you should follow these steps:
− Create the table on the remote server. Alternatively, make a note of the table definition of an existing 
table, perhaps using the SHOW CREATE TABLE statement.
− Create the table on the local server with an identical table definition, but adding the connection 
information that links the local table to the remote table.
For example, you could create the following table on the remote server:
CREATE TABLE test_table (
id INT(20) NOT NULL AUTO_INCREMENT,
name VARCHAR(32) NOT NULL DEFAULT '',
other INT(20) NOT NULL DEFAULT '0',
PRIMARY KEY (id),
INDEX name (name)
)
ENGINE=MyISAM;
To create the local table that will be federated to the remote table, there are two options available. You can 
either create the local table and specify the connection string (containing the server name, login, password) to be 
used to connect to the remote table using the CONNECTION, or you can use an existing connection that you have 
previously created using the CREATE SERVER statement.
To use the first method, you must specify the CONNECTION string after the engine type in a CREATE TABLE 
statement. For example:
CREATE TABLE federated_table (
id INT(20) NOT NULL AUTO_INCREMENT,
name VARCHAR(32) NOT NULL DEFAULT '',
other INT(20) NOT NULL DEFAULT '0',
MySQL Database Administration
 40 
PRIMARY KEY (id),
INDEX name (name) 
)
ENGINE=FEDERATED
CONNECTION='mysql://fed_user@remote_host:9306/federated/test_table';
The CONNECTION string contains the information required to connect to the remote server containing the 
table that will be used to physically store the data. The connection string specifies the server name, login 
credentials, port number and database/table information. In the example, the remote table is on the server 
remote_host, using port 9306. The name and port number should match the host name (or IP address) and port 
number of the remote MySQL server instance you want to use as your remote table.
The format of the connection string is as follows:
scheme://user_name[:password]@host_name[:port_num]/db_name/tbl_name
Where:
− scheme: A recognized connection protocol. Only mysql is supported as the scheme value at this point.
− user_name: The user name for the connection. This user must have been created on the remote 
server, and must have suitable privileges to perform the required actions (SELECT, INSERT, UPDATE,
and so forth) on the remote table.
− password: (Optional) The corresponding password for user_name.
− host_name: The host name or IP address of the remote server.
− port_num: (Optional) The port number for the remote server. The default is 3306.
− db_name: The name of the database holding the remote table.
− tbl_name: The name of the remote table. The name of the local and the remote table do not have to 
match.
Creating a FEDERATED Table Using CREATE SERVER:
If you are creating a number of FEDERATED tables on the same server, or if you want to simplify the process 
of creating FEDERATED tables, you can use the CREATE SERVER statement to define the server connection 
parameters, just as you would with the CONNECTION string.
The format of the CREATE SERVER statement is:
CREATE SERVER
server_name
FOREIGN DATA WRAPPER wrapper_name
OPTIONS (option [, option] ...)
The server_name is used in the connection string when creating a new FEDERATED table. 
For example, to create a server connection identical to the CONNECTION string:
CONNECTION='mysql://fed_user@remote_host:9306/federated/test_table';
You would use the following statement:
CREATE SERVER fedlink
FOREIGN DATA WRAPPER mysql
OPTIONS (USER 'fed_user', HOST 'remote_host', PORT 9306, DATABASE 'federated');
To create a FEDERATED table that uses this connection, you still use the CONNECTION keyword, but specify 
the name you used in the CREATE SERVER statement.
CREATE TABLE test_table (
MySQL Database Administration
 41 
id INT(20) NOT NULL AUTO_INCREMENT,
name VARCHAR(32) NOT NULL DEFAULT '',
other INT(20) NOT NULL DEFAULT '0',
PRIMARY KEY (id),
INDEX name (name)
)
ENGINE=FEDERATED
CONNECTION='fedlink/test_table';
The connection name in this example contains the name of the connection (fedlink) and the name of the table 
(test_table) to link to, separated by a slash. If you specify only the connection name without a table name, the table 
name of the local table is used instead.
6.8.3. FEDERATED Storage Engine Notes and Tips
You should be aware of the following points when using the FEDERATED storage engine:
− The remote table that a FEDERATED table points to must exist before you try to access the table 
through the FEDERATED table.
− It is possible for one FEDERATED table to point to another, but you must be careful not to create a 
loop.
− The FEDERATED storage engine supports SELECT, INSERT, UPDATE, DELETE, TRUNCATE 
TABLE, and indexes. It does not support ALTER TABLE, or any Data Definition Language statements 
that directly affect the structure of the table, other than DROP TABLE.
− Transactions are not supported.
− There is no way for the FEDERATED engine to know if the remote table has changed.
− Any DROP TABLE statement issued against a FEDERATED table drops only the local table, not the 
remote table.
6.9. The ARCHIVE Storage Engine
The ARCHIVE storage engine is used for storing large amounts of data without indexes in a very small 
footprint.
The ARCHIVE storage engine is included in MySQL binary distributions. To enable this storage engine if you 
build MySQL from source, invoke configure with the --with-archive-storage-engine option.
To examine the source for the ARCHIVE engine, look in the storage/archive directory of a MySQL source 
distribution.
When you create an ARCHIVE table, the server creates a table format file in the database directory. The file 
begins with the table name and has an .frm extension. The data file has an extension of .ARZ. (Prior to MySQL 
5.1.15, a metadata file with an extension of .ARM is created as well.) An .ARN file may appear during optimization 
operations.
The ARCHIVE engine supports INSERT and SELECT, but not DELETE, REPLACE, or UPDATE. It does 
support ORDER BY operations. The ARCHIVE engine uses row-level locking. 
As of MySQL 5.1.6, the ARCHIVE engine supports the AUTO_INCREMENT column attribute. Attempting to 
create an index on any other column results in an error.
Storage: Rows are compressed as they are inserted. The ARCHIVE engine uses zlib lossless data compression 
(see http:// www.zlib.net/). You can use OPTIMIZE TABLE to analyze the table and pack it into a smaller format (for 
a reason to use OPTIMIZE TABLE, see later in this section). The engine also supports CHECK TABLE. There are 
several types of insertions that are used:
− An INSERT statement just pushes rows into a compression buffer, and that buffer flushes as 
necessary. The insertion into the buffer is protected by a lock. A SELECT forces a flush to occur, unless 
MySQL Database Administration
 42 
the only insertions that have come in were INSERT DELAYED (those flush as necessary)
Retrieval: On retrieval, rows are uncompressed on demand; there is no row cache. A SELECT operation performs 
a complete table scan: When a SELECT occurs, it finds out how many rows are currently available and reads that 
number of rows. SELECT is performed as a consistent read. Note that lots of SELECT statements during insertion 
can deteriorate the compression, unless only bulk or delayed inserts are used. To achieve better compression, you 
can use OPTIMIZE TABLE or REPAIR TABLE. The number of rows in ARCHIVE tables reported by SHOW TABLE
STATUS is always accurate.
6.10. The CSV Storage Engine
The CSV storage engine stores data in text files using comma-separated values format. To enable the CSV 
storage engine if you build MySQL from source, invoke configure with the --with-csv-storage-engine option. To 
examine the source for the CSV engine, look in the storage/csv directory of a MySQL source distribution.
When you create a CSV table, the server creates a table format file in the database directory. The file begins 
with the table name and has an .frm extension. The storage engine also creates a data file. Its name begins with 
the table name and has a .CSV extension. The data file is a plain text file. When you store data into the table, the 
storage engine saves it into the data file in commaseparated values format.
mysql> CREATE TABLE test (i INT NOT NULL, c CHAR(10) NOT NULL)
-> ENGINE = CSV;
Query OK, 0 rows affected (0.12 sec)
mysql> INSERT INTO test VALUES(1,'record one'),(2,'record two');
Query OK, 2 rows affected (0.00 sec)
Records: 2 Duplicates: 0 Warnings: 0
mysql> SELECT * FROM test;
+------+------------+
| i | c |
+------+------------+
| 1 | record one |
| 2 | record two |
+------+------------+
2 rows in set (0.00 sec)
Starting with MySQL 5.1.9, creating a CSV table also creates a corresponding Metafile that stores the state of 
the table and the number of rows that exist in the table. The name of this file is the same as the name of the table 
with the extension CSM. 
If you examine the test.CSV file in the database directory created by executing the preceding statements, its 
contents should look like this:
"1","record one"
"2","record two"
This format can be read, and even written, by spreadsheet applications such as Microsoft Excel or StarOffice 
Calc.
You can directly edit the .CSV file to manipulate data, but the changes are visible only after executing the 
FLUSH TABLES command. But this is not the prefered way.
6.10.1. Repairing and Checking CSV Tables:
Functionality introduced in version 5.1.9
The CSV storage engines supports the CHECK and REPAIR statements to verify and if possible repair a 
damaged CSV table. When running the CHECK statement, the CSV file will be checked for validity by looking for 
the correct field separators, escaped fields (matching or missing quotation marks), the correct number of fields 
compared to the table definition and the existence of a corresponding CSV metafile. The first invalid row discovered 
will report an error. Checking a valid table produces output like that shown below:
mysql> check table csvtest;
+--------------+-------+----------+----------+
| Table | Op | Msg_type | Msg_text |
MySQL Database Administration
 43 
+--------------+-------+----------+----------+
| test.csvtest | check | status | OK |
+--------------+-------+----------+----------+
1 row in set (0.00 sec)
A check on a corrupted table returns a fault:
mysql> check table csvtest;
+--------------+-------+----------+----------+
| Table | Op | Msg_type | Msg_text |
+--------------+-------+----------+----------+
| test.csvtest | check | error | Corrupt |
+--------------+-------+----------+----------+
1 row in set (0.01 sec)
To repair a table you can use REPAIR, this copies as many valid rows from the existing CSV data as possible, 
and then replaces the existing CSV file with the recovered rows. Any rows beyond the corrupted data are lost.
mysql> repair table csvtest;
+--------------+--------+----------+----------+
| Table | Op | Msg_type | Msg_text |
+--------------+--------+----------+----------+
| test.csvtest | repair | status | OK |
+--------------+--------+----------+----------+
1 row in set (0.02 sec)
Note: Note that during repair, only the rows from the CSV file up to the first damaged row are copied to the new 
table. All other rows from the first damaged row to the end of the table are removed, even valid rows.
6.10.2. CSV Limitations:
The CSV storage engine does not support indexing.
Partitioning is not supported for tables using the CSV storage engine.
Beginning with MySQL 5.1.23, tables using the CSV storage engine can no longer be created with NULL 
columns. However, for backward compatibility, you can continue to use such tables that were created in previous 
MySQL releases.
6.11. The BLACKHOLE Storage Engine
The BLACKHOLE storage engine acts as a “black hole” that accepts data but throws it away and does not 
store it. Retrievals always return an empty result:
mysql> CREATE TABLE test(i INT, c CHAR(10)) ENGINE = BLACKHOLE;
Query OK, 0 rows affected (0.03 sec)
mysql> INSERT INTO test VALUES(1,'record one'),(2,'record two');
Query OK, 2 rows affected (0.00 sec)
Records: 2 Duplicates: 0 Warnings: 0
mysql> SELECT * FROM test;
Empty set (0.00 sec)
To enable the BLACKHOLE storage engine if you build MySQL from source, invoke configure with the -
-with-blackhole-storage-engine option. To examine the source for the BLACKHOLE engine, look in the sql directory 
of a MySQL source distribution.
When you create a BLACKHOLE table, the server creates a table format file in the database directory. The file 
begins with the table name and has an .frm extension. There are no other files associated with the table.
The BLACKHOLE storage engine supports all kinds of indexes. That is, you can include index declarations in 
the table definition.
Inserts into a BLACKHOLE table do not store any data, but if the binary log is enabled, the SQL statements 
are logged (and replicated to slave servers). This can be useful as a repeater or filter mechanism. Suppose that 
MySQL Database Administration
 44 
your application requires slave-side filtering rules, but transferring all binary log data to the slave first results in too 
much traffic. In such a case, it is possible to set up on the master host a “dummy” slave process whose default 
storage engine is BLACKHOLE, depicted as follows:
The dummy process does not actually store any data, so there is little processing overhead incurred by 
running the additional mysqld process on the replication master host. This type of setup can be repeated with 
additional replication slaves.
As of MySQL 5.1.4, the BLACKHOLE engine is transaction-aware, in the sense that committed transactions 
are written to the binary log and rolled-back transactions are not.
Blackhole Engine and Auto Increment Columns
The Blackhole engine is a no-op engine. Any operations performed on a table using Blackhole will have no 
effect. This should be born in mind when considering the behavior of primary key columns that auto increment. The 
engine will not automatically increment field values, and does not retain auto increment field state. This has 
important implications in replication.
Consider the following replication scenario where all three of the following conditions apply:
1.On a master server there is a blackhole table with an auto increment field that is a primary key.
2.On a slave the same table exists but using the MyISAM engine.
3.Inserts are performed into the master's table without explicitly setting the auto increment value in the INSERT 
statement itself or through using a SET INSERT_ID statement.
In this scenario replication will fail with a duplicate entry error on the primary key column.
In statement based replication, the value of INSERT_ID in the context event will always be the same. Replication 
will therefore fail due to trying insert a row with a duplicate value for a primary key column.
In row based replication, the value that the engine returns for the row always be the same for each insert. This 
will result in the slave attempting to replay two insert log entries using the same value for the primary key column, 
and so replication will fail.
7. MySQL Client Programs
7.1 mysql ― The MySQL Command-Line Tool
mysql is a simple SQL shell (with GNU readline capabilities). It supports interactive and noninteractive use. 
When used interactively, query results are presented in an ASCII-table format. When used noninteractively (for 
example, as a filter), the result is presented in tab-separated format. The output format can be changed using 
command options.
If you have problems due to insufficient memory for large result sets, use the --quick option. This forces mysql 
to retrieve results from the server a row at a time rather than retrieving the entire result set and buffering it in 
memory before displaying it.
Using mysql is very easy. Invoke it from the prompt of your command interpreter as follows:
MySQL Database Administration
 45 
shell> mysql db_name
Or:
shell> mysql --user=user_name --password=your_password db_name
mysql Options:
mysql supports the following options, which can be specified on the command line or in the [mysql] and [client] 
option file groups.
--compress, -C 
Compress all information sent between the client and the server if both support compression. 
--database=db_name, -D db_name 
The database to use. This is useful primarily in an option file. 
--delimiter=str 
Set the statement delimiter. The default is the semicolon character (“;”). 
--execute=statement, -e statement 
Execute the statement and quit.
--force, -f 
Continue even if an SQL error occurs. 
--host=host_name, -h host_name 
Connect to the MySQL server on the given host. 
--html, -H 
Produce HTML output. 
--password[=password], -p[password] 
The password to use when connecting to the server. If you use the short option form (-p), you cannot have a space 
between the option and the password. If you omit the password value following the --password or -p option on the 
command line, mysql prompts for one. 
--port=port_num, -P port_num 
The TCP/IP port number to use for the connection. 
--quick, -q 
Do not cache each query result, print each row as it is received. This may slow down the server if the output is 
suspended. With this option, mysql does not use the history file. 
--skip-column-names, -N
Do not write column names in results. 
--socket=path, -S path
For connections to localhost, the Unix socket file to use.
--tee=file_name 
Append a copy of output to the given file. This option works only in interactive mode.
--user=user_name, -u user_name 
The MySQL user name to use when connecting to the server. 
--xml, -X 
Produce XML output. 
--connect_timeout 
The number of seconds before connection timeout.
MySQL Database Administration
 46 
7.2 mysqladmin ― Client for Administering a MySQL Server
mysqladmin is a client for performing administrative operations. You can use it to check the server's 
configuration and current status, to create and drop databases, and more. 
create db_name
Create a new database named db_name. 
drop db_name 
Delete the database named db_name and all its tables. 
flush-logs 
Flush all logs. 
flush-privileges (reload)
Reload the grant tables (same as reload). 
flush-status 
Clear status variables. 
flush-tables 
Flush all tables. 
kill id,id,...
Kill server threads. If multiple thread ID values are given, there must be no spaces in the list. 
ping
Check whether the server is available. The return status from mysqladmin is 0 if the server is running, 1 if it is not. 
This is 0 even in case of an error such as Access denied, because this means that the server is running but refused 
the connection, which is different from the server not running. 
processlist 
Show a list of active server threads. This is like the output of the SHOW PROCESSLIST statement. If the --verbose 
option is given, the output is like that of SHOW FULL PROCESSLIST.
status 
Display a short server status message. 
Uptime
The number of seconds the MySQL server has been running. 
Threads 
The number of active threads (clients). 
Questions
The number of questions (queries) from clients since the server was started. 
Slow queries 
The number of queries that have taken more than long_query_time seconds. 
Opens
The number of tables the server has opened. 
Flush tables 
The number of flush-*, refresh, and reload commands the server has executed. 
Open tables 
The number of tables that currently are open. 
Queries per second avg
Average Queries executed in the server per second.
MySQL Database Administration
 47 
variables
Display the server system variables and their values. 
version 
Display version information from the server. 
7.3 mysqlcheck ― A Table Maintenance Program
The mysqlcheck client performs table maintenance: It checks, repairs, optimizes, or analyzes tables. Each 
table is locked and therefore unavailable to other sessions while it is being processed, although for check 
operations, the table is locked with a READ lock only. Table maintenance operations can be time-consuming, 
particularly for large tables. If you use the --databases or --all-databases option to process all tables in one or more 
databases, an invocation of mysqlcheck might take a long time.
mysqlcheck is similar in function to myisamchk, but works differently. The main operational difference is that 
mysqlcheck must be used when the mysqld server is running, whereas myisamchk should be used when it is not. 
The benefit of using mysqlcheck is that you do not have to stop the server to perform table maintenance. 
mysqlcheck uses the SQL statements CHECK TABLE, REPAIR TABLE, ANALYZE TABLE, and OPTIMIZE
TABLE in a convenient way for the user. It determines which statements to use for the operation you want to 
perform, and then sends the statements to the server to be executed. For details about which storage engines each 
statement works with, see the descriptions for those statements
The MyISAM storage engine supports all four maintenance operations, so mysqlcheck can be used to perform 
any of them on MyISAM tables. Other storage engines do not necessarily support all operations. In such cases, an 
error message is displayed. For example, if test.t is a MEMORY table, an attempt to check it produces this result: 
shell> mysqlcheck test t
test.t
note : The storage engine for the table doesn't support check
Note : It is best to make a backup of a table before performing a table repair operation; under some circumstances 
the operation might cause data loss. Possible causes include but are not limited to file system errors.
There are three general ways to invoke mysqlcheck: 
shell> mysqlcheck [options] db_name [tbl_name ...]
shell> mysqlcheck [options] --databases db_name ...
shell> mysqlcheck [options] –all-databases
If you do not name any tables following db_name or if you use the --databases or --all-databases option, entire 
databases are checked. 
Options:
--all-databases, -A 
Check all tables in all databases. This is the same as using the --databases option and naming all the databases on 
the command line. 
--analyze, -a 
Analyze the tables and stores the key distribution for a table.
--auto-repair
If a checked table is corrupted, automatically fix it. Any necessary repairs are done after all tables have been 
checked. 
--check, -c 
Check the tables for errors. This is the default operation. 
--check-only-changed, -C 
Check only tables that have changed since the last check or that have not been closed properly. 
--databases, -B 
MySQL Database Administration
 48 
Process all tables in the named databases. Normally, mysqlcheck treats the first name argument on the command 
line as a database name and following names as table names. With this option, it treats all name arguments as 
database names. 
--extended, -e 
If you are using this option to check tables, it ensures that they are 100% consistent but takes a long time. 
--fast, -F 
Check only tables that have not been closed properly. 
--force, -f 
Continue even if an SQL error occurs. 
--host=host_name, -h host_name
Connect to the MySQL server on the given host. 
--medium-check, -m
Do a check that is faster than an --extended operation. This finds only 99.99% of all errors, which should be good 
enough in most cases. 
--optimize, -o
Optimize the tables. 
--password[=password], -p[password] 
The password to use when connecting to the server.
--port=port_num, -P port_num 
The TCP/IP port number to use for the connection. 
--quick, -q
If you are using this option to repair tables, it tries to repair only the index tree. This is the fastest repair method. 
--repair, -r 
Perform a repair that can fix almost anything except unique keys that are not unique. 
--socket=path, -S path 
For connections to localhost, the Unix socket file to use
--tables 
Override the --databases or -B option. All name arguments following the option are regarded as table names. 
--user=user_name, -u user_name
The MySQL user name to use when connecting to the server. 
7.4 mysqldump ― A Database Backup Program
Refer 11. Backup and Recovery
7.5 mysqlimport ― A Data Import Program
Refer 11.3.3 Dumping Data in Delimited-Text Format
7.6 mysqlshow ― Display Database, Table, and Column Information
The mysqlshow client can be used to quickly see which databases exist, their tables, or a table's columns or 
indexes. mysqlshow provides a command-line interface to several SQL SHOW statements. The same information 
can be obtained by using those statements directly. For example, you can issue them from the mysql client 
program. 
Invoke mysqlshow like this: 
MySQL Database Administration
 49 
shell> mysqlshow [options] [db_name [tbl_name [col_name]]]
− If no database is given, a list of database names is shown
− If no table is given, all matching tables in the database are shown.
− If no column is given, all matching columns and column types in the table are shown.
The output displays only the names of those databases, tables, or columns for which you have some privileges.
If the last argument contains shell or SQL wildcard characters (“*”, “?”, “%”, or “_”), only those names that are 
matched by the wildcard are shown. If a database name contains any underscores, those should be escaped with a 
backslash to get a list of the proper tables or columns. “*” and “?” characters are converted into SQL “%” and “_” 
wildcard characters. This might cause some confusion when you try to display the columns for a table with a “_” in 
the name, because in this case, mysqlshow shows you only the table names that match the pattern. This is easily 
fixed by adding an extra “%” last on the command line as a separate argument.
Options:
--count 
Show the number of rows per table. This can be slow for non-MyISAM tables.
--host=host_name
--password[=password]
--port=port_num
--socket=path
--keys
Show table indexes
--status
Display extra information about each table (SHOW TABLE STATUS)
7.7 mysqlslap ― Load Emulation Client
mysqlslap is a program designed to emulate client load for a MySQL server and to report the timing of each 
stage. It works as if multiple clients are accessing the server. mysqlslap is available as of MySQL 5.1.4. 
Invoke mysqlslap like this: 
[shell] # mysqlslap [options]
Some options such as --create or --query enable you to specify a string containing an SQL statement or a file 
containing statements. If you specify a file, by default it must contain one statement per line. (That is, the implicit 
statement delimiter is the newline character.) Use the --delimiter option to specify a different delimiter, which 
enables you to specify statements that span multiple lines or place multiple statements on a single line. You cannot 
include comments in a file; mysqlslap does not understand them. 
mysqlslap runs in three stages:
1.Create schema, table, and optionally any stored programs or data you want to using for the test. This stage 
uses a single client connection.
2.Run the load test. This stage can use many client connections. 
3.Clean up (disconnect, drop table if specified). This stage uses a single client connection. 
Examples: 
Supply your own create and query SQL statements, with 50 clients querying and 200 selects for each: 
mysqlslap --delimiter=";" \
 --create="CREATE TABLE a (b int);INSERT INTO a VALUES (23)" \
 --query="SELECT * FROM a" --concurrency=50 –iterations=200
Tell the program to load the create, insert, and query SQL statements from the specified files, where the 
create.sql file has multiple table creation statements delimited by ';' and multiple insert statements delimited by ';'. 
The --query file will have multiple queries delimited by ';'. Run all the load statements, then run all the queries in the 
MySQL Database Administration
 50 
query file with five clients.
mysqlslap --concurrency=5 --iterations=5 –query=query.sql --create=create.sql --delimiter=";"
mysqlslap supports the following options, which can be specified on the command line or in the [mysqlslap]:
--auto-generate-sql, -a
Generate SQL statements automatically when they are not supplied in files or using command options. 
--auto-generate-sql-add-autoincrement
Add an AUTO_INCREMENT column to automatically generated tables. This option was added in MySQL 
5.1.18. 
--auto-generate-sql-execute-number=N
Specify how many queries to generate automatically. This option was added in MySQL 5.1.18.
--auto-generate-sql-secondary-indexes=N
Specify how many secondary indexes to add to automatically generated tables. By default, none are added. 
This option was added in MySQL 5.1.18.
--auto-generate-sql-unique-query-number=N
How many different queries to generate for automatic tests. For example, if you run a key test that performs 
1000 selects, you can use this option with a value of 1000 to run 1000 unique queries, or with a value of 50 to 
perform 50 different selects. The default is 10. This option was added in MySQL 5.1.18. 
--create=value
The file or string containing the statement to use for creating the table. 
--delimiter=str, -F str
The delimiter to use in SQL statements supplied in files or using command options.
--detach=N
Detach (close and reopen) each connection after each N statements. The default is 0 (connections are not 
detached). This option was added in MySQL 5.1.21. 
--engine=engine_name, -e engine_name
The storage engine to use for creating tables. 
--host=host_name, -h host_name
Connect to the MySQL server on the given host. 
--iterations=N, -i N
The number of times to run the tests. 
--number-char-cols=N, -x N
The number of VARCHAR columns to use if --auto-generate-sql is specified. 
--number-int-cols=N, -y N
The number of INT columns to use if --auto-generate-sql is specified. 
--only-print
Do not connect to databases. mysqlslap only prints what it would have done. This option was added in MySQL 
5.1.5.
--password[=password], -p[password]
The password to use when connecting to the server. If you use the short option form (-p), you cannot have a 
space between the option and the password.
--port=port_num, -P port_num
The TCP/IP port number to use for the connection. 
--query=value, -q value
The file or string containing the SELECT statement to use for retrieving data. 
MySQL Database Administration
 51 
--socket=path, -S path
For connections to localhost, the Unix socket file to used.
--user=user_name, -u user_name
The MySQL user name to use when connecting to the server. 
8. MySQL Administrative and Utility Programs
8.1 myisamchk ― MyISAM Table-Maintenance Utility
The myisamchk utility gets information about your database tables or checks, repairs, or optimizes them. 
myisamchk works with MyISAM tables. You can also use the CHECK TABLE and REPAIR TABLE statements to
check and repair MyISAM tables.
Note: It is best to make a backup of a table before performing a table repair operation; under some circumstances 
the operation might cause data loss.
Invoke myisamchk like this:
shell> myisamchk [options] tbl_name ...
With no options, myisamchk simply checks your table as the default operation. tbl_name is the database table 
you want to check or repair. If you run myisamchk somewhere other than in the database directory,
you must specify the path to the database directory, because myisamchk has no idea where the database is 
located. In fact, myisamchk does not actually care whether the files you are working on are located in a database 
directory. You can copy the files that correspond to a database table into some other location and perform recovery 
operations on them there.
You can name several tables on the myisamchk command line if you wish. You can also specify a table by 
naming its index file (the file with the .MYI suffix). This enables you to specify all tables in a directory by using the 
pattern *.MYI. For example, if you are in a database directory, you can check all the MyISAM tables in that directory 
like this:
shell> myisamchk *.MYI
If you are not in the database directory, you can check all the tables there by specifying the path to the 
directory:
shell> myisamchk /path/to/database_dir/*.MYI
You can even check all tables in all databases by specifying a wildcard with the path to the MySQL data 
directory:
shell> myisamchk /path/to/datadir/*/*.MYI
Note: You must ensure that no other program is using the tables while you are running myisamchk. The most 
effective means of doing so is to shut down the MySQL server while running myisamchk, or to lock all tables that 
myisamchk is being used on.
Otherwise, when you run myisamchk, it may display the following error message:
warning: clients are using or haven't closed the table properly
This means that you are trying to check a table that has been updated by another program (such as the 
mysqld server) that hasn't yet closed the file or that has died without closing the file properly, which can sometimes 
lead to the corruption of one or more MyISAM tables. 
Options:
--check, -c 
Check the table for errors. This is the default operation if you specify no option that selects an operation type 
explicitly. 
MySQL Database Administration
 52 
--fast, -F
Check only tables that haven't been closed properly. 
--analyze, -a 
Analyze the distribution of key values. This improves join performance by enabling the join optimizer to better 
choose the order in which to join the tables and which indexes it should use. To obtain information about the key 
distribution.
--backup, -B 
Make a backup of the .MYD file as file_name-time.BAK 
--extend-check, -e 
Do a repair that tries to recover every possible row from the data file. Normally, this also finds a lot of garbage 
rows. Do not use this option unless you are desperate. 
--recover, -r 
Do a repair that can fix almost any problem except unique keys that are not unique. If you want to recover a 
table, this is the option to try first. You should try --safe-recover only if myisamchk reports that the table cannot be 
recovered using --recover.
--safe-recover, -o 
Do a repair using an old recovery method that reads through all rows in order and updates all index trees 
based on the rows found. This is an order of magnitude slower than --recover, but can handle a couple of very 
unlikely cases that --recover cannot.
--unpack, -u
Unpack a table that was packed with myisampack. 
--set-auto-increment[=value], -A[value] 
Force AUTO_INCREMENT numbering for new records to start at the given value (or higher, if there are 
existing records with AUTO_INCREMENT values this large). If value is not specified, AUTO_INCREMENT numbers 
for new records begin with the largest value currently in the table, plus one.
8.2. myisampack — Generate Compressed, Read-Only MyISAM Tables
The myisampack utility compresses MyISAM tables. myisampack works by compressing each column in the 
table separately. Usually, myisampack packs the data file 40% to 70%.
When the table is used later, the server reads into memory the information needed to decompress columns. 
This results in much better performance when accessing individual rows, because you only have to uncompress 
exactly one row.
− If the mysqld server was invoked with external locking disabled, it is not a good idea to invoke 
myisampack if the table might be updated by the server during the packing process. It is safest to 
compress tables with the server stopped
− After packing a table, it becomes read only.
Invoke myisampack like this: 
shell> myisampack [options] file_name ...
After you compress a table with myisampack, you should use myisamchk -rq to rebuild its indexes.
Options:
--backup
Make a backup of each table's data file using the name tbl_name.OLD.
--tmpdir=path 
Use the named directory as the location where myisampack creates temporary files.
Compressed Table Characteristics:
MySQL Database Administration
 53 
Compressed storage format is a read-only format that is generated with the myisampack tool. Compressed 
tables can be uncompressed with myisamchk. 
− Compressed tables take very little disk space. This minimizes disk usage, which is helpful when using 
slow disks (such as CDROMs).
− Each row is compressed separately, so there is very little access overhead. The header for a row takes 
up one to three bytes depending on the biggest row in the table. Each column is compressed 
differently.
− Numbers with a value of zero are stored using one bit.
− If values in an integer column have a small range, the column is stored using the smallest possible 
type. For example, a BIGINT column (eight bytes) can be stored as a TINYINT column (one byte) if all 
its values are in the range from -128 to 127.
− If a column has only a small set of possible values, the data type is converted to ENUM.
8.3. mysql_convert_table_format — Convert Tables to Use a Given Storage Engine
mysql_convert_table_format converts the tables in a database to use a particular storage engine (MyISAM by 
default). mysql_convert_table_format is written in Perl and requires that the DBI and DBD::mysql Perl modules be 
installed.
Invoke mysql_convert_table_format like this:
shell> mysql_convert_table_format [options] db_name
Options:
--host=host_name 
Connect to the MySQL server on the given host.
--password=password 
The password to use when connecting to the server. Note that the password value is not optional for this 
option, unlike for other MySQL programs.
--port=port_num 
The TCP/IP port number to use for the connection. 
--socket=path 
For connections to localhost, the Unix socket file to use. 
--type=engine_name 
Specify the storage engine that the tables should be converted to use. The default is MyISAM if this option is 
not given. 
--user=user_name 
The MySQL user name to use when connecting to the server. 
mysql_config — Get Compile Options for Compiling Clients
mysql_config provides you with useful information for compiling your MySQL client and connecting it to 
MySQL. About port, socket, include files, libraries, version etc.
9. MySQL Server Administration
9.1 Server System Variables
auto_increment_increment
Controls the interval between successive column values.
auto_increment_offset
Determines the starting point for the AUTO_INCREMENT column value.
Autocommit
Disables or enable the autocommit mode for InnoDB Engine.
log-error
MySQL Database Administration
 54 
Enables the error log (Enabled by default).
skip-networking
Disallows access for the TCP/IP connections.
init_connect
A string to be executed by the server for each client that connects. The string consists of one or more SQL 
statements, separated by semicolon characters. For example, each client session begins by default with 
autocommit mode enabled.
init_file
The name of the file specified with the --init-file option when you start the server. This should be a file 
containing SQL statements that you want the server to execute when it starts. Each statement must be on a single 
line and should not include comments. No statement terminator such as ;, \g, or \G should be given at the end of 
each statement.
join_buffer_size
The minimum size of the buffer that is used for plain index scans, range index scans, and joins that do not use 
indexes and thus perform full table scans. Increase the value of join_buffer_size to get a faster full join when 
adding indexes is not possible. The maximum permissible setting for join_buffer_size is 4GB.
max_allowed_packet
The maximum size of one packet or any generated/intermediate string.You must increase this value if you are 
using large BLOB columns or long strings.
max_connect_errors
If there are more than this number of interrupted connections from a host, that host is blocked from further 
connections. You can unblock blocked hosts with the FLUSH HOSTS statement. If a connection is established 
successfully within fewer than max_connect_errors attempts after a previous connection was interrupted, the error 
count for the host is cleared to zero.
max_connections
The maximum permitted number of simultaneous client connections. By default, this is 151, beginning with 
MySQL 5.1.15.
--skip-external-locking
Do not use external locking (system locking). This affects only MyISAM table access.
wait_timeout(default 28800)
The number of seconds the server waits for activity on a noninteractive connection before closing it. This 
timeout applies only to TCP/IP and Unix socket file connections, not to connections made using named pipes, or 
shared memory.
9.2 Server Status Variables
The server maintains many status variables that provide information about its operation. You can view these 
variables and their values by using the SHOW [GLOBAL | SESSION] STATUS statement The 
optional GLOBAL keyword aggregates the values over all connections, and SESSIONshows the values for the 
current connection. 
Aborted_clients
The number of connections that were aborted because the client died without closing the connection properly.
Aborted_connects
The number of failed attempts to connect to the MySQL server.
Bytes_received
Bytes received by the server.
Bytes_sent
Bytes sent received by the server.
Uptime
MySQL Database Administration
 55 
Uptime of the MySQL server
Com_XXX Variables
We have several Com variables which identifies number of queries executed.
Max_used_connections
The maximum number of connections that have been in use simultaneously since the server started.
Queries
The number of statements executed by the server. This variable includes statements executed within stored 
programs.
Questions
The number of statements executed by the server. As of MySQL 5.0.72, this includes only statements sent to 
the server by clients and no longer includes statements executed within stored programs.
Select_scan
The number of joins that did a full scan.
Table_locks_immediate
The number of times that a request for a table lock could be granted immediately.
Table_locks_waited
The number of times that a request for a table lock could not be granted immediately and a wait was needed. 
If this is high and you have performance problems, you should first optimize your queries, and then either split your 
table or tables or use replication.
Threads_connected
The number of currently open connections.
Threads_created
The number of threads created to handle connections. If Threads_created is big, you may want to increase 
thethread_cache_size value. The cache miss rate can be calculated as Threads_created/Connections.
9.3 Server SQL Modes
The MySQL server can operate in different SQL modes, and can apply these modes differently for different 
clients. Modes define what SQL syntax MySQL should support and what kind of data validation checks it should 
perform. This makes it easier to use MySQL in different environments and to use MySQL together with other 
database servers. 
You can set the default SQL mode by starting mysqld with the --sql-mode="modes" option, or by using sqlmode="modes" in my.cnf. The default value is empty. 
You can change the SQL mode at runtime by using a SET [GLOBAL|SESSION] sql_mode='modes' statement 
to set the sql_mode system value. Setting the SESSION variable affects only the current client. Any client can 
change its own session sql_mode value at any time.
You can retrieve the current global or session sql_mode value with the following statements:
mysql> SELECT @@GLOBAL.sql_mode;
mysql> SELECT @@SESSION.sql_mode;
The most important sql_mode values are probably these:
ALLOW_INVALID_DATES
Do not perform full checking of dates. Check only that the month is in the range from 1 to 12 and the day is in 
the range from 1 to 31. With strict mode disabled, invalid dates such as '2004-04-31' are converted to '0000-00-00' 
and a warning is generated. With strict mode enabled, invalid dates generate an error.
ANSI_QUOTES
Treat “"” as an identifier quote character (like the “`” quote character) and not as a string quote character. You 
can still use “`” to quote identifiers with this mode enabled. With ANSI_QUOTES enabled, you cannot use double 
quotation marks to quote literal strings, because it is interpreted as an identifier.
MySQL Database Administration
 56 
IGNORE_SPACE
Permit spaces between a function name and the “(” character.
NO_AUTO_CREATE_USER
Prevent the GRANT statement from automatically creating new users unless non-empty password is 
specified.
NO_DIR_IN_CREATE
When creating a table, ignore all INDEX DIRECTORY and DATA DIRECTORY directives. This option is useful 
on slave replication servers.
NO_ENGINE_SUBSTITUTION
Control automatic substitution of the default storage engine when a statement such as CREATE TABLE or 
ALTER TABLE specifies a storage engine that is disabled or not compiled in.
NO_ZERO_IN_DATE
In strict mode, do not accept dates where the year part is nonzero but the month or day part is 0 (for example, 
'0000-00-00' is legal but '2010-00-01' and '2010-01-00' are not). If used with the IGNORE option, MySQL inserts a 
'0000-00-00' date for any such date. When not in strict mode, the date is accepted but a warning is generated.
PIPES_AS_CONCAT
Treat || as a string concatenation operator.
REAL_AS_FLOAT
Treat REAL as a synonym for FLOAT.
STRICT_TRANS_TABLES & STRICT_ALL_TABLES
Strict mode controls how MySQL handles input values that are invalid or missing. A value can be invalid for 
several reasons. For example, it might have the wrong data type for the column, or it might be out of range.
For transactional tables, an error occurs for invalid or missing values in a statement when either of the 
STRICT_ALL_TABLES or STRICT_TRANS_TABLES modes are enabled. The statement is aborted and rolled 
back.
For non-transactional tables, the behavior is the same for either mode, if the bad value occurs in the first row 
to be inserted or updated. The statement is aborted and the table remains unchanged. If the statement inserts or 
modifies multiple rows and the bad value occurs in the second or later row, the result depends on which strict 
option is enabled:
− For STRICT_ALL_TABLES, MySQL returns an error and ignores the rest of the rows. However, in this 
case, the earlier rows still have been inserted or updated. This means that you might get a partial 
update, which might not be what you want. To avoid this, it is best to use single-row statements 
because these can be aborted without changing the table.
− For STRICT_TRANS_TABLES, MySQL converts an invalid value to the closest valid value for the 
column and insert the adjusted value. If a value is missing, MySQL inserts the implicit default value for 
the column data type. In either case, MySQL generates a warning rather than an error and continues 
processing the statement.
ANSI
This mode changes syntax and behavior to confirm more closely to standard SQL
REAL_AS_FLOAT, PIPES_AS_CONCAT, ANSI_QUOTES, IGNORE_SPACE, ANSI
TRADITIONAL
Make MySQL behave like a “traditional” SQL database system. A simple description of this mode is “give an 
error instead of a warning” when inserting an incorrect value into a column. 
Note: The INSERT/UPDATE aborts as soon as the error is noticed. This may not be what you want if you are using 
a non-transactional storage engine, because data changes made prior to the error may not be rolled back, resulting 
in a “partially done” update. 
Equivalent to STRICT_TRANS_TABLES, STRICT_ALL_TABLES, NO_ZERO_IN_DATE, NO_ZERO_DATE, 
ERROR_FOR_DIVISION_BY_ZERO, NO_AUTO_CREATE_USER. 
MySQL Database Administration
 57 
10. MySQL Server Logs
10.1. The Error Log
The error log contains information indicating when mysqld was started and stopped and also any critical errors 
that occur while the server is running. If mysqld notices a table that needs to be automatically checked or repaired, 
it writes a message to the error log.
You can specify where mysqld writes the error log with the --log-error[=file_name] option. If the option is given 
with no file_name value, mysqld uses the name host_name.err by default. The server creates the file in the data 
directory unless an absolute path name is given to specify a different directory.
To rename the file, you can do so manually before flushing. Then flushing the logs reopens a new file with the 
original file name. For example, you can rename the file and create a new one using the following commands:
shell> mv host_name.err host_name.err-old
shell> mysqladmin flush-logs
shell> mv host_name.err-old backup-directory
The --log-warnings option or log_warnings system variable can be used to control warning logging to the error 
log. The default value is enabled (1). Warning logging can be disabled using a value of 0. If the value is greater 
than 1, aborted connections are written to the error log.
10.2. The General Query Log
The general query log is a general record of what mysqld is doing. The server writes information to this log 
when clients connect or disconnect, and it logs each SQL statement received from clients. The general query log 
can be very useful when you suspect an error in a client and want to know exactly what the client sent to mysqld.
Control the general query log at server startup as follows:
− Before 5.1.6, the general query log destination is always a file. To enable the log, start mysqld with the 
–log[=file_name].
− As of MySQL 5.1.6, the destination can be a file or a table, or both. Start mysqld with the –
log[=file_name] and optionally use --log-output to specify the log destination.
--log-output
This option determines the destination for general query and slow query log output. The option value can be 
given as one or more of the words TABLE, FILE, or NONE. If the option is given without a value, the default is 
FILE. TABLE select logging to the general_log and slow_log tables in the mysql database as a destination. FILE 
selects logging to log files as a destination. NONE disables logging. This option selects log output destinations, but 
does not enable log output.
− As of MySQL 5.1.12, as an alternative to --log or -l, use --general_log[={0|1}] to specify the initial 
general query log state.
− As of MySQL 5.1.12, use --general_log[={0|1}] to enable or disable the general query log, and 
optionally --general_log_file=file_name to specify a log file name. The --log option is deprecated.
If you specify no name for the general query log file, the default name is host_name.log. The server creates 
the file in the data directory unless an absolute path name is given to specify a different directory. 
From MySQL 5.1.12 we can control the general query log at runtime. Use the global general_log and 
general_log_file system variables. Set general_log to 0 (or OFF) to disable the log or to 1 (or ON) to enable it. Set 
general_log_file to specify the name of the log file.
To rename the file, you can do so manually before flushing. Then flushing the logs reopens a new file with the 
original file name. For example, you can rename the file and create a new one using the following commands:
shell> mv host_name.log host_name-old.log
shell> mysqladmin flush-logs
shell> mv host_name-old.log backup-directory
The session sql_log_off variable can be set to ON or OFF to disable or enable general query logging for the 
current connection. 
MySQL Database Administration
 58 
10.3. The Binary Log
The binary log contains “events” that describe database changes such as table creation operations or 
changes to table data. It also contains events for statements that potentially could have made changes (for 
example, a DELETE which matched no rows), unless row-based logging is used. The binary log also contains 
information about how long each statement took that updated data. The binary log has two important purposes: 
− For replication purpose.
− Data recovery operations.
Running a server with binary logging enabled makes performance slightly slower. However, the benefits of the 
binary log in enabling you to set up replication and for restore operations generally outweigh this minor
performance decrement. 
The binary log is not used for statements such as SELECT or SHOW that do not modify data.
The format of the events recorded in the binary log is dependent on the binary logging format. Three format 
types are supported.
1. statement-based logging (causes logging to be statement-based)
2. row-based logging (causes logging to be row-based) (5.1.5)
3. mixed-base logging (causes logging to use mixed format) (5.1.8)
Statement-Based Logging: Propogates all the SQL statements which are executed in the server.
Row-Based Logging: writes events to the binary log that indicate how individual table rows are affected.
Mixed-Logging: With mixed logging, statement-based logging is used by default, but the logging mode switches 
automatically to row-based in certain cases.
Setting The Binary Log Format
The logging format also can be switched at runtime. To specify the format globally for all clients, set the global 
value of the binlog_format system variable: 
mysql> SET GLOBAL binlog_format = 'STATEMENT';
mysql> SET GLOBAL binlog_format = 'ROW';
mysql> SET GLOBAL binlog_format = 'MIXED';
An individual client can control the logging format for its own statements by setting the session value of 
binlog_format: 
mysql> SET SESSION binlog_format = 'STATEMENT';
mysql> SET SESSION binlog_format = 'ROW';
mysql> SET SESSION binlog_format = 'MIXED';
To change the global binlog_format value, you must have the SUPER privilege.
Binary Log Options and Variables
--log-bin[=base_name]
Enable binary logging. The server logs all statements that change data to the binary log.
binlog_format (5.1.5)
This variable sets the binary logging format, and can be any one of STATEMENT, ROW, or MIXED.
--log-bin-index[=file_name]
The index file for binary log file names. If you omit the file name, and if you did not specify one with --log-bin, 
MySQL uses host_name-bin.index as the file name. 
--binlog-do-db=db_name
Logs only the specific database changes.
Statement-based logging: Only those statements are written to the binary log where the default database 
(that is, the one selected by USE) is db_name. To specify more than one database, use this option multiple times, 
MySQL Database Administration
 59 
once for each database; however, doing so does not cause cross-database statements such as UPDATE 
some_db.some_table SET foo='bar' to be logged while a different database (or no database) is selected. 
Row-based logging: Logging is restricted to database db_name. Only changes to tables belonging to 
db_name are logged; the default database has no effect on this. Suppose that the server is started with --binlog-dodb=sales and row-based logging is in effect, and then the following statements are executed: 
USE prices;
UPDATE sales.february SET amount=amount+100;
The changes to the february table in the sales database are logged in accordance with the UPDATE 
statement; this occurs whether or not the USE statement was issued.
--binlog-ignore-db=db_name
Statement-based logging: Tells the server to not log any statement where the default database (that is, the
one selected by USE) is db_name. 
Row-based format: Tells the server not to log updates to any tables in the database db_name. The current 
database has no effect. 
--binlog_cache_size
The size of the cache to hold the SQL statements for the binary log during a transaction. A binary log cache is 
allocated for each client if the server supports any transactional storage engines and if the server has the binary log 
enabled. 
--max_binlog_size
If a write to the binary log causes the current log file size to exceed the value of this variable, the server 
rotates the binary logs. The minimum value is 4096 bytes. The maximum and default value is 1GB.
--sync_binlog
If the value of this variable is greater than 0, the MySQL server synchronizes its binary log to disk. There is 
one write to the binary log per statement if autocommit is enabled, and one write per transaction otherwise. The 
default value of sync_binlog is 0, which does no synchronizing to disk—in this case, the server relies on the 
operating system to flush the binary log's contents from time to time. A value of 1 is the safest choice because in 
the event of a crash you lose at most one statement or transaction from the binary log. However, But it is also the 
slowest choice.
mysqld appends a numeric extension to the binary log basename to generate binary log file names. The 
number increases each time the server creates a new log file, thus creating an ordered series of files. The server 
creates a new file in the series each time it starts or flushes the logs. The server also creates a new binary log file 
automatically after the current log's size reaches max_binlog_size. A binary log file may become larger than 
max_binlog_size if you are using large transactions because a transaction is written to the file in one piece, never 
split between files.
To keep track of which binary log files have been used, mysqld also creates a binary log index file that 
contains the names of all used binary log files. By default, this has the same basename as the binary log file, with 
the extension '.index'. You can change the name of the binary log index file with the --log-bin-index[=file_name] 
option. You should not manually edit this file while mysqld is running; doing so would confuse mysqld.
Deleting Binary Logs:
You can delete all binary log files with the RESET MASTER statement, or a subset of them with PURGE 
BINARY LOGS.
mysql> RESET MASTER;
mysql> PURGE BINARY|MASTER LOGS TO ‘<filename>’; 
A client that has the SUPER privilege can disable binary logging of its own statements by using a SET 
sql_log_bin=0 statement.
You can display the contents of binary log files with the mysqlbinlog utility.
mysql> mysqlbinlog <filename> > log.txt;
MySQL Database Administration
 60 
Options:
--database=db_name, -d db_name
This option causes mysqlbinlog to output entries from the binary log (local log only) that occur while db_name 
is been selected as the default database by USE.
--host=host_name, -h host_name
Option to specify the hostname of the server.
--password[=password], -p[password]
Option to specify the password of the server for respective user. 
--port=port_num, -P port_num
Option to specify the port of MySQL server on which it is running.
--socket=path, -S path
Option to specify the socket file of MySQL server.
--result-file=name, -r name
Direct output to the given file.
--start-datetime=datetime
Start reading the binary log at the first event having a timestamp equal to or later than the datetime argument. 
The datetime value is relative to the local time zone on the machine where you run mysqlbinlog.
Shell > mysqlbinlog --start-datetime="2005-12-25 11:25:56" binlog.000003
--stop-datetime=datetime
Stop reading the binary log at the first event having a timestamp equal to or later than the datetime argument. 
This option is useful for point-in-time recovery.
--start-position=N, -j N
Start reading the binary log at the first event having a position equal to or greater than N. This option applies 
to the first log file named on the command line. This option is useful for point-in-time recovery.
--stop-position=N
Stop reading the binary log at the first event having a position equal to or greater than N. This option applies to 
the last log file named on the command line. This option is useful for point-in-time recovery.
10.4. The Slow Query Log
The slow query log consists of all SQL statements that took more than long_query_time seconds to execute. 
The time to acquire the initial table locks is not counted as execution time. mysqld writes a statement to the slow 
query log after it has been executed and after all locks have been released, so log order might be different from 
execution order. 
To enable the slow query log, start mysqld with the --log-slow-queries[=file_name] option. 
--long_query_time (min=1, default=10)
If a query takes longer than this many seconds, the server increments the Slow_queries status variable. If you 
are using the --log-slow-queries option, the query is logged to the slow query log file. 
− Before 5.1.6, the slow query log destination is always a file.
− As of MySQL 5.1.6, the destination can be a file or a table.
− As of MySQL 5.1.12, as an alternative to --log-slow-queries, use --slow_query_log[={0|1}] to specify the 
initial slow query log state. In this case, the default slow query log file name is used.
− As of MySQL 5.1.29, use --slow_query_log[={0|1}] to enable or disable the slow query log, and 
optionally --slow_query_log_file=file_name to specify a log file name. The --log-slow-queries option is 
deprecated. 
If you specify no name for the slow query log file, the default name is host_name-slow.log. The server creates 
the file in the data directory unless an absolute path name is given to specify a different directory. 
MySQL Database Administration
 61 
11. Backup and Recovery
It is important to back up your databases so that you can recover your data and be up and running again in 
case problems occur, such as system crashes, hardware failures, or users deleting data by mistake. Backups are 
also essential as a safeguard before upgrading a MySQL installation, and they can be used to transfer a MySQL 
installation to another system or to set up replication slave servers. MySQL offers a variety of backup strategies 
from which you can choose the methods that best suit the requirements.
11.1. Backup and Recovery Types
Logical Versus Physical (Raw) Backups:
Logical backups save information represented as logical database structure (CREATE DATABASE, CREATE 
TABLE statements) and content (INSERT statements or delimited-text files). Physical backups consist of raw 
copies of the directories and files that store database contents.
Logical backup methods have these characteristics:
− The backup is done by querying the MySQL server to obtain database structure and content 
information.
− Backup is slower than physical methods because the server must access database information and 
convert it to logical format. If the output is written on the client side, the server must also send it to the 
backup program.
− Backup and restore granularity is available at the server level (all databases), database level (all tables 
in a particular database), or table level. This is true regardless of storage engine.
− The backup does not include log or configuration files, or other database-related files that are not part 
of databases
− Backups stored in logical format are machine independent and highly portable.
− Logical backups are performed with the MySQL server running. The server is not taken offline.
− Logical backup tools include the mysqldump program and the SELECT ... INTO OUTFILE statement. 
These work for any storage engine, even MEMORY.
− To restore logical backups, SQL-format dump files can be processed using the mysql client. To load 
delimited-text files, use the LOAD DATA INFILE statement or the mysqlimport client.
Physical backup methods have these characteristics:
− The backup consists of exact copies of database directories and files. Typically this is a copy of all or 
part of the MySQL data directory. Data from MEMORY tables cannot be backed up this way because 
their contents are not stored on disk.
− Physical backup methods are faster than logical because they involve only file copying without 
conversion.
− Backup and restore granularity ranges from the level of the entire data directory down to the level of 
individual files. This may or may not provide for table-level granularity, depending on storage engine.
− In addition to databases, the backup can include any related files such as log or configuration files.
− Backups are portable only to other machines that have identical or similar hardware characteristics.
− Backups can be performed while the MySQL server is not running. If the server is running, it is 
necessary to perform appropriate locking so that the server does not change database contents during 
the backup.
Local Versus Remote Backups:
A local backup is performed on the same host where the MySQL server runs, whereas a remote backup is 
done from a different host. For some types of backups, the backup can be initiated from a remote host even if the 
output is written locally on the server host.
− mysqldump can connect to local or remote servers. For SQL output (CREATE and INSERT 
statements), local or remote dumps can be done and generate output on the client. For delimited-text 
output (with the --tab option), data files are created on the server host.
− mysqlhotcopy performs only local backups: It connects to the server to lock it against data 
modifications and then copies local table files.
− SELECT ... INTO OUTFILE can be initiated from a local or remote client host, but the output file is 
created on the server host.
MySQL Database Administration
 62 
Full Versus Incremental Backups:
A full backup includes all data managed by a MySQL server at a given point in time. An incremental backup 
consists of the changes made to the data during a given time span (from one point in time to another). MySQL has 
different ways to perform full backups. Incremental backups are made possible by enabling the server's binary log, 
which the server uses to record data changes.
11.2. Database Backup Methods
Making Backups by Copying Table Files:
For storage engines that represent each table using its own files, tables can be backed up by copying those 
files. For example, My-ISAM tables are stored as files, so it is easy to do a backup by copying files (*.frm, *.MYD, 
and *.MYI files). To get a consistent backup, stop the server or do a LOCK TABLES on the relevant tables followed 
by FLUSH TABLES for the tables. You need only a read lock; this enables other clients to continue to query the 
tables while you are making a copy of the files in the database directory. The FLUSH TABLES statement is needed 
to ensure that the all active index pages are written to disk before you start the backup. 
But note that table file copying methods do not work if your database contains InnoDB tables. mysqlhotcopy 
does not work for InnoDB tables because InnoDB does not necessarily store table contents in database directories.
Backing Up and Recovering of InnoDB Database:
InnoDB Hot Backup enables you to back up a running MySQL database, including InnoDB and MyISAM 
tables, with minimal disruption to operations while producing a consistent snapshot of the database. When InnoDB 
Hot Backup is copying InnoDB tables, reads and writes to both InnoDB and MyISAM tables can continue. During 
the copying of MyISAM tables, reads (but not writes) to those tables are permitted. In addition, InnoDB Hot Backup 
supports creating compressed backup files, and performing backups of subsets of InnoDB tables.
If you are able to shut down your MySQL server, you can make a binary backup that consists of all files used 
by InnoDB to manage its tables. Use the following procedure:
1.Shut down the MySQL server and make sure that it stops without errors.
2.Copy all InnoDB data files (ibdata files and .ibd files) into a safe place.
3.Copy all the .frm files for InnoDB tables to a safe place.
4.Copy all InnoDB log files (ib_logfile files) to a safe place.
5.Copy your my.cnf configuration file or files to a safe place.
In addition to making binary backups as just described, regularly make dumps of your tables with mysqldump. 
A binary file might be corrupted without you noticing it. Dumped tables are stored into text files that are humanreadable, so spotting table corruption becomes easier. Also, because the format is simpler, the chance for serious 
data corruption is smaller. mysqldump also has a --single-transaction option for making a consistent snapshot 
without locking out other clients.
Replication works with InnoDB tables, so you can use MySQL replication capabilities to keep a copy of your 
database at database sites requiring high availability. To be able to recover your InnoDB database to the present 
from the time at which the binary backup was made, run your MySQL server with binary logging turned on. To 
achieve point-in-time recovery after restoring a backup, you can apply changes from the binary log that occurred 
after the backup was made.
To recover from a crash of your MySQL server, the only requirement is to restart it. InnoDB automatically 
checks the logs and performs a roll-forward of the database to the present. InnoDB automatically rolls back 
uncommitted transactions that were present at the time of the crash.
Making Delimited-Text File Backups:
To create a text file containing a table's data, you can use
mysql > SELECT * INTO OUTFILE 'file_name' FROM tbl_name. 
Here is an example that produces a file in the comma-separated values (CSV) format used by many programs: 
mysql > SELECT a,b,a+b INTO OUTFILE '/tmp/result.txt'
MySQL Database Administration
 63 
 FIELDS TERMINATED BY ',' OPTIONALLY ENCLOSED BY '"'
 LINES TERMINATED BY '\n'
 FROM test_table;
The file is created on the MySQL server host, not the client host. For this statement, the output file cannot 
already exist because permitting files to be overwritten constitutes a security risk. This method works for any kind of 
data file, but saves only table data, not the table structure.
To reload a delimited-text data file, use LOAD DATA INFILE or mysqlimport., will cover in later sections.
mysqlhotcopy — A Database Backup Program
It uses FLUSH TABLES, LOCK TABLES, and cp or scp to make a database backup. It is a fast way to make a 
backup of the database or single tables, but it can be run only on the same machine where the database directories 
are located. mysqlhotcopy works only for backing up MyISAM and ARCHIVE tables. It runs on Unix.
To use mysqlhotcopy, you must have read access to the files for the tables that you are backing up, the 
SELECT privilege for those tables, the RELOAD privilege (to be able to execute FLUSH TABLES), and the LOCK 
TABLES privilege (to be able to lock the tables). 
shell> mysqlhotcopy db_name [/path/to/new_directory]
shell> mysqlhotcopy db_name_1 ... db_name_n /path/to/new_directory
11.3. Using mysqldump for Backups:
11.3.1. Dumping Data in SQL Format:
This section describes how to use mysqldump to produce dump files, and how to reload dump files. A dump 
file can be used in several ways:
− As a backup to enable data recovery in case of data loss.
− As a source of data for setting up replication slaves.
There are three general ways to invoke mysqldump:
shell> mysqldump [options] db_name [tbl_name ...]
shell> mysqldump [options] --databases db_name ...
shell> mysqldump [options] --all-databases
By default, mysqldump writes information as SQL statements to the standard output. You can save the output in a 
file:
shell> mysqldump [arguments] > file_name
To dump all databases, invoke mysqldump with the --all-databases option:
shell> mysqldump --all-databases > dump.sql
To dump only specific databases, name them on the command line and use the --databases option:
shell> mysqldump --databases db1 db2 db3 > dump.sql
The --databases option causes all names on the command line to be treated as database names. Without this 
option, mysqldump treats the first name as a database name and those following as table names.
With --all-databases or --databases, mysqldump writes CREATE DATABASE and USE statements prior to the 
dump output for each database. This ensures that when the dump file is reloaded, it creates each database if it 
does not exist and makes it the default database so database contents are loaded into the same database from 
which they came.
To dump a single database, name it on the command line:
shell> mysqldump --databases test > dump.sql
MySQL Database Administration
 64 
In the single-database case, it is permissible to omit the --databases option:
shell> mysqldump test > dump.sql
To dump only specific tables from a database, name them on the command line following the database name:
shell> mysqldump test t1 t3 t7 > dump.sql
mysqldump does not dump the INFORMATION_SCHEMA database by default. As of MySQL 5.1.38, 
mysqldump dumps INFORMATION_SCHEMA if you name it explicitly on the command line, although you must 
also use the --skip-lock-tables option. Before 5.1.38, mysqldump silently ignores INFORMATION_SCHEMA even if 
you name it explicitly on the command line.
Use of --opt is the same as specifying --add-drop-table, --add-locks, --create-options, --disable-keys, --
extended-insert, --lock-tables, --quick, and --set-charset. All of the options that --opt stands for also are on by 
default because --opt is on by default.
To select the effect of --opt except for some features, use the --skip option for each feature. To disable 
extended inserts and memory buffering, use --opt --skip-extended-insert --skip-quick.
Use of --compact is the same as specifying --skip-add-drop-table, --skip-add-locks, --skip-comments,--skipdisable-keys, and --skip-set-charset options.
Options:
--add-drop-database Add a DROP DATABASE statement before each CREATE DATABASE statement.
--add-drop-table Add a DROP TABLE statement before each CREATE TABLE statement.
--add-drop-trigger Add a DROP TRIGGER statement before each CREATE TRIGGER statement.
--add-locks Surround each table dump with LOCK TABLES and UNLOCK TABLES statements.
--all-databases Dump all tables in all databases.
--complete-insert Use complete INSERT statements that include column names.
--databases To dump several databases.
--disable-keys For each table, surround the INSERT statements with statements to disable and 
enable keys.
--dump-date Include dump date as "Dump completed on" comment if --comments is given
--extended-insert Use multiple-row INSERT syntax that include several VALUES lists
--tab=path Produce tab-separated data files
--fields-enclosed-by=string This option is used with the --tab option and has the same meaning as the 
corresponding clause for LOAD DATA INFILE
--fields-terminated-by=string This option is used with the --tab option and has the same meaning as the 
corresponding clause for LOAD DATA INFILE
--flush-logs Flush the MySQL server log files before starting the dump
--no-create-db This option suppresses the CREATE DATABASE statements
--no-create-info Do not write CREATE TABLE statements that re-create each dumped table.
--no-data Do not dump table contents.
--opt Shorthand for --add-drop-table --add-locks --create-options --disable-keys 
--extended-insert --lock-tables --quick –set-charset.
--routines Dump stored routines (procedures and functions) from the dumped databases
--skip-trigers Do not dump triggers.
--skip-add-drop-table Do not add a DROP TABLE statement before each CREATE TABLE statement
--skip-extended-insert Turn off extended-insert
MySQL Database Administration
 65 
--tables Override the --databases or -B option
--lock-all-tables
Lock all tables across all databases. This is achieved by acquiring a global read lock for the duration of the 
whole dump. This option automatically turns off --single-transaction and --lock-tables.
--lock-tables, -l
For each dumped database, lock all tables to be dumped before dumping them. The tables are locked 
with READ LOCAL to permit concurrent inserts in the case of MyISAM tables.
--master-data[=value]
Use this option to dump a master replication server to produce a dump file that can be used to set up another 
server as a slave of the master. It causes the dump output to include a CHANGE MASTER TO statement. If the 
option value is 2, the CHANGE MASTER TO statement is written as an SQL comment, and thus is informative only; 
it has no effect when the dump file is reloaded. If the option value is 1, the statement is not written as a comment 
and takes effect when the dump file is reloaded. If no option value is specified, the default value is 1. It 
automatically also turns on --lock-all-tables.
--compact
Produce more compact output. This option enables the --skip-add-drop-table, --skip-add-locks, --skipcomments, --skip-disable-keys, and --skip-set-charset options.
11.3.2. Dumping Data in Delimited-Text Format with mysqldump:
If you invoke mysqldump with the --tab=dir_name option, it uses dir_name as the output directory and dumps 
tables individually in that directory using two files for each table. The table name is the basename for these files. 
For a table named t1, the files are named t1.sql and t1.txt. The .sql file contains a CREATE TABLE statement for 
the table. The .txt file contains the table data, one line per table row.
The following command dumps the contents of the db1 database to files in the /tmp database:
shell> mysqldump --tab=/tmp db1
It is best that --tab be used only for dumping a local server. If you use it with a remote server, the --tab
directory must exist on both the local and remote hosts, and the .txt files will be written by the server in the remote 
directory (on the server host), whereas the .sql files will be written by mysqldump in the local directory.
11.3.3. Reloading SQL-Format Backups:
To reload a dump file written by mysqldump that consists of SQL statements, use it as input to the mysql 
client.
− When you reload the dump file, you must specify a default database name so that the server knows 
which database to reload.
− For reloading, you can specify a database name different from the original name, which enables you to 
reload the data into a different database.
− If the database to be reloaded does not exist, you must create it first.
If the dump file was created by mysqldump with the --all-databases or --databases option, it contains CREATE 
DATABASE and USE statements and it is not necessary to specify a default database into which to load the data:
shell> mysql < dump.sql
Alternatively, from within mysql, use a source command:
mysql> source dump.sql
If the file is a single-database dump not containing CREATE DATABASE and USE statements, create the database 
first Then specify the database name when you load the dump file:
shell> mysql db1 < dump.sql
MySQL Database Administration
 66 
Alternatively, from within mysql, create the database, select it as the default database, and load the dump file:
mysql> CREATE DATABASE IF NOT EXISTS db1;
mysql> USE db1;
mysql> source dump.sql
Reloading Delimited-Text Format Backups:
For backups produced with mysqldump --tab, each table is represented in the output directory by an .sql file 
containing the CREATE TABLE statement for the table, and a .txt file containing the table data. To reload a table, 
first change location into the output directory. Then process the .sql file with mysql to create an empty table and 
process the .txt file to load the data into the table:
shell> mysql db1 < t1.sql
shell> mysqlimport db1 t1.txt
An alternative to using mysqlimport to load the data file is to use the LOAD DATA INFILE statement from 
within the mysql client:
mysql> USE db1;
mysql> LOAD DATA [LOCAL] INFILE 't1.txt' INTO TABLE t1;
If you used any data-formatting options with mysqldump when you initially dumped the table, you must use the 
same options with mysqlimport or LOAD DATA INFILE to ensure proper interpretation of the data file contents:
shell> mysqlimport –fields-terminated-by=, --fields-enclosed-by='"' --lines-terminated-by=0x0d0a db1 t1.txt
Or:
mysql> USE db1;
mysql> LOAD DATA INFILE 't1.txt' INTO TABLE t1 FIELDS TERMINATED BY ',' FIELDS ENCLOSED BY '"' LINES 
TERMINATED BY '\r\n';
Point-in-Time (Incremental) Recovery Using the Binary Log
Point-in-time recovery is based on these principles: 
The source of information for point-in-time recovery is the set of incremental backups represented by the 
binary log files generated subsequent to the full backup operation. Therefore, the server must be started with the --
log-bin option to enable binary logging. To restore data from the binary log, you must know the name and location 
of the current binary log files.
suppose that exactly at 10:00 a.m. on April 20, 2005 an SQL statement was executed that deleted a large 
table. To restore the table and data, you could restore the previous night's backup, and then execute the following 
command: 
shell> mysqlbinlog --stop-datetime="2005-04-20 9:59:59" \
 /var/log/mysql/bin.123456 | mysql -u root -p
If you did not detect the erroneous SQL statement that was entered until hours later, you will probably also 
want to recover the activity that occurred afterward. Based on this, you could run mysqlbinlog again with a start 
date and time, like so: 
shell> mysqlbinlog --start-datetime="2005-04-20 10:01:00" \
 /var/log/mysql/bin.123456 | mysql -u root -p
Forcing InnoDB Recovery:
If there is database page corruption, you may want to dump your tables from the database with SELECT INTO 
... OUTFILE.Usually, most of the data obtained in this way is intact. However, it is possible that the corruption might 
cause SELECT * FROM tbl_name statements or InnoDB background operations to crash or assert, or even cause 
InnoDB roll-forward recovery to crash. In such cases, you can use the innodb_force_recovery option to force the 
InnoDB storage engine to start up while preventing background operations from running, so that you are able to 
dump your tables. For example, you can add the following line to the [mysqld] section of your option file before 
MySQL Database Administration
 67 
restarting the server:
[mysqld]
innodb_force_recovery = 4
innodb_force_recovery is 0 by default (normal startup without forced recovery) The permissible nonzero 
values for innodb_force_recovery follow. A larger number includes all precautions of smaller numbers. If you are 
able to dump your tables with an option value of at most 4, then you are relatively safe that only some data on 
corrupt individual pages is lost. A value of 6 is more drastic because database pages are left in an obsolete state, 
which in turn may introduce more corruption into B-trees and other database structures.
1 (SRV_FORCE_IGNORE_CORRUPT)
Let the server run even if it detects a corrupt page. Try to make SELECT * FROM tbl_name jump over corrupt index 
records and pages, which helps in dumping tables.
2 (SRV_FORCE_NO_BACKGROUND)
Prevent the main thread from running. If a crash would occur during the purge operation, this recovery value 
prevents it.
3 (SRV_FORCE_NO_TRX_UNDO)
Do not run transaction rollbacks after recovery.
4 (SRV_FORCE_NO_IBUF_MERGE)
Prevent insert buffer merge operations. If they would cause a crash, do not do them. Do not calculate table 
statistics.
5 (SRV_FORCE_NO_UNDO_LOG_SCAN)
Do not look at undo logs when starting the database: InnoDB treats even incomplete transactions as committed.
6 (SRV_FORCE_NO_LOG_REDO)
Do not do the log roll-forward in connection with recovery. The database must not otherwise be used with any 
nonzero value of innodb_force_recovery. As a safety measure, InnoDB prevents users from performing INSERT, 
UPDATE, or DELETE operations when innodb_force_recovery is greater than 0.
You can SELECT from tables to dump them, or DROP or CREATE tables even if forced recovery is used. If 
you know that a given table is causing a crash on rollback, you can drop it. You can also use this to stop a runaway 
rollback caused by a failing mass import or ALTER TABLE. You can kill the mysqld process and set 
innodb_force_recovery to 3 to bring the database up without the rollback, then DROP the table that is causing the 
runaway rollback.
12. Running Multiple MySQL Instances on One Machine
In some cases, you might want to run multiple instances of MySQL on a single machine. You might want to 
test a new MySQL release while leaving an existing production setup undisturbed. Or you might want to give 
different users access to different mysqld servers that they manage themselves.
It is possible to use a different MySQL server binary per instance, or use the same binary for multiple 
instances, or any combination of the two approaches. For example, you might run a server from MySQL 5.0 and 
one from MySQL 5.1, to see how different versions handle a given workload. Or you might run multiple instances of 
the current production version, each managing a different set of databases.
Whether or not you use distinct server binaries, each instance that you run must be configured with unique 
values for several operating parameters. This eliminates the potential for conflict between instances.
12.1. Setting Up Multiple Data Directories
Each MySQL Instance on a machine should have its own data directory. The location is specified using the --
datadir=path option.
There are different methods of setting up a data directory for a new instance:
− Create a new data directory
− Copy an existing data directory
Note: Normally, you should never have two servers that update data in the same databases. This may lead to 
MySQL Database Administration
 68 
unpleasant surprises if your operating system does not support fault-free system locking. If (despite this warning) 
you run multiple servers using the same data directory and they have logging enabled, you must use the 
appropriate options to specify log file names that are unique to each server. Otherwise, the servers try to log to the 
same files.
Create a New Data Directory:
With this method, the data directory will be in the same state as when you first install MySQL. It will have the 
default set of MySQL accounts and no user data.On Unix, initialize the data directory by running mysql_install_db.
Copy an Existing Data Directory:
With this method, any MySQL accounts or user data present in the data directory are carried over to the new 
data directory.
1.Stop the existing MySQL instance using the data directory. This must be a clean shutdown so that the 
instance flushes any pending changes to disk.
2.Copy the data directory to the location where the new data directory should be.
3.Copy the my.cnf or my.ini option file used by the existing instance. This serves as a basis for the new 
instance.
4.Modify the new option file so that any pathnames referring to the original data directory refer to the new data 
directory. Also, modify any other options that must be unique per instance, such as the TCP/IP port number 
and the log files.
5.Start the new instance, telling it to use the new option file.
12.2. Running Multiple MySQL Instances on Unix:
One way is to run multiple MySQL instances on Unix is to compile different servers with different default 
TCP/IP ports and Unix socket files so that each one listens on different network interfaces. Compiling in different 
base directories for each installation also results automatically in a separate, compiled-in data directory, log file, and 
PID file location for each server. 
Assume that an existing 5.0 server is configured for the default TCP/IP port number (3306) and Unix socket 
file (/tmp/mysql.sock). To configure a new 5.1.57 server to have different operating parameters, use a configure 
command something like this:
shell> ./configure --with-tcp-port=port_number \
--with-unix-socket-path=file_name \
--prefix=/usr/local/mysql-5.1.57
Here, port_number and file_name must be different from the default TCP/IP port number and Unix socket file 
path name, and the --prefix value should specify an installation directory different from the one under which the 
existing MySQL installation is located.
If you have a MySQL server listening on a given port number, you can use the following command to find out 
what operating parameters it is using for several important configurable variables, including the base directory and 
Unix socket file name:
shell> mysqladmin --host=host_name --port=port_number variables
You need not compile a new MySQL server just to start with a different Unix socket file and TCP/IP port 
number. It is also possible to use the same server binary and start each invocation of it with different parameter 
values at runtime. One way to do so is by using command-line options:
shell> mysqld_safe --socket=file_name --port=port_number
To start a second server, provide different --socket and --port option values, and pass a –datadir=path option to 
mysqld_safe so that the server uses a different data directory.
Alternatively, put the options for each server in a different option file, then start each server using a --defaultsfile option that specifies the path to the appropriate option file. For example, if the option files for two server 
instances are named /usr/local/mysql/my.cnf and /usr/local/mysql/my.cnf2, start the servers like this: command:
MySQL Database Administration
 69 
shell> mysqld_safe --defaults-file=/usr/local/mysql/my.cnf
shell> mysqld_safe --defaults-file=/usr/local/mysql/my.cnf2
Using Client Programs in a Multiple-Server Environment:
To connect with a client program to a MySQL server that is listening to different network interfaces from those 
compiled into your client, you can use one of the following methods:
− Start the client with --host=host_name --port=port_number to connect using TCP/IP to a remote server, 
with --host=127.0.0.1 --port=port_number to connect using TCP/IP to a local server, or with --
host=localhost --socket=file_name to connect to a local server using a Unix socket file.
MySQL Instance Manager
MySQL Instance Manager is been deprecated in MySQL 5.1 and is removed in MySQL 5.5.
12.3. Using mysqld_multi for Managing Multiple MySQL Servers
mysqld_multi is designed to manage several mysqld processes that listen for connections on different Unix 
socket files and TCP/IP ports. It can start or stop servers, or report their current status.
mysqld_multi searches for groups named [mysqldN] in my.cnf (or in the file named by the --config-file option). 
N can be any positive integer. This number is referred to in the following discussion as the option group number, or 
GNR. 
1.Initialize the new datadir.
2.Change the option file.
Sample Option file is as below:
[mysqld_multi]
mysqld = /usr/local/bin/mysqld_safe
mysqladmin = /usr/local/bin/mysqladmin
user = multi_admin
password = multipass
[mysqld2]
socket = /tmp/mysql.sock2
port = 3307
pid-file = /usr/local/mysql/var2/hostname.pid2
datadir = /usr/local/mysql/var2
language = /usr/local/share/mysql/english
user = john
[mysqld3]
socket = /tmp/mysql.sock3
port = 3308
pid-file = /usr/local/mysql/var3/hostname.pid3
datadir = /usr/local/mysql/var3
language = /usr/local/share/mysql/swedish
user = monty
To invoke mysqld_multi, use the following syntax: 
shell> mysqld_multi [options] {start|stop|report} [GNR[,GNR] ...]
start, stop, and report indicate which operation to perform. You can perform the designated operation for a 
single server or multiple servers, depending on the GNR list that follows the option name. If there is no list, 
mysqld_multi performs the operation for all servers in the option file. 
Each GNR value represents an option group number or range of group numbers. The value should be the 
number at the end of the group name in the option file. For example, the GNR for a group named [mysqld17] is 17. 
To specify a range of numbers, separate the first and last numbers by a dash. The GNR value 10-13 represents 
groups [mysqld10] through [mysqld13]. Multiple groups or group ranges can be specified on the command line, 
separated by commas.
MySQL Database Administration
 70 
This command starts a single server using option group [mysqld17]: 
shell> mysqld_multi start 17
This command stops several servers, using option groups [mysqld8] and [mysqld10] through [mysqld13]: 
shell> mysqld_multi stop 8,10-13
For an example of how you might set up an option file, use this command: 
shell> mysqld_multi --example
Options:
--example Display a sample option file. 
--mysqladmin=prog_name The mysqladmin binary to be used to stop servers. 
--mysqld=prog_name The mysqld binary to be used.
--password=password The password of the MySQL account to use when invoking mysqladmin.
--user=user_name The user name of the MySQL account to use when invoking mysqladmin. 
13. General Security Guidelines
− Do not ever give anyone (except MySQL root accounts) access to the user table in the mysql 
database! This is critical.
− Learn the MySQL access privilege system. The GRANT and REVOKE statements are used for 
controlling access to MySQL. Do not grant more privileges than necessary. Never grant privileges to all 
hosts.
− Do not store any plaintext passwords in your database. Instead, use MD5(), SHA1(), or some other 
one-way hashing function and store the hash value.
− Invest in a firewall. This protects you from at least 50% of all types of exploits in any software. Put 
MySQL behind the firewall or in a demilitarized zone.
− See what are the privileges provided by the MySQL.
14. Optimization
Optimization is a complex task because ultimately it requires understanding of the entire system to be 
optimized. Although it may be possible to perform some local optimizations with little knowledge of your system or 
application, the more optimal you want your system to become, the more you must know about it.
14.1 Optimization Overview
The most important factor in making a system fast is its basic design. You must also know what a kind of 
processing your system is doing, and what its bottlenecks are. In most cases, system bottlenecks arise from these 
sources:
Disk seeks: It takes time for the disk to find a piece of data. With modern disks, the mean time for this is usually 
lower than 10ms, so we can in theory do about 100 seeks a second. This time improves slowly with new disks and 
is very hard to optimize for a single table. The way to optimize seek time is to distribute the data onto more than 
one disk. 
Disk reading and writing: When the disk is at the correct position, we need to read the data. With modern disks, 
one disk delivers at least 10–20MB/s throughput. This is easier to optimize than seeks because you can read in 
parallel from multiple disks. 
CPU cycles: When we have the data in main memory, we need to process it to get our result. Having small tables 
compared to the amount of memory is the most common limiting factor. But with small tables, speed is usually not 
the problem.
MySQL Database Administration
 71 
14.2 Obtaining Query Execution Plan Information
14.2.1. Optimizing Queries with EXPLAIN
The EXPLAIN statement can be used either as a way to obtain information about how MySQL executes a 
SELECT statement or as a synonym for DESCRIBE.
− When you precede a SELECT statement with the keyword EXPLAIN, MySQL displays information from 
the optimizer about the query execution plan. That is, MySQL explains how it would process the 
SELECT, including information about how tables are joined and in which order.
− EXPLAIN PARTITIONS is available beginning with MySQL 5.1.5. It is useful only when examining 
queries involving partitioned tables.
− EXPLAIN tbl_name is synonymous with DESCRIBE tbl_name or SHOW COLUMNS FROM tbl_name.
If you have a problem with indexes not being used when you believe that they should be, you should run 
ANALYZE TABLE to update table statistics such as cardinality of keys, that can affect the choices the optimizer 
makes.
EXPLAIN Output Format:
EXPLAIN returns a row of information for each table used in the SELECT statement. The tables are listed in 
the output in the order that MySQL would read them while processing the query. MySQL resolves all joins using a 
nested-loop join method. This means that MySQL reads a row from the first table, and then finds a matching row in 
the second table, the third table, and so on. When all tables are processed, MySQL outputs the selected columns 
and backtracks through the table list until a table is found for which there are more matching rows. The next row is 
read from this table and the process continues with the next table.
Example:
mysql> EXPLAIN SELECT * FROM tbl_a a, tbl_b b where a.id = b.id;
+----+---------------+-------+-----------+-------------------+--------------+------------+--------+------+-------+
| id | select_type | table | type | possible_keys | key | key_len | ref | rows | Extra |
+----+---------------+-------+-----------+-------------------+--------------+------------+--------+------+-------+
| 1 | SIMPLE | b | system | PRIMARY | NULL | NULL | NULL | 1 | |
| 1 | SIMPLE | a | const | PRIMARY | PRIMARY | 8 | const | 1 | |
+----+---------------+-------+-----------+-------------------+--------------+------------+---------+------+-------+
14.2.2. Optimizing SELECT Statements
First, one factor affects all statements: The more complex your permissions setup, the more overhead you 
have. Using simpler permissions when you issue GRANT statements enables MySQL to reduce permissionchecking overhead when clients execute statements. For example, if you do not grant any table-level or columnlevel privileges, the server need not ever check the contents of the tables_priv and columns_priv tables. Similarly, if 
you place no resource limits on any accounts, the server does not have to perform resource counting. If you have a 
very high statement-processing load, it may be worth the time to use a simplified grant structure to reduce 
permission-checking overhead.
If your problem is with a specific MySQL expression or function, you can perform a timing test by invoking the 
BENCHMARK() function using the mysql client program. Its syntax is
Syntax:
mysql > BENCHMARK(loop_count,expression);
The return value is always zero, but mysql prints a line displaying approximately how long the statement took to 
execute. For example:
mysql> SELECT BENCHMARK(1000000,1+1);
+---------------------------------------+
| BENCHMARK(1000000,1+1) |
+---------------------------------------+
| 0 |
+---------------------------------------+
1 row in set (0.32 sec)
MySQL Database Administration
 72 
It shows that MySQL can execute 1,000,000 simple addition expressions in 0.32 seconds on that system.
Speed of SELECT Statements:
In general, when you want to make a slow SELECT ... WHERE query faster, the first thing to check is whether 
you can add an index. You can use the EXPLAIN statement to determine which indexes are used for a SELECT. 
Some general tips for speeding up queries on MyISAM tables:
− To help MySQL better optimize queries, use ANALYZE TABLE or run myisamchk --analyze on a table 
after it has been loaded with data. This updates a value for each index part that indicates the average 
number of rows that have the same value. (For unique indexes, this is always 1.) MySQL uses this to 
decide which index to choose when you join two tables based on a nonconstant expression. You can 
check the result from the table analysis by using SHOW INDEX FROM tbl_name and examining the 
Cardinality value.
− To sort an index and data according to an index, use myisamchk --sort-index (assuming that you want 
to sort on index 1). This is a good way to make queries faster if you have a unique index from which 
you want to read all rows in order according to the index. The first time you sort a large table this way, it 
may take a long time.
WHERE Clause Optimization:
This section discusses optimizations that can be made for processing WHERE clauses. The examples use 
SELECT statements, but the same optimizations apply for WHERE clauses in DELETE and UPDATE statements. 
Removal of unnecessary parentheses:
((a AND b) AND c OR (((a AND b) AND (c AND d))))
=> (a AND b AND c) OR (a AND b AND c AND d)
Constant folding:
(a<b AND b=c) AND a=5
=> b>5 AND b=c AND a=5
In some cases, MySQL can read rows from the index without even consulting the data file. If all columns used 
from the index are numeric, only the index tree is used to resolve the query.
Remove non key columns in WHERE clause.
Should not use IN, LIKE operators.
Avoid sub queries and queries in FROM clause.
Use functions in the left side of the condition.
Should not use DISTINCT clause, instead use GROUP BY clause.
Do not create duplicate indexes.
14.3. Tuning Server Parameters
For a mysqld server that is currently running, you can see the current values of its system variables by 
connecting to it and issuing this statement:
mysql> SHOW VARIABLES;
You can also see some statistical and status indicators for a running server by issuing this statement:
mysql> SHOW STATUS;
System variable and status information also can be obtained using mysqladmin:
shell> mysqladmin variables
shell> mysqladmin extended-status
When tuning a MySQL server, the two most important variables to configure are key_buffer_size and 
table_open_cache. You should first feel confident that you have these set appropriately before trying to change any 
MySQL Database Administration
 73 
other variables.
If you are performing GROUP BY or ORDER BY operations on tables that are much larger than your available 
memory, you should increase the value of read_rnd_buffer_size to speed up the reading of rows following sorting 
operations.
Temp variables:
You can compare the number of internal on-disk temporary tables created to the total number of internal 
temporary tables created by comparing the values of the Created_tmp_disk_tables and Created_tmp_tables 
variables. 
Server variable : tmp_table_size (Need to be increased depending upon the below values)
Status variables : Created_tmp_disk_tables, Created_tmp_tables.
Query Cache:
The cache is not used for queries of the following types: 
1. Queries that are a subquery of an outer query 
2. Queries executed within the body of a stored function, trigger, or event 
A query cannot be cached if it contains any of the functions like CURDATE(), NOW(), CONVERT_TZ(), 
CURTIME(), DATABASE(), RAND(), UUID() etc.
A query also is not cached under these conditions: 
1.It refers to tables in the mysql or INFORMATION_SCHEMA system database.
2.SELECT ... INTO OUTFILE.
3.It uses TEMPORARY tables. 
4.It does not use any tables. 
5.It generates warnings. 
Two query cache-related options may be specified in SELECT statements: 
SQL_CACHE
The query result is cached if it is cacheable and the value of the query_cache_type system variable is ON or 
DEMAND.
SQL_NO_CACHE
The query result is not cached. 
Examples: 
SELECT SQL_CACHE id, name FROM customer;
SELECT SQL_NO_CACHE id, name FROM customer;
Query Cache Configuration:
The have_query_cache server system variable indicates whether the query cache is available: 
mysql> SHOW VARIABLES LIKE 'have_query_cache';
+--------------------------+--------+
| Variable_name | Value |
+--------------------------+--------+
| have_query_cache | YES |
+--------------------------+--------+
To set the size of the query cache, set the query_cache_size system variable. Setting it to 0 disables the 
query cache. The default size is 0, so the query cache is disabled by default. 
If the query cache size is greater than 0, the query_cache_type variable influences how it works. This variable can 
be set to the following values: 
1.A value of 0 or OFF prevents caching or retrieval of cached results.
MySQL Database Administration
 74 
2.A value of 1 or ON enables caching except of those statements that begin with SELECT SQL_NO_CACHE.
3.A value of 2 or DEMAND causes caching of only those statements that begin with SELECT SQL_CACHE. 
Individual clients can control cache behavior for their own connection by setting the SESSION 
query_cache_type value. For example, a client can disable use of the query cache for its own queries like this: 
mysql> SET SESSION query_cache_type = 0;
When a query is to be cached, its result (the data sent to the client) is stored in the query cache during result 
retrieval. Therefore the data usually is not handled in one big chunk. The query cache allocates blocks for storing 
this data on demand, so when one block is filled, a new block is allocated. Because memory allocation operation is 
costly (timewise), the query cache allocates blocks with a minimum size given by the query_cache_min_res_unit 
system variable. When a query is executed, the last result block is trimmed to the actual data size so that unused 
memory is freed. Depending on the types of queries your server executes, you might find it helpful to tune the value 
of query_cache_min_res_unit: 
− The default value of query_cache_min_res_unit is 4KB. This should be adequate for most cases.
− If most of your queries have large results (check the Qcache_total_blocks and 
Qcache_queries_in_cache status variables), you can increase performance by increasing 
query_cache_min_res_unit. However, be careful to not make it too large
The RESET QUERY CACHE statement, to removes all query results from the query cache execute the 
FLUSH TABLES statement.
Status variables:
Qcache_free_blocks
The number of free memory blocks in the query cache. 
qcache_hits
Whenever MySQL performs a SELECT operation, it either increments com_select or the qcache_hits status 
variables. com_selects thus show us the cache misses. 
So get the hit ratio by this formula: qcache_hits / (qcache_hits + com_select) which gives us .9999 or 99.99%.
Qcache_inserts 
The number of queries added to the query cache. 
Qcache_lowmem_prunes 
The number of queries that were deleted from the query cache because of low memory. 
Qcache_not_cached
The number of noncached queries (not cacheable, or not cached due to the query_cache_type setting). 
The information provided by the Qcache_lowmem_prunes status variable can help you tune the query cache 
size. It counts the number of queries that have been removed from the cache to free up memory for caching new 
queries. The query cache uses a least recently used (LRU) strategy to decide which queries to remove from the 
cache.
Other Optimizations:
sort_buffer_size
If you see many Sort_merge_passes per second in SHOW GLOBAL STATUS output, you can consider 
increasing the sort_buffer_size value to speed up ORDER BY or GROUP BY operations that cannot be improved 
with query optimization or improved indexing. The entire buffer is allocated even if it is not all needed, so setting it 
larger than required globally will slow down most queries that sort.
myisam_sort_buffer_size
 The size of the buffer that is allocated when sorting MyISAM indexes during a REPAIR TABLE or when creating 
indexes with CREATE INDEX or ALTER TABLE.
thread_cache_size
How many threads the server should cache for reuse. When a client disconnects, the client's threads are put 
in the cache if there are fewer than thread_cache_size threads there. Requests for threads are satisfied by reusing 
threads taken from the cache if possible, and only when the cache is empty is a new thread created. By examining 
the difference between the Connections and Threads_created status variables, you can see how efficient the 
MySQL Database Administration
 75 
thread cache is.
wait_timeout
The number of seconds the server waits for activity on a noninteractive connection before closing it.
15. Partitioning
15.1. Overview of Partitioning in MySQL
A partition is a division of a logical database or its constituting elements into distinct independent parts. 
Database partitioning is normally done for manageability, performance reasons.
The partitioning can be done by either building separate smaller databases, or by splitting selected elements, 
for example just one table.
Partitioning enables you to distribute portions of individual tables across a file system according to rules which 
you can set largely as needed.In effect, different portions of a table are stored as separate tables in different 
locations. The user-selected rule by which the division of data is accomplished is known as a partitioning function, 
which in MySQL can be the modulus, simple matching against a set of ranges or value lists, an internal hashing 
function, or a linear hashing function. The function is selected according to the partitioning type specified by the 
user. 
In MySQL 5.1, all partitions of the same partitioned table must use the same storage engine; for example, you 
cannot use MyISAM for one partition and InnoDB for another. However, there is nothing preventing you from using 
different storage engines for different partitioned tables.
15.1. Partitioning Types
This section discusses the types of partitioning which are available in MySQL 5.1.
1.RANGE Partitioning 
2.LIST Partitioning 
3.HASH Partitioning 
4.KEY Partitioning 
RANGE Partitioning:
RANGE partitioning contains rows for which the partitioning expression value lies within a given range. 
Ranges should be contiguous but not overlapping, and are defined using the VALUES LESS THAN operator. 
Suppose if you are creating a table to hold the employee details as below:
CREATE TABLE employees (
 id INT NOT NULL,
 fname VARCHAR(30),
 lname VARCHAR(30),
 hired DATE NOT NULL DEFAULT '1970-01-01',
 dept_id INT NOT NULL
);
This table can be partitioned by range in a number of ways, depending on your needs. One way would be to 
use the dept_id column. For instance, you might decide to partition the table 4 ways by adding a PARTITION BY 
RANGE clause as shown here: 
CREATE TABLE employees (
 id INT NOT NULL,
 fname VARCHAR(30),
 lname VARCHAR(30),
 hired DATE NOT NULL DEFAULT '1970-01-01',
 dept_id INT NOT NULL
) engine = myisam
PARTITION BY RANGE (dept_id) (
 PARTITION p0 VALUES LESS THAN (6),
MySQL Database Administration
 76 
 PARTITION p1 VALUES LESS THAN (11),
 PARTITION p2 VALUES LESS THAN (16),
 PARTITION p3 VALUES LESS THAN (21)
);
In this partitioning scheme, all rows corresponding to employees working at dept 1 through 5 are stored in 
partition p0, to those employed at dept 6 through 10 are stored in partition p1, and so on. Note that each partition is 
defined in order, from lowest to highest. This is a requirement of the PARTITION BY RANGE syntax; you can think 
of it as being analogous to a series of if ... elseif ... statements in C or Java in this regard.
It is easy to determine that a new row containing the data (72, 'Michael', 'Widenius', '1998-06-25' 13) is 
inserted into partition p2, but what happens when your chain adds a 21st dept_id? Under this scheme, there is no 
rule that covers a row whose dept_id is greater than 20, so an error results because the server does not know 
where to place it. You can keep this from occurring by using a “catchall” VALUES LESS THAN clause in the 
CREATE TABLE statement that provides for all values greater than the highest value explicitly named.
CREATE TABLE employees (
 id INT NOT NULL,
 fname VARCHAR(30),
 lname VARCHAR(30),
 hired DATE NOT NULL DEFAULT '1970-01-01',
 dept_id INT NOT NULL
) engine = myisam
PARTITION BY RANGE (dept_id) (
 PARTITION p0 VALUES LESS THAN (6),
 PARTITION p1 VALUES LESS THAN (11),
 PARTITION p2 VALUES LESS THAN (16),
 PARTITION p3 VALUES LESS THAN MAXVALUE
);
MAXVALUE represents an integer value that is always greater than the largest possible integer value. Now, 
any rows whose dept_id column value is greater than or equal to 16 are stored in partition p3. At some point in the 
future when the number of depts has increased to 25, 30, or more you can use an ALTER TABLE statement to add 
new partitions for stores 21-25, 26-30, and so on.
Rather than splitting up the table data according to dept number, you can use an expression based DATE 
column instead. For example, let us suppose that you wish to partition based on the year that each employee 
joined the company. An example of a CREATE TABLE statement that implements such a partitioning scheme is 
shown here: 
CREATE TABLE employees (
 id INT NOT NULL,
 fname VARCHAR(30),
 lname VARCHAR(30),
 hired DATE NOT NULL DEFAULT '1970-01-01',
 dept_id INT NOT NULL
) engine = myisam
PARTITION BY RANGE ( YEAR(hired) ) (
 PARTITION p0 VALUES LESS THAN (1991),
 PARTITION p1 VALUES LESS THAN (1996),
 PARTITION p2 VALUES LESS THAN (2001),
 PARTITION p3 VALUES LESS THAN MAXVALUE
);
In this scheme, for all employees who joined before 1991, the rows are stored in partition p0; for those who 
joined in the years 1991 through 1995, in p1; for those who joined in the years 1996 through 2000, in p2; and for 
any workers who joined after the year 2000, in p3.
Range partitioning is particularly useful when you want or need to delete “old” data. If you are using the 
partitioning scheme shown immediately above, you can simply use ALTER TABLE employees DROP PARTITION 
p0; to delete all rows relating to employees who stopped working for the firm prior to 1991. For a table with a great 
many rows, this can be much more efficient than running a DELETE query such as DELETE FROM employees 
WHERE YEAR(separated) <= 1990;.
MySQL Database Administration
 77 
LIST Partitioning:
List partitioning in MySQL is similar to range partitioning in many ways. As in partitioning by RANGE, each 
partition must be explicitly defined. The chief difference between the two types of partitioning is that, in list 
partitioning, each partition is defined and selected based on the membership of a column value in one of a set of 
value lists, rather than in one of a set of contiguous ranges of values. This is done by using PARTITION BY 
LIST(expr) where expr is a column value or an expression based on a column value and returning an integer value, 
and then defining each partition by means of a VALUES IN (value_list), where value_list is a comma-separated list 
of integers. 
Unlike the case with partitions defined by range, list partitions do not need to be declared in any particular 
order. 
Suppose if you are creating a table to hold the employee details as below:
CREATE TABLE employees (
 id INT NOT NULL,
 fname VARCHAR(30),
 lname VARCHAR(30),
 hired DATE NOT NULL DEFAULT '1970-01-01',
 dept_id INT NOT NULL
);
Suppose that there are 20 departments distributed among 4 franchises as shown in the following table. 
Branch Dept ID Numbers
B1 3, 5, 6, 9, 17
B2 1, 2, 10, 11, 19, 20
B3 4, 12, 13, 14, 18
B4 7, 8, 15, 16
To partition this table in such a way that rows for departments belonging to the same branch are stored in the 
same partition, you could use the CREATE TABLE statement shown here:
CREATE TABLE employees (
 id INT NOT NULL,
 fname VARCHAR(30),
 lname VARCHAR(30),
 hired DATE NOT NULL DEFAULT '1970-01-01',
 dept_id INT NOT NULL
)
PARTITION BY LIST(dept_id) (
 PARTITION pB1 VALUES IN (3,5,6,9,17),
 PARTITION pB2 VALUES IN (1,2,10,11,19,20),
 PARTITION pB3 VALUES IN (4,12,13,14,18),
 PARTITION pB4 VALUES IN (7,8,15,16)
);
This makes it easy to add or drop employee records relating to specific branch from the table. For instance, 
suppose that all departments in the B3 branch are removed. All rows relating to employees working at particular 
departments in that B3 branch can be deleted with an ALTER TABLE employees DROP PARTITION pB3
statement, which can be executed much more efficiently than the equivalent DELETE statement (DELETE FROM 
employees WHERE dept_id IN (4,12,13,14,18)). However, the ALTER TABLE ... DROP PARTITION statement also 
removes the partition itself from the definition for the table, and you must execute an ALTER TABLE ... ADD 
PARTITION statement to restore the table's original partitioning scheme. (This problem is resolved in MySQL 5.5, 
which adds the ALTER TABLE ... TRUNCATE PARTITION statement for removing all rows from a given partition 
without affecting the table definition.) 
Unlike the case with RANGE partitioning, there is no “catch-all” such as MAXVALUE; all expected values for 
the partitioning expression should be covered in PARTITION ... VALUES IN (...) clauses. An INSERT statement 
containing an unmatched partitioning column value fails with an error, as shown in this example: 
MySQL Database Administration
 78 
mysql> INSERT INTO employees VALUES (101, ‘abc’, ‘xyz’, NOW(), 41);
ERROR 1525 (HY000): Table has no partition for value 41
When inserting multiple rows using a single INSERT statement, any rows coming before the row containing 
the unmatched value are inserted, but any coming after it are not.
HASH Partitioning:
Partitioning by HASH is used primarily to ensure an even distribution of data among a predetermined number 
of partitions. With range or list partitioning, you must specify explicitly into which partition a given column value or 
set of column values is to be stored; with hash partitioning, MySQL takes care of this for you, and you need only 
specify a column value or expression based on a column value to be hashed and the number of partitions into 
which the partitioned table is to be divided. 
To partition a table using HASH partitioning, just append to the CREATE TABLE statement a PARTITION BY 
HASH (expr) clause, where expr is an expression that returns an integer. This can simply be the name of a column 
whose type is one of MySQL's integer types. In addition, you will most likely want to follow this with a PARTITIONS 
num clause, where num is a positive integer representing the number of partitions into which the table is to be 
divided. 
For example, the following statement creates a table that uses hashing on the dept_id column and is divided 
into 4 partitions: 
CREATE TABLE employees (
 id INT NOT NULL,
 fname VARCHAR(30),
 lname VARCHAR(30),
 hired DATE NOT NULL DEFAULT '1970-01-01',
 dept_id INT NOT NULL
)
PARTITION BY HASH(dept_id)
PARTITIONS 4;
If you do not include a PARTITIONS clause, the number of partitions defaults to 1. 
Using the PARTITIONS keyword without a number following it results in a syntax error. 
You can also use an SQL expression that returns an integer for expr. For instance, you might want to partition 
based on the year in which an employee was hired. This can be done as shown here: 
CREATE TABLE employees (
 id INT NOT NULL,
 fname VARCHAR(30),
 lname VARCHAR(30),
 hired DATE NOT NULL DEFAULT '1970-01-01',
 dept_id INT NOT NULL
)
PARTITION BY HASH(YEAR(hired))
PARTITIONS 4;
expr must return a nonconstant, nonrandom integer value (in other words. You should also keep in mind that 
this expression is evaluated each time a row is inserted or updated, this means that very complex expressions may 
give rise to performance issues, particularly when performing operations (such as batch inserts) that affect a great 
many rows at one time. 
When PARTITION BY HASH is used, MySQL determines which partition of num partitions to use based on the 
modulus of the result of the user function. In other words, for an expression expr, the partition in which the record is 
stored is partition number N, where N = MOD(expr, num). Suppose that table t1 is defined as follows, so that it has 
4 partitions: 
CREATE TABLE t1 (col1 INT, col2 CHAR(5), col3 DATE)
 PARTITION BY HASH( YEAR(col3) )
 PARTITIONS 4;
If you insert a record into t1 whose col3 value is '2005-09-15', then the partition in which it is stored is 
MySQL Database Administration
 79 
determined as follows: 
MOD(YEAR('2005-09-01'),4)
= MOD(2005,4)
= 1
KEY Partitioning:
Partitioning by key is similar to partitioning by hash, except that where hash partitioning employs a userdefined expression, the hashing function for key partitioning is supplied by the MySQL server. MySQL Cluster uses 
MD5() for this purpose; for tables using other storage engines, the server employs its own internal hashing function 
which is based on the same algorithm as PASSWORD().
The syntax rules for CREATE TABLE ... PARTITION BY KEY are similar to those for creating a table that is 
partitioned by hash. The major differences are listed here: 
- KEY is used rather than HASH.
- KEY takes only a list of one or more column names. Beginning with MySQL 5.1.5, the column or columns 
used as the partitioning key must comprise part or all of the table's primary key, if the table has one. 
Beginning with MySQL 5.1.6, KEY takes a list of zero or more column names. Where no column name is specified 
as the partitioning key, the table's primary key is used, if there is one. For example, the following CREATE TABLE
statement is valid in MySQL 5.1.6 or later: 
CREATE TABLE k1 (
 id INT NOT NULL PRIMARY KEY,
 name VARCHAR(20)
)
PARTITION BY KEY()
PARTITIONS 2;
If there is no primary key but there is a unique key, then the unique key is used for the partitioning key: 
CREATE TABLE k1 (
 id INT NOT NULL,
 name VARCHAR(20),
 UNIQUE KEY (id)
)
PARTITION BY KEY()
PARTITIONS 2;
In both of these cases, the partitioning key is the id column, even though it is not shown in the output of SHOW 
CREATE TABLE or in the PARTITION_EXPRESSION column of the INFORMATION_SCHEMA.PARTITIONS table
Unlike the case with other partitioning types, columns used for partitioning by KEY are not restricted to integer 
or NULL values. For example, the following CREATE TABLE statement is valid:
CREATE TABLE tm1 (
 s1 CHAR(32) PRIMARY KEY
)
PARTITION BY KEY(s1)
PARTITIONS 10;
Managing partitions:
Range and list partitions are very similar with regard to how the adding and dropping of partitions are handled. 
Tables which are partitioned by hash or by key are very similar to one another with regard to making changes in a 
partitioning setup. 
Dropping a Partition:
Dropping a partition from a table that is partitioned by either RANGE or by LIST can be accomplished using 
the ALTER TABLE statement with a DROP PARTITION clause. 
MySQL Database Administration
 80 
mysql> ALTER TABLE <table_name> DROP PARTITION p2;
It is very important to remember that, when you drop a partition, you also delete all the data that was stored in 
that partition. You can see that this is the case by re-running the previous SELECT query. If you wish to drop all 
data from all partitions while preserving the table definition and its partitioning scheme, use the TRUNCATE TABLE
statement.
If you intend to change the partitioning of a table without losing data, use ALTER TABLE ... REORGANIZE 
PARTITION instead.
You cannot drop partitions from tables that are partitioned by HASH or KEY in the same way that you can from 
tables that are partitioned by RANGE or LIST. However, you can merge HASH or KEY partitions using the ALTER 
TABLE ... COALESCE PARTITION statement.
Adding a Partition:
mysql> ALTER TABLE <table_name> ADD PARTITION (PARTITION p0 VALUES LESS THAN (50));
VALUES LESS THAN value must be strictly increasing for each partition.
Merge partitions: 
mysql> ALTER TABLE <table_name> REORGANIZE PARTITION p0, p1 INTO (PARTITION p01 VALUES LESS 
THAN (10)); 
VALUES LESS THAN value must be strictly 2nd partion MAX VALUE.
REORGANIZE PARTITION can be used by any partitioning type but for hash partitions the new number of 
partitions must be the same as those reorganised.
mysql> ALTER TABLE t1 COALESCE PARTITION 2; 
This command can be used to merge partitions in a hash partition. No data is lost. 
Split partitions:
mysql> ALTER TABLE <table_name> REORGANIZE PARTITION p01 INTO (PARTITION p1 VALUES LESS 
THAN (10), PARTITION p2 VALUES LESS THAN (16)); 
Rebuild partitions: 
mysql> ALTER TABLE <table_name> REBUILD PARTITION p0, p1;
Rebuild the partitions, can be a method to remove fragmentation as an example. 
Optimise, analyse, repair and check partitions 
mysql> ALTER TABLE t1 OPTIMIZE PARTITION (p0, p1);
mysql> ALTER TABLE t1 CHECK PARTITION (p0); 
mysql> ALTER TABLE t1 ANALYZE PARTITION (p0); 
mysql> ALTER TABLE t1 REPAIR PARTITION (p0); 
Restrictions and Limitations on Partitioning:
1. User-defined partitioning and the MERGE storage engine are not compatible. Tables using the MERGE storage 
engine cannot be partitioned.
2. FEDERATED storage engine. Partitioning of FEDERATED tables is not supported.
3. CSV storage engine. Partitioned tables using the CSV storage engine are not supported.
4. Prior to MySQL 5.1.6, tables using the BLACKHOLE storage engine also could not be partitioned. 
5. Partitioning by KEY is the only type of partitioning supported for the NDBCLUSTER storage engine.
MySQL Database Administration
 81 
16. INFORMATION_SCHEMA Tables
INFORMATION_SCHEMA provides access to database metadata. 
Metadata is data about the data, such as the name of a database or table, the data type of a column, or 
access privileges. Other terms that sometimes are used for this information are data dictionary and system catalog. 
INFORMATION_SCHEMA is the information database, the place that stores information about all the other 
databases that the MySQL server maintains. Inside INFORMATION_SCHEMA there are several read-only tables. 
They are actually views, not base tables, so there are no files associated with them.
In effect, we have a database named INFORMATION_SCHEMA, although the server does not create a 
database directory with that name. It is possible to select INFORMATION_SCHEMA as the default database with a 
USE statement, but it is possible only to read the contents of tables. You cannot insert into them, update them, or 
delete from them. 
Example of a statement that retrieves information from INFORMATION_SCHEMA: 
mysql> SELECT table_name, table_type, engine
FROM information_schema.tables
WHERE table_schema = 'db5'
ORDER BY table_name DESC;
The statement requests a list of all the tables in database db5, in reverse alphabetic order, showing just three 
pieces of information: the name of the table, its type, and its storage engine. 
SCHEMATA Table:
This table provides information about databases. 
TABLES Table:
This table provides information about tables in databases.
STATISTICS Table:
This table provides information about table indexes. 
USER_PRIVILEGES Table:
This table provides information about global privileges. This information comes from the mysql.user grant table.
SCHEMA_PRIVILEGES Table:
This table provides information about schema (database) privileges. This information comes from the mysql.db
grant table. 
TABLE_PRIVILEGES Table:
This table provides information about table privileges. This information comes from the mysql.tables_priv grant 
table. 
COLUMN_PRIVILEGES Table:
This table provides information about column privileges. This information comes from the mysql.columns_priv grant 
table. 
TABLE_CONSTRAINTS Table:
This table describes which tables have constraints. 
MySQL Database Administration
 82 
REFERENTIAL_CONSTRAINTS Table:
This table provides information about foreign keys. This table was added in MySQL 5.1.10.
ROUTINES Table:
This table provides information about stored routines (both procedures and functions). his information comes from 
the mysql.proc table. 
VIEWS Table:
This table provides information about views in databases. You must have the SHOW VIEW privilege to access this 
table. 
TRIGGERS Table:
This table provides information about triggers. You must have the SUPER privilege to access this table.
PROFILING Table:
This table provides statement profiling information. Its contents correspond to the information produced by the 
SHOW PROFILES and SHOW PROFILE statements. The table is empty unless the profiling session variable is set 
to 1. 
ENGINES Table:
This table provides information about storage engines. 
PARTITIONS Table:
This table provides information about table partitions. 
GLOBAL_STATUS and SESSION_STATUS Tables:
This tables provide information about server status variables. Their contents correspond to the information 
produced by the SHOW GLOBAL STATUS and SHOW SESSION STATUS statements. This tables were added in 
MySQL 5.1.12.
GLOBAL_VARIABLES and SESSION_VARIABLES Tables:
This tables provide information about server status variables. Their contents correspond to the information 
produced by the SHOW GLOBAL VARIABLES and SHOW SESSION VARIABLES statements. This tables were 
added in MySQL 5.1.12.
PROCESSLIST Table:
The PROCESSLIST table provides information about which threads are running. 
EVENTS Table:
The EVENTS table provides information about scheduled events.
MySQL Profiler:
The SQL Profiler is built into the database server and can be dynamically enabled/disabled via the MySQL 
client utility. To begin profiling one or more SQL queries, simply issue the following command:
mysql> set profiling=1;
Two things happen once you issue this command. First, any query you issue from this point on will be traced 
by the server with various performance diagnostics being created and attached to each distinct query. Second, a 
memory table named profiling is created in the INFORMATION_SCHEMA database for your particular session (not 
viewable by any other MySQL session) that stores all the SQL diagnostic results. This table remains persistent until 
you disconnect from MySQL at which point it is destroyed.
MySQL Database Administration
 83 
Now, simply execute a SQL query:
mysql> SELECT COUNT(*) FROM t1 WHERE broker_id = 2;
+----------+
| count(*) |
+----------+
| 200 |
+----------+
Once the query completes, you can issue the following command to view the SQL profiles that have currently been 
stored for you:
mysql> show profiles;
+----------+-----------------+-----------------------------------------------------------------------+
| Query_ID | Duration | Query |
+----------+-----------------+------------------------------------------------------------------------+
| 0 | 0.00007300 | set profiling=1 |
| 1 | 0.00044700 | SELECT COUNT(*) FROM t1 WHERE broker_id = 2 |
+----------+-----------------+------------------------------------------------------------------------+
You get a quick summary of all your captured SQL plus the total duration that the query took to complete. To 
get the same diagnostic info, you can also query the memory table that holds your statistical information:
mysql> SELECT SUM(duration) FROM information_schema.profiling WHERE query_id = 1;
+-------------------+
| sum(duration) |
+-------------------+
| 0.000447 |
+-------------------+
You can view more detailed diagnostic info about one or more queries that you've profiled. The most basic 
command is one that lists the steps a profiled query went through to satisfy your SQL request, along with each 
step's time:
mysql> show profile for query 1;
+------------------------+----------------+
| Status | Duration |
+------------------------+----------------+
| (initialization) | 0.00006300 |
| Opening tables | 0.00001400 |
| System lock | 0.00000600 |
| Table lock | 0.00001000 |
| init | 0.00002200 |
| optimizing | 0.00001100 |
| statistics | 0.00009300 |
| preparing | 0.00001700 |
| executing | 0.00000700 |
| Sending data | 0.00016800 |
| end | 0.00000700 |
| query end | 0.00000500 |
| freeing items | 0.00001200 |
| closing tables | 0.00000800 |
| logging slow query | 0.00000400 |
+-------------------------+-----------------+
Event Scheduler:
The MySQL Event Scheduler manages the scheduling and execution of events: Tasks that run according to 
schedule. Event support was added in MySQL 5.1.6.
MySQL Events are tasks that run according to a schedule. Therefore, we sometimes refer to them as 
scheduled events. When you create an event, you are creating a named database object containing one or more 
SQL statements to be executed at one or more regular intervals, beginning and ending at a specific date and time. 
Conceptually, this is similar to the idea of the Unix crontab (also known as a “cron job”) or the Windows Task 
Scheduler. 
MySQL Database Administration
 84 
MySQL Events have the following major features and properties: 
− In MySQL 5.1.12 and later, an event is uniquely identified by its name and the schema to which it is 
assigned.
− An event performs a specific action according to a schedule. This action consists of an SQL statement, 
which can be a compound statement in a BEGIN ... END block if desired
− An event's timing can be either one-time or recurrent. A one-time event executes one time only. A 
recurrent event repeats its action at a regular interval.
Event Scheduler Configuration:
Events are executed by a special event scheduler thread; when we refer to the Event Scheduler, we actually 
refer to this thread. When running, the event scheduler thread and its current state can be seen by users having the 
PROCESS privilege in the output of SHOW PROCESSLIST.
The global event_scheduler system variable determines whether the Event Scheduler is enabled and running 
on the server. Beginning with MySQL 5.1.12, it has one of these 3 values, which affect event scheduling as 
described here: 
− OFF: The Event Scheduler is stopped. The event scheduler thread does not run, is not shown in the 
output of SHOW PROCESSLIST, and no scheduled events are executed. OFF is the default value for 
event_scheduler.
− ON: The Event Scheduler is started; the event scheduler thread runs and executes all scheduled 
events. When the Event Scheduler is ON, the event scheduler thread is listed in the output of SHOW 
PROCESSLIST as a daemon process.
− DISABLED: This value renders the Event Scheduler nonoperational. When the Event Scheduler is 
DISABLED, the event scheduler thread does not run (and so does not appear in the output of SHOW
PROCESSLIST). In addition, the Event Scheduler state cannot be changed at runtime. 
It is possible to set the Event Scheduler to DISABLED only at server startup. If event_scheduler is ON or OFF, 
you cannot set it to DISABLED at runtime. Also, if the Event Scheduler is set to DISABLED at startup, you cannot 
change the value of event_scheduler at runtime.
mysql > SET GLOBAL event_scheduler = ON;
To disable the event scheduler, use one of the following two methods: 
− As a command-line option when starting the server:
--event-scheduler=DISABLED
− In the server configuration file (my.cnf, or my.ini on Windows systems), include the line where it will be 
read by the server
event_scheduler=DISABLED
Note: You can issue event-manipulation statements when event_scheduler is set to DISABLED. No warnings or 
errors are generated in such cases (provided that the statements are themselves valid). However, scheduled 
events cannot execute until this variable is set to ON (or 1). Once this has been done, the event scheduler thread 
executes all events whose scheduling conditions are satisfied.
Beginning with MySQL 5.1.17, starting the MySQL server with the --skip-grant-tables option causes 
event_scheduler to be set to DISABLED, overriding any other value set either on the command line or in the my.cnf 
or my.ini file (Bug#26807).
MySQL 5.1.6 and later provides an EVENTS table in the INFORMATION_SCHEMA database. This table can 
be queried to obtain information about scheduled events which have been defined on the server.
Creating Events:
CREATE EVENT <event_name>
ON SCHEDULE [AT] <schedule> [EVERY] <interval> 
 DO
 <event_body>;
Example:
MySQL Database Administration
 85 
CREATE EVENT myevent
 ON SCHEDULE AT CURRENT_TIMESTAMP + INTERVAL 1 HOUR
 DO
 UPDATE myschema.mytable SET mycol = mycol + 1;
The previous statement creates an event named myevent. This event executes once—one hour following its 
creation—by running an SQL statement that increments the value of the myschema.mytable table's mycol column 
by 1. 
The ON SCHEDULE clause determines when, how often, and for how long the event_body defined for the 
event repeats. This clause takes one of two forms: 
− AT timestamp is used for a one-time event. It specifies that the event executes one time only at the 
date and time given by timestamp, which must include both the date and time, or must be an 
expression that resolves to a datetime value.
− To repeat actions at a regular interval, use an EVERY clause. The EVERY keyword is followed by an 
interval as described in the previous discussion of the AT keyword. (+ INTERVAL is not used with 
EVERY.) For example, EVERY 6 WEEK means “every six weeks”. 
CREATE EVENT e_hourly
ON SCHEDULE
 EVERY 1 HOUR
 COMMENT 'Clears out sessions table each hour.'
 DO
 DELETE FROM site_activity.sessions;
More complex compound statements, such as those used in stored routines, are possible in an event.
delimiter |
CREATE EVENT e
 ON SCHEDULE
 EVERY 5 SECOND
 DO
 BEGIN
 DECLARE v INTEGER;
 DECLARE CONTINUE HANDLER FOR SQLEXCEPTION BEGIN END;
 SET v = 0;
 WHILE v < 5 DO
 INSERT INTO t1 VALUES (0);
 UPDATE t2 SET s1 = s1 + 1;
 SET v = v + 1;
 END WHILE;
 END |
delimiter ;
There is no way to pass parameters directly to or from events; however, it is possible to invoke a stored 
routine with parameters within an event: 
CREATE EVENT e_call_myproc
 ON SCHEDULE
 AT CURRENT_TIMESTAMP + INTERVAL 1 DAY
 DO CALL myproc(5, 27);
Alter Event:
Examples:
ALTER EVENT myevent
 ON SCHEDULE
EVERY 12 HOUR;
MySQL Database Administration
 86 
ALTER TABLE myevent
 AT CURRENT_TIMESTAMP + INTERVAL 1 DAY
 DO
 TRUNCATE TABLE myschema.mytable;
To disable myevent, use this ALTER EVENT statement: 
ALTER EVENT myevent DISABLE;
ALTER EVENT myevent RENAME TO yourevent;
You can also move an event to a different database using ALTER EVENT ... RENAME TO ... and 
db_name.event_name notation, as shown here: 
ALTER EVENT olddb.myevent RENAME TO newdb.myevent;
Drop Event:
DROP EVENT [IF EXISTS] event_name;
17. Buffering and Caching
MySQL uses several strategies that cache information in memory buffers to increase performance. Depending 
on your database architecture, you balance the size and layout of these areas, to provide the most performance 
benefit without wasting memory or exceeding available memory.
17.1. The MyISAM Key Cache
To minimize disk I/O, the MyISAM storage engine exploits a strategy that is used by many database 
management systems. It employs a cache mechanism to keep the most frequently accessed table blocks in 
memory:
- For index blocks, a special structure called the key cache (or key buffer) is maintained. The structure 
contains a number of block buffers where the most-used index blocks are placed.
- For data blocks, MySQL uses no special cache. Instead it relies on the native operating system file system 
cache.
- Multiple sessions can access the cache concurrently.
- You can set up multiple key caches and assign table indexes to specific caches.
To control the size of the key cache, use the key_buffer_size system variable. If this variable is set equal to 
zero, no key cache is used. The key cache also is not used if the key_buffer_size value is too small to allocate the 
minimal number of block buffers (8).
When the key cache is not operational, index files are accessed using only the native file system buffering 
provided by the operating system. (In other words, table index blocks are accessed using the same strategy as that 
employed for table data blocks.)
When data from any table index block must be accessed, the server first checks whether it is available in 
some block buffer of the key cache. If it is, the server accesses data in the key cache rather than on disk. Usually 
the server follows an LRU (Least Recently Used) strategy: When choosing a block for replacement, it selects the 
least recently used index block. To make this choice easier, the key cache module maintains all used blocks in a 
special list (LRU chain) ordered by time of use. When a block is accessed, it is the most recently used and is 
placed at the end of the list. When blocks need to be replaced, blocks at the beginning of the list are the least 
recently used and become the first candidates for eviction.
Shared Key Cache Access:
Threads can access key cache buffers simultaneously, subject to the following conditions:
- A buffer that is not being updated can be accessed by multiple sessions.
- A buffer that is being updated causes sessions that need to use it to wait until the update is complete.
- Multiple sessions can initiate requests that result in cache block replacements, as long as they do not 
interfere with each other (that is, as long as they need different index blocks, and thus cause different cache blocks 
to be replaced).
MySQL Database Administration
 87 
Shared access to the key cache enables the server to improve throughput significantly
Multiple Key Caches:
Shared access to the key cache improves performance but does not eliminate contention among sessions 
entirely. They still compete for control structures that manage access to the key cache buffers. To reduce key cache 
access contention further, MySQL also provides multiple key caches. This feature enables you to assign different 
table indexes to different key caches.
The separate key cache can be created by setting its size with a SET GLOBAL parameter setting statement or 
by using server startup options. For example:
mysql> SET GLOBAL keycache1.key_buffer_size=128*1024;
The following statement assigns indexes from the tables t1, t2, and t3 to the key cache named keycache1:
mysql> CACHE INDEX t1, t2, t3 IN keycache1;
The key cache referred to in a CACHE INDEX statement can be created by setting its size with a SET GLOBAL 
parameter setting statement or by using server startup options. For example:
mysql> SET GLOBAL keycache1.key_buffer_size=128*1024;
For a busy server, you can use a strategy that involves three key caches:
- A “hot” key cache that takes up 20% of the space allocated for all key caches. Use this for tables that are 
heavily used for searches but that are not updated.
- A “cold” key cache that takes up 20% of the space allocated for all key caches. Use this cache for mediumsized, intensively modified tables, such as temporary tables.
- A “warm” key cache that takes up 60% of the key cache space. Employ this as the default key cache, to be 
used by default for all other tables.
17.2. The InnoDB Buffer Pool
InnoDB maintains a buffer pool for caching data and indexes in memory. InnoDB manages the pool as a list, 
using a least recently used (LRU) algorithm incorporating a midpoint insertion strategy. When room is needed to 
add a new block to the pool, InnoDB evicts the least recently used block and adds the new block to the middle of 
the list. The midpoint insertion strategy in effect causes the list to be treated as two sublists:
− At the head, a sublist of “new” (or “young”) blocks that have been recently used.
− At the tail, a sublist of “old” blocks that are less recently used.
As a result of the algorithm, the new sublist contains blocks that are heavily used by queries. The old sublist 
contains less-used blocks, and candidates for eviction are taken from this sublist.
innodb_buffer_pool_size
Specifies the size of the buffer pool. If your buffer pool is small and you have sufficient memory, making the 
pool larger can improve performance by reducing the amount of disk I/O needed as queries access InnoDB tables.
innodb_old_blocks_pct
Specifies the approximate percentage of the buffer pool that InnoDB uses for the old block sublist. The range 
of values is 5 to 95. The default value is 37 (that is, 3/8 of the pool).
innodb_old_blocks_time
Specifies how long in milliseconds (ms) a block inserted into the old sublist must stay there after its first 
access before it can be moved to the new sublist. The default value is 0: A block inserted into the old sublist moves 
immediately to the new sublist the first time it is accessed, no matter how soon after insertion the access occurs. If 
the value is greater than 0, blocks remain in the old sublist until an access occurs at least that many ms after the 
first access. For example, a value of 1000 causes blocks to stay in the old sublist for 1 second after the first access 
before they become eligible to move to the new sublist.
MySQL Database Administration
 88 
innodb_old_blocks_pct and innodb_old_blocks_time are available as of MySQL 5.1.41, but only for InnoDB 
Plugin, not the built-in version of InnoDB.
18. Locking Issues
MySQL manages contention for table contents using locking:
− Internal locking is performed within the MySQL server itself to manage contention for table contents by 
multiple threads. This type of locking is internal because it is performed entirely by the server and 
involves no other programs.
− External locking occurs when the server and other programs lock MyISAM table files to coordinate 
among themselves which program can access the tables at which time.
18.1. Internal Locking Methods:
This section discusses internal locking; that is, locking performed within the MySQL server itself to manage 
contention for table contents by multiple sessions. This type of locking is internal because it is performed entirely by 
the server and involves no other programs. External locking occurs when the server and other programs lock 
MyISAM table files to coordinate among themselves which program can access the tables at which time. MySQL 
uses row-level locking for InnoDB tables, and table-level locking for MyISAM, MEMORY, and MERGE tables.
Which lock type works better for your application depends on the application and its workload, especially 
whether the data is modified frequently and how many concurrent sessions need to read or write the same tables. 
Different parts of an application may require different lock types.
Considerations for Table Locking:
Table locking in MySQL is deadlock-free for storage engines that use table-level locking. Deadlock avoidance 
is managed by always requesting all needed locks at once at the beginning of a query and always locking the 
tables in the same order.
MySQL grants table write locks as follows:
1. If there are no locks on the table, put a write lock on it.
2. Otherwise, put the lock request in the write lock queue.
MySQL grants table read locks as follows:
1. If there are no write locks on the table, put a read lock on it.
2. Otherwise, put the lock request in the read lock queue.
Table updates are given higher priority than table retrievals. Therefore, when a lock is released, the lock is 
made available to the requests in the write lock queue and then to the requests in the read lock queue. This 
ensures that updates to a table are not “starved” even if there is heavy SELECT activity for the table. However, if 
you have many updates for a table, SELECT statements wait until there are no more updates.
You can analyze the table lock contention on your system by checking the Table_locks_immediate and 
Table_locks_waited status variables, which indicate the number of times that requests for table locks could be 
granted immediately and the number that had to wait, respectively.
The MyISAM storage engine supports concurrent inserts to reduce contention between readers and writers for 
a given table: If a MyISAM table has no free blocks in the middle of the data file, rows are always inserted at the 
end of the data file. In this case, you can freely mix concurrent INSERT and SELECT statements for a MyISAM
table without locks. That is, you can insert rows into a MyISAM table at the same time other clients are reading from 
it. Holes can result from rows having been deleted from or updated in the middle of the table. If there are holes, 
concurrent inserts are disabled but are enabled again automatically when all holes have been filled with new data. 
This behavior is altered by the concurrent_insert system variable.
InnoDB uses row locks. Deadlocks are possible for InnoDB because it automatically acquires locks during the 
processing of SQL statements, not at the start of the transaction.
MySQL Database Administration
 89 
Considerations for Row Locking:
Advantages of row-level locking:
1. Fewer lock conflicts when different sessions access different rows.
2. Possible to lock a single row for a long time.
Disadvantages of row-level locking:
1. Requires more memory than table-level locks.
2. Slower than table-level locks when used on a large part of the table because you must acquire 
many more locks.
3. Slower if you often do GROUP BY operations on a large part of the data or if you must scan the 
entire table frequently.
Choosing the Type of Locking:
Generally, table locks are superior to row-level locks in the following cases:
1. Most statements for the table are reads.
2. Statements for the table are a mix of reads and writes, where writes are updates or deletes for a 
single row that can be fetched with one key read:
mysql> UPDATE tbl_name SET column=value WHERE unique_key_col=key_value;
mysql> DELETE FROM tbl_name WHERE unique_key_col=key_value;
3. SELECT combined with concurrent INSERT statements, and very few UPDATE or DELETE
statements
4. Many scans or GROUP BY operations on the entire table without any writers.
18.2. Table Locking Issues:
To achieve a very high lock speed, MySQL uses table locking for all storage engines except InnoDB and 
NDBCLUSTER. For InnoDB tables, MySQL uses table locking only if you explicitly lock the table with LOCK 
TABLES. For this storage engine, avoid using LOCK TABLES at all, because InnoDB uses automatic row-level 
locking to ensure transaction isolation.
For large tables, table locking is often better than row locking, but there are some disadvantages:
− Table locking enables many sessions to read from a table at the same time, but if a session wants to 
write to a table, it must first get exclusive access. During the update, all other sessions that want to 
access this particular table must wait until the update is done.
− A session issues a SELECT that takes a long time to run. Another session then issues an UPDATE on 
the same table. This session waits until the SELECT is finished.
The following items describe some ways to avoid or reduce contention caused by table locking:
− Try to get the SELECT statements to run faster so that they lock tables for a shorter time.
− To give a specific INSERT, UPDATE, or DELETE statement lower priority, use the LOW_PRIORITY
attribute.
− To give a specific SELECT statement higher priority, use the HIGH_PRIORITY attribute.
− Start mysqld with --low-priority-updates. For storage engines that use only table-level locking (such as 
MyISAM, MEMORY, and MERGE), this gives all statements that update (modify) a table lower priority 
than SELECT statements.
− Using SQL_BUFFER_RESULT with SELECT statements can help to make the duration of table locks 
shorter.
18.3. Concurrent Inserts:
The MyISAM storage engine supports concurrent inserts to reduce contention between readers and writers for 
a given table: If a MyISAM table has no holes in the data file (deleted rows in the middle), an INSERT statement 
can be executed to add rows to the end of the table at the same time that SELECT statements are reading rows 
MySQL Database Administration
 90 
from the table. If there are multiple INSERT statements, they are queued and performed in sequence, concurrently 
with the SELECT statements. The results of a concurrent INSERT may not be visible immediately.
The concurrent_insert system variable can be set to modify the concurrent-insert processing. By default, the 
variable is set to 1 and concurrent inserts are handled as just described. If concurrent_insert is set to 0, concurrent 
inserts are disabled. If the variable is set to 2, concurrent inserts at the end of the table are permitted even for 
tables that have deleted rows.
18.4. External Locking:
External locking is used in situations where a single process such as the MySQL server cannot be assumed to 
be the only process that requires access to tables. Here are some examples:
− If you run multiple servers that use the same database directory (not recommended), each server must 
have external locking enabled.
− If you use myisamchk to perform table maintenance operations on MyISAM tables, you must either 
ensure that the server is not running, or that the server has external locking enabled so that it locks 
table files as necessary to coordinate with myisamchk for access to the tables. The same is true for 
use of myisampack to pack MyISAM tables. If the server is run with external locking enabled, you can 
use myisamchk at any time for read operations such a checking tables. In this case, if the server tries 
to update a table that myisamchk is using, the server will wait for myisamchk to finish before it 
continues.
With external locking in effect, each process that requires access to a table acquires a file system lock for the 
table files before proceeding to access the table. If all necessary locks cannot be acquired, the process is blocked 
from accessing the table until the locks can be obtained. External locking affects server performance because the 
server must sometimes wait for other processes before it can access tables.
For mysqld, external locking is controlled by the value of the skip_external_locking system variable. When this 
variable is enabled, external locking is disabled, and vice versa. Use of external locking can be controlled at server 
startup by using the --external-locking or --skip-external-locking option.
19. High Availability and Scalability
19.1. Replication:
Replication enables data from one MySQL database server (the master) to be replicated to one or more 
MySQL database servers (the slaves). Replication is asynchronous - slaves need not be connected permanently to 
receive updates from the master. Depending on the configuration, you can replicate all databases, selected 
databases, or even selected tables within a database. 
The target uses for replication in MySQL include: 
Scale-out solutions - spreading the load among multiple slaves to improve performance. In this environment, all 
writes and updates must take place on the master server. Reads, however, may take place on one or more slaves. 
This model can improve the performance of writes (since the master is dedicated to updates), while dramatically 
increasing read speed across an increasing number of slaves. 
Data security - because data is replicated to the slave, and the slave can pause the replication process, it is 
possible to run backup services on the slave without corrupting the corresponding master data. 
Analytics - live data can be created on the master, while the analysis of the information can take place on the 
slave without affecting the performance of the master. 
Replication in MySQL features support for one-way, asynchronous replication, in which one server acts as the 
master, while one or more other servers act as slaves. This is in contrast to the synchronous replication which is a 
characteristic of MySQL Cluster.
Advantages:
1.It makes backing up the database easier and safer.
2.Gives more performance with load balancing. we can split the load between two servers by directing reads to 
the slave server and writes to the master server.
MySQL Database Administration
 91 
3.We can replicate from one storage engine to another storage engine.
4.We can use this slave server for data analysis, reports etc....instead on impacting the production server we 
can do this in slave server and even we can shutdown the slave server. 
Disadvantages:
1.The main disadvantage of replication is there is no guaranty of data synchronization between two servers.
2.No automatic fail over technique in case if master fails. This causes a little down time.
3.User defined variables and temporary tables may not work.
4.If replication is set with multiple slaves it may cause some load on master server to updated the statement to 
all the slaves.
Replication Formats:
 Replication is of three formats:
 1. STATEMENT BASED
 2. ROW BASED
 3. MIXED-FORMAT (Combination of statement based and row based)
Statement Based: All statements propagates from master to slave and executes the statements on slave.
Advantages of Statement-Based Replication: 
 1. Less data written to log files. This results less storage space for log files.
 2. Log files contains all the changes made to the database. so they can be used to track the database changes. 
Disadvantages of Statement-Based Replication:
 1. Queries using function like NOW(), RAND(), CURDATE(), UUID() etc are unsafe.
 2. DELETE and UPDATE queries using a LIMIT clause and without using ORDER BY clause are unsafe.
 3. Queries requires more number of locks on tables.
Row Based: Row-based binary logging logs changes in individual table rows.
Advantages of Row-Based Replication:
 
 1. All queries can be replicated safely.
 2. Queries requires less number of locks on tables.
Disadvantages of Row-Based Replication:
 1. Large data written to log files. This results large storage space for log files.
 This would take a little longer time when statements like BLOB and TEXT values are encountered.
 2. We cannot track the logs to find the changes committed to the database. 
Mixed Based: When the mixed format is in effect, statement-based logging is used by default, but automatically 
switches to row-based logging in particular cases
 Note: MIXED-FORMAT replication was introduced from MySQL Version 5.1.8.
19.1.1 Replication Configuration:
Replication between servers in MySQL is based on the binary logging mechanism. The MySQL instance 
operating as the master writes updates and changes as “events” to the binary log. The information in the binary log 
is stored in different logging formats according to the database changes being recorded. Slaves are configured to 
read the binary log from the master and to execute the events in the binary log on the slave's local database. 
Once binary logging has been enabled, all statements are recorded in the binary log. Each slave receives a 
copy of the entire contents of the binary log. It is the responsibility of the slave to decide which statements in the 
binary log should be executed; you cannot configure the master to log only certain events. If you do not specify 
otherwise, all events in the master binary log are executed on the slave. If required, you can configure the slave to 
MySQL Database Administration
 92 
process only events that apply to particular databases or tables. 
Each slave keeps a record of the binary log coordinates: The file name and position within the file that it has 
read and processed from the master. This means that multiple slaves can be connected to the master and 
executing different parts of the same binary log. Because the slaves control this process, individual slaves can be 
connected and disconnected from the server without affecting the master's operation. Also, because each slave 
remembers the position within the binary log, it is possible for slaves to be disconnected, reconnect and then “catch 
up” by continuing from the recorded position.
Both the master and each slave must be configured with a unique ID. In addition, each slave must be 
configured with information about the master host name, log file name, and position within that file. These details 
can be controlled from within a MySQL session using the CHANGE MASTER TO statement on the slave. The 
details are stored within the slave's master.info file. 
How to Set Up Replication:
This section describes how to set up complete replication of a MySQL server. There are a number of different 
methods for setting up replication, and the exact method to use depends on how you are setting up replication, and 
whether you already have data within your master database.
There are some generic tasks that are common to all replication setups: 
− On the master, you must enable binary logging and configure a unique server ID. This might require a 
server restart.
− On each slave that you want to connect to the master, you must configure a unique server ID. This 
might require a server restart
− You may want to create a separate user that will be used by your slaves to authenticate with the 
master to read the binary log for replication. The step is optional.
− Before creating a data snapshot or starting the replication process, you should record the position of 
the binary log on the master. You will need this information when configuring the slave so that the slave 
knows where within the binary log to start executing events.
− If you already have data on your master and you want to use it to synchronize your slave, you will need 
to create a data snapshot. You can create a snapshot using mysqldump or by copying the data files 
directly.
Once you have configured the basic options, you will need to follow the instructions for your replication 
setup. A number of alternatives are provided: 
− If you are establishing a new MySQL master and one or more slaves, you need only set up the 
configuration, as you have no data to exchange.
− If you are already running a MySQL server, and therefore already have data that must be transferred to 
your slaves before replication starts.
− If you are adding slaves to an existing replication environment, you can set up the slaves without 
affecting the master.
Setting Up Replication with New Master and Slaves:
 
 SQL 
 Thread
IO Thread
Master Slave 
DB
 Binary 
Logs 
Relay
Logs
DB
MySQL Database Administration
 93 
The easiest and most straight forward method for setting up replication is to use new master and slave 
servers. You can also use this method if you are setting up new servers but have an existing dump of the 
databases from a different server that you want to load into your replication configuration. By loading the data into a 
new master, the data will be automatically replicated to the slaves. 
Setting the Replication Master Configuration:
On a master, you must enable binary logging and establish a unique server ID. If this has not already been 
done, this part of master setup requires a server restart. 
Each server within a replication group must be configured with a unique server ID. This ID is used to identify 
individual servers within the group, and must be a positive integer between 1 and (232)–1. How you organize and 
select the numbers is entirely up to you
Step 1:
To configure the binary log and server ID options, you will need to shut down your MySQL server and edit the 
my.cnf or my.ini file. Add the following options to the configuration file within the [mysqld] section.
[mysqld]
log-bin=mysql-bin
server-id=1
# skip-networking
After making the changes, restart the server. 
Ensure that the skip-networking option is not enabled on your master. If networking has been disabled, your slave 
will not able to communicate with the master and replication will fail. 
Step 2:
Each slave must connect to the master using a MySQL user name and password, so there must be a user 
account on the master that the slave can use to connect. Any account can be used for this operation, providing it 
has been granted the REPLICATION SLAVE privilege. You may wish to create a different account for each slave, 
or connect to the master using the same account for each slave.
You need not create an account specifically for replication. However, you should be aware that the user name 
and password will be stored in plain text within the master.info file. Therefore, you may want to create a separate 
account that has privileges only for the replication process, to minimize the possibility of compromise to other 
accounts. 
mysql> GRANT REPLICATION SLAVE ON *.* TO 'repl'@'slave_hostname' IDENTIFIED BY ‘password’;
Step 3:
To configure replication on the slave you must determine the master's current coordinates within its binary log. 
You will need this information so that when the slave starts the replication process, it is able to start processing 
events from the binary log at the correct point. 
To obtain the master binary log coordinates, follow these steps: 
1. Start a session on the master by connecting to it with the command-line client, and flush all tables and block 
write statements by executing the FLUSH TABLES WITH READ LOCK statement: 
mysql> FLUSH TABLES WITH READ LOCK;
For InnoDB tables, note that FLUSH TABLES WITH READ LOCK also blocks COMMIT operations. 
2. In a different session on the master, use the SHOW MASTER STATUS statement to determine the current binary 
log file name and position: 
mysql > SHOW MASTER STATUS;
+------------------------+-----------+--------------------+--------------------------+
| File | Position | Binlog_Do_DB | Binlog_Ignore_DB |
+------------------------+-----------+--------------------+--------------------------+
| mysql-bin.000003 | 73 | | |
+------------------------+-----------+--------------------+--------------------------+
The File column shows the name of the log file and Position shows the position within the file. You need them 
MySQL Database Administration
 94 
later when you are setting up the slave. They represent the replication coordinates at which the slave should begin 
processing new updates from the master. 
In the first session release the read lock: 
mysql> UNLOCK TABLES;
If the master has been running previously without binary logging enabled, the log file name and position 
values displayed by SHOW MASTER STATUS will be empty. 
You now have the information you need to enable the slave to start reading from the binary log in the correct 
place to start replication. 
Setting the Replication Slave Configuration:
Step 4:
On a replication slave, you must establish a unique server ID. If this has not already been done, this part of 
slave setup requires a server restart. 
[mysqld]
server-id=2
After making the changes, restart the server. 
If you are setting up multiple slaves, each one must have a unique server-id value that differs from that of the 
master and from each of the other slaves.
You do not have to enable binary logging on the slave for replication to be enabled. However, if you enable 
binary logging on the slave, you can use the binary log for data backups and crash recovery on the slave, and also 
use the slave as part of a more complex replication topology (for example, where the slave acts as a master to 
other slaves). 
Step 5:
To set up the slave to communicate with the master for replication, you must tell the slave the necessary 
connection information. To do this, execute the following statement on the slave, replacing the option values with 
the actual values relevant to your system: 
mysql> CHANGE MASTER TO
 MASTER_HOST='master_host_name',
 MASTER_USER='replication_user_name',
 MASTER_PASSWORD='replication_password',
 MASTER_PORT = ‘master_port’,
 MASTER_LOG_FILE='recorded_log_file_name',
 MASTER_LOG_POS=recorded_log_position;
The MASTER_LOG_FILE and MASTER_LOG_POS values should be used here which are obtained from Step 3.
The CHANGE MASTER TO statement has other options as well.
Step 6:
After that issue a command to start slave.
mysql> START SLAVE;
The above statement starts both sql thread and IO thread.
When a START SLAVE statement is issued on a slave server, the slave creates an I/O thread, which connects 
to the master and asks it to send the updates recorded in its binary logs. 
The slave creates an SQL thread to read the relay log that is written by the slave I/O thread and execute the 
events contained therein. 
To start or stop just SQL Thread use 
MySQL Database Administration
 95 
mysql> START/STOP SLAVE SQL_THREAD;
To start or stop just SQL Thread use 
mysql> START/STOP SLAVE IO_THREAD;
Step 7:
To see replication status use below command:
mysql> SHOW SLAVE STATUS\G
Setting Up Replication with Existing Master and New Slave:
When setting up replication with existing data, you will need to decide how best to get the data from the 
master to the slave before starting the replication service.
1.If server_id and binary logging are not enabled on the master you need to enable it and restart the server 
(see step 1).
2.If the MySQL master is running, create a user to be used by the slave when connecting to the master during 
replication (see step 2).
Creating a Data Snapshot Using mysqldump:
3.Start a session on the server by connecting to it with the command-line client, and flush all tables and block 
write statements by executing the FLUSH TABLES WITH READ LOCK statement: 
mysql> FLUSH TABLES WITH READ LOCK;
In another session, use mysqldump to create a dump either of all the databases you want to replicate, or of 
selected individual databases. For example: 
[shell]# mysqldump --all-databases --lock-all-tables > dbdump.sql
Transfer the dump file to slave server.
[shell]# scp dbdump.sql slaveip:/<path>
password:
4.Obtain master status by using SHOW MASTER STATUS (see Step 3).
5.Update the configuration of the slave (see Step 4).
6.Import the dump file in slave: 
[shell]# mysql < dbdump.sql
7.Configure the slave with the replication coordinates from the master (see Step 5).
8.Start the slave threads (see Step 6).
 
 SQL
 Thread
IO Thread
Master Slave 
DB
 Binary 
Logs
Relay
Logs
DB DB
MySQL Database Administration
 96 
Adding a Slave to an existing Slave:
1.If server_id and binary logging are not enabled on the Slave 1 you need to enable it and also you need to 
enable log-slave-updates parameter which writes the events from relaylog to binlog and restart the server. 
(see step 1).
2.Create a user in Slave 1 giving privileges to Slave 2 to connect with REPLICATION SLAVE privilege. (see 
step 2).
3.On Slave 1 Creating a Data Snapshot Using mysqldump (Refer above)
9.Obtain master status in Slave 1 by using SHOW MASTER STATUS (see Step 3).
10. Update the configuration of the Slave 2 (see Step 4).
11. Import the dump file in Slave 2: 
[shell]# mysql < dbdump.sql
7.Configure the Slave 2 with the replication coordinates from the Slave 1 (see Step 5).
12. Start the slave threads (see Step 6).
Replication Scenarios:
Bi-directional Replication:
In bi-directional replication clients can retrieve and update the data in both the servers. One problem in a 
multimaster replication is the conflict that can happen with self-generated keys. The AUTO_INCREMENT feature is 
 
SQL Thread 
 
 
 
 
Log Slave Updates
Master Slave 1
Slave 1 
DB
 Binary 
Logs
Relay
Logs
 Slave 2
DB DB
 Binary 
Logs
Relay
Logs
 DB
 SQL Threads 
 
IO Threads
Master 1 Master 2
DB DB
 Binary 
Logs
Binary 
Logs
 
Relay
Logs
Relay
Logs
MySQL Database Administration
 97 
quite convenient, but in a replication environment it will be disruptive. If node A and node B both insert an autoincrementing key on the same table, conflicts arise immediately and replication stops.
To over come this issue we need to set below 2 parameters in both servers.
Master 1: 
auto_increment_offset = 1;
auto_increment_increment = 2;
Master 2: 
auto_increment_offset = 2;
auto_increment_increment = 2;
In the first master the auto increment value starts from 1 and increments by 2, so it continues in odd number 
series. In the second master the auto increment value starts from 2 and increments by 2, so it continues in even 
number series. As the two servers generate different auto increment values you can over come this issue.
Circular Replication:
In circular replication clients can retrieve and update the data in all the servers. You need to set 
auto_increment_offset ans auto_increment_increment variables as below.
Master 1: 
auto_increment_offset = 1;
auto_increment_increment = 3;
Master 2: 
auto_increment_offset = 2;
auto_increment_increment = 3;
Master 3: 
 
Master 1
Master 3 Master 2
 
 Binary 
 Logs 
Binary 
 Logs
 Binary 
 Logs
DB DB
DB
Relay
Logs
Relay
Logs
Relay
Logs
MySQL Database Administration
 98 
auto_increment_offset = 3;
auto_increment_increment = 3;
Replication Options and Variables:
server-id=<value>
Need to use unique server id to setup a replication configuration.
--master-info-file=file_name
The name to use for the file in which the slave records information about the master. The default name is 
master.info in the data directory.
--log-slave-updates
Normally, a slave does not log to its own binary log any updates that are received from a master server. This 
option tells the slave to log the updates performed by its SQL thread to its own binary log. For this option to have 
any effect, the slave must also be started with the --log-bin option to enable binary logging. --log-slave-updates is 
used when you want to chain replication servers. For example, you might want to set up replication servers using 
this arrangement: 
A -> B -> C
--master-connect-retry=seconds
The number of seconds that the slave thread sleeps before trying to reconnect to the master in case the 
master goes down or the connection is lost.If not set, the default is 60.The number of reconnection attempts is 
limited by the --master-retry-count option.
--master-retry-count=count
The number of times that the slave tries to connect to the master before giving up. Reconnects are attempted 
at intervals set by the --master-connect-retry option. The default value is 86400. A value of 0 means “infinite”; the 
slave attempts to connect forever.
--max-relay-log-size=size
The size at which the server rotates relay log files automatically.
--read-only
Cause the slave to permit no updates except from slave threads or from users having the SUPER privilege. 
On a slave server, this can be useful to ensure that the slave accepts updates only from its master server and not 
from clients.
--relay-log=file_name
The basename for the relay log. The default basename is host_name-relay-bin. The server writes the file in 
the data directory unless the basename is given with a leading absolute path name to specify a different directory. 
--relay-log-index=file_name
The name to use for the relay log index file. The default name is host_name-relay-bin.index in the data 
directory
-relay-log-info-file=file_name
The name to use for the file in which the slave records information about the relay logs. The default name is 
relay-log.info in the data directory.
--relay-log-purge={0|1}
Disable or enable automatic purging of relay logs as soon as they are no longer needed. The default value is 
1 (enabled). This is a global variable that can be changed dynamically.
--replicate-do-db=db_name
The effects of this option depend on whether statement-based or row-based replication is in use. 
SBR: Tell the slave SQL thread to restrict replication to statements where the default database (that is, the one 
selected by USE) is db_nam. To specify more than one database, use this option multiple times, once for each 
database; however, doing so does not replicate cross-database statements such as UPDATE some_db.some_table 
SET foo='bar' while a different database (or no database) is selected.
RBR: Tells the slave SQL thread to restrict replication to database db_name. Only tables belonging to db_name are 
changed; the current database has no effect on this. However, issuing cross update statements on the master has 
no effect on the slave when using row-based replication and –replicate-do-db.
MySQL Database Administration
 99 
--replicate-ignore-db=db_name
As with --replicate-do-db, the effects of this option depend on whether statement-based or row-based 
replication is in use. 
SBR: Tells the slave SQL thread not to replicate any statement where the default database (that is, the one 
selected by USE) is db_name.
RBR: Tells the slave SQL thread not to update any tables in the database db_name. The default database has no 
effect. When using statement-based replication, the following example does not work as you might expect. 
Suppose that the slave is started with --replicate-ignore-db=sales and you issue the following statements on the 
master: 
USE prices;
UPDATE sales.january SET amount=amount+1000;
The UPDATE statement is replicated in such a case because --replicate-ignore-db applies only to the default 
database (determined by the USE statement). Because the sales database was specified explicitly in the 
statement, the statement has not been filtered. However, when using row-based replication, the UPDATE 
statement's effects are not propagated to the slave, and the slave's copy of the sales.january table is unchanged.
--replicate-do-table=db_name.tbl_name
Tells the slave SQL thread to restrict replication to the specified table. To specify more than one table, use this 
option multiple times, once for each table. This works for both cross-database updates and default database 
updates. 
--replicate-ignore-table=db_name.tbl_name
Tells the slave SQL thread not to replicate any statement that updates the specified table, even if any other 
tables might be updated by the same statement. To specify more than one table to ignore, use this option multiple 
times, once for each table. This works for cross-database updates.
--replicate-rewrite-db=from_name->to_name
Tells the slave to translate the default database (that is, the one selected by USE) to to_name if it was 
from_name on the master. Only statements involving tables are affected and only if from_name is the default 
database on the master. This does not work for cross-database updates. To specify multiple rewrites, use this 
option multiple times.
--replicate-wild-do-table=db_name.tbl_name
Tells the slave thread to restrict replication to statements where any of the updated tables match the specified 
database and table name patterns. To specify more than one table, use this option multiple times, once for each 
table. This works for cross-database updates.
Example: --replicate-wild-do-table=foo%.bar% replicates only updates that use a table where the database name 
starts with foo and the table name starts with bar. 
--replicate-wild-ignore-table=db_name.tbl_name
Tells the slave thread not to replicate a statement where any table matches the given wildcard pattern. To 
specify more than one table to ignore, use this option multiple times, once for each table.
--slave-skip-errors=[err_code1,err_code2,...|all]
Normally, replication stops when an error occurs on the slave. This gives you the opportunity to resolve the 
inconsistency in the data manually. This option tells the slave SQL thread to continue replication when a statement 
returns any of the errors listed in the option value. 
Examples: 
--slave-skip-errors=1062,1053
--slave-skip-errors=all
19.2. Replication Solutions
Using Replication for Backups:
Replication server can be used for consistent backups. These backups can be used to configure another slave 
MySQL Database Administration
 100 
to this server or else to dump the database into other server.
IF you are taking backups using mysqldump utility, you need to stop sql thread (or you can stop both threads) 
so that the mysql server stops udpating the datafiles.
[shell]# mysqladmin stop-slave (OR)
[shell]# mysql -e 'STOP SLAVE SQL_THREAD;'
[shell]# mysqldump --all-databases > fulldb.dump
[shell]# mysqladmin start-slave
Replication servers can also be used to take physical backups (raw backups). To take physical backups 
MySQL Server should be safely shutdowned. You can shutdown the slave MySQL Server and after taking backups 
you can start the server and replication as well from the same position where it stopped.
[shell]# /etc/init.d/mysql stop
[shell]# tar -cvzf dbbackup.tar.gz /var/lib/mysql
[shell]# /etc/init.d/mysql start
Normally you should back up the entire data directory for the slave MySQL server. If you want to be able to 
restore the data and operate as a slave (for example, in the event of failure of the slave), then in addition to the 
slave's data, you should also back up the slave status files, master.info and relay-log.info, along with the relay log 
files. These files are needed to resume replication after you restore the slave's data. 
If you lose the relay logs but still have the relay-log.info file, you can check it to determine how far the SQL 
thread has executed in the master binary logs. Then you can use CHANGE MASTER TO with the 
MASTER_LOG_FILE and MASTER_LOG_POS options to tell the slave to re-read the binary logs from that point. 
This requires that the binary logs still exist on the master server. 
Using Replication with Different Master and Slave Storage Engines:
It does not matter for the replication process whether the source table on the master and the replicated table 
on the slave use different engine types.
This provides a number of benefits in the replication process in that you can take advantage of different 
engine types for different replication scenarios. For example, in a typical scale-out scenario, you want to use 
InnoDB tables on the master to take advantage of the transactional functionality, but use MyISAM on the slaves 
where transaction support is not required because the data is only read. When using replication in a data-logging 
environment you may want to use the Archive storage engine on the slave. 
− If you used mysqldump to create the database snapshot on your master, you could edit the dump file 
text to change the engine type used on each table.
− Another alternative for mysqldump is to disable engine types that you do not want to use on the slave 
before using the dump to build the data on the slave. For example, you can add the --skip-innodb 
option on your slave to disable the InnoDB engine. If a specific engine does not exist for a table to be 
created, MySQL will use the default engine type, usually MyISAM. (This requires that the 
NO_ENGINE_SUBSTITUTION SQL mode is not enabled.) If you want to disable additional engines in 
this way, you may want to consider building a special binary to be used on the slave that only supports 
the engines you want. 
− If you are using raw data files (a binary backup) to set up the slave, you will be unable to change the 
initial table format. Instead, use ALTER TABLE to change the table types after the slave has been 
started. 
− If you are already running a replication solution and want to convert your existing tables to another 
engine type, follow these steps: 
mysql> STOP SLAVE;
mysql> ALTER TABLE <table_name> ENGINE='engine_type'
mysql> START SLAVE;
Improving Replication Performance:
As the number of slaves connecting to a master increases, the load, although minimal, also increases, as 
each slave uses a client connection to the master. Also, as each slave must receive a full copy of the master binary 
log, the network load on the master may also increase and create a bottleneck. If you are using a large number of 
MySQL Database Administration
 101 
slaves connected to one master, and that master is also busy processing requests, then you may want to improve 
the performance of the replication process. 
One way to improve the performance of the replication process is to create a deeper replication structure that 
enables the master to replicate to only one slave, and for the remaining slaves to connect to this primary slave for 
their individual replication requirements.
For this to work, you must configure the MySQL instances as follows: 
− Master 1 is the primary master where all changes and updates are written to the database. Binary 
logging should be enabled on this machine.
− Master 2 is the slave to the Master 1 that provides the replication functionality to the remainder of the 
slaves in the replication structure. Master 2 is the only machine permitted to connect to Master 1. 
Master 2 also has binary logging enabled, and the --log-slave-updates option so that replication 
instructions from Master 1 are also written to Master 2's binary log so that they can then be replicated 
to the true slaves. 
− Slave 1, Slave 2, and Slave 3 act as slaves to Master 2, and replicate the information from Master 2, 
which actually consists of the upgrades logged on Master 1. 
The above solution reduces the client load and the network interface load on the primary master, which should 
improve the overall performance of the primary master when used as a direct database solution. 
If your slaves are having trouble keeping up with the replication process on the master, there are a number of 
options available: 
− If possible, put the relay logs and the data files on different physical drives. To do this, use the --relaylog option to specify the location of the relay log.
− If the slaves are significantly slower than the master, you may want to divide up the responsibility for 
replicating different databases to different slaves. 
− If your master makes use of transactions and you are not concerned about transaction support on your 
slaves, use MyISAM or another nontransactional engine on the slaves.
Switching Masters during Failover:
There is currently no official solution for providing failover between master and slaves in the event of a failure. 
With the currently available features, you would have to set up a master and a slave (or several slaves), and to 
write a script that monitors the master to check whether it is up. Then instruct your applications and the slaves to 
change master in case of failure.
Remember that you can tell a slave to change its master at any time, using the CHANGE MASTER TO 
statement. The slave will not check whether the databases on the master are compatible with the slave, it will just 
start reading and executing events from the specified binary log coordinates on the new master. In a failover 
situation, all the servers in the group are typically executing the same events from the same binary log file, so 
changing the source of the events should not affect the database structure or integrity
Run your slaves with the --log-bin option and without --log-slave-updates. In this way, the slave is ready to 
become a master as soon as you issue STOP SLAVE; RESET MASTER, and CHANGE MASTER TO statement on 
the other slaves.
Troubleshooting Replication:
If you encounter any issues with replication setup the first thing to do is check the error log for messages. If 
you cannot tell from the error log what the problem was, try the following techniques:
Master 1 Master 2 
Slave 1
Slave 2
Slave 3
MySQL Database Administration
 102 
− Verify that the master has binary logging enabled by issuing a SHOW MASTER STATUS statement. If 
logging is enabled, Position is nonzero. If binary logging is not enabled, verify that you are running the 
master with the --log-bin option.
− Verify that the master and slave both were started with the --server-id option and that the ID value is 
unique on each server. 
− Verify that the slave is running. Use SHOW SLAVE STATUS to check whether the Slave_IO_Running 
and Slave_SQL_Running values are both Yes. If not, verify the options that were used when starting 
the slave server. For example, --skip-slave-start prevents the slave threads from starting until you issue 
a START SLAVE statement. 
− If the slave is running, check whether it established a connection to the master. Use SHOW 
PROCESSLIST, find the I/O and SQL threads and check their State column to see what they display. If 
the I/O thread state says Connecting to master, Verify the privileges for the user being used for 
replication on the master. 
− If a statement that succeeded on the master refuses to run on the slave, try the following procedure if it 
is not feasible to do a full database resynchronization by deleting the slave's databases and copying a 
new snapshot from the master: 
1. Determine whether the affected table on the slave is different from the master table. Try to understand how this 
happened. Then make the slave's table identical to the master's and run START SLAVE. 
2. If the preceding step does not work or does not apply, try to understand whether it would be safe to make the 
update manually (if needed) and then ignore the next statement from the master.
3. If you decide that the slave can skip the next statement from the master, issue the following statements:
mysql> SET GLOBAL sql_slave_skip_counter = N;
mysql> START SLAVE;
Replication Issues:
 1. Do not use RESET MASTER command om master server while replication is running.
As the replication is based on binary logs, RESET MASTER command would flush all binary logs and start 
from the first binary log. For example if the current binary log is "binlog.000024", it will flush it and start from the first 
binary log as "binlog.000001". And the Slave_SQL_Thread would searching for "binlog.000024" file and the 
replication would fail.
 2. Another major issue with the replication is network. If the network fails between the two servers the slave 
tries to connect to the master based on the below variables and it gives up.
master-retry-count 
This variables defines the number of times the slave tries to connect to the master before giving up. The 
reconnect interval is set by master-connect-retry variable.
Master-connect-retry
This variables defines the number of seconds the slave thread sleep before trying to connect to the 
master. The default value of this variable is 60 seconds.
 3. If the disk space where the binary logs are stored is full we may get the below error:
[ERROR] /usr/sbin/mysqld: Disk is full writing '/var/bin/mysql/mysql-bin.000034' (Errcode: 28). Waiting for 
someone to free space... Retry in 60 secs .
In the above, error code 28 defines disk full error. In this case you can use 
PURGE BINARY LOGS command. This command flushes all the binary logs but keeps the present binary log file 
with the same name. So that the replication may not fail.
 4. Usually we will be getting 1045 error (access denied for user 'root'@'ipaddress') while we setting up 
replication or changing master user and host using CHANGE MASTER command.
We will get this error if the user doesn't have REPLICATION SLAVE privilege on the specified host. Assigning 
the required privilege may solve the issue.
MySQL Database Administration
 103 
 5. Also we may get errors like 1062(duplicate entry), 1146 (table doesn't exists).
If there is a unique key on a table and a row exists in slave sever and doesn't exists in master server then we 
may get 1062 error.
If any DML command if the table doesn't exists on the slave server we may get 1146 error.
Creating the table on the slave server solves the issue. 
To over come the errors of these types and if you know the error numbers we can give the error numbers in 
the variable as 
slave-skip-errors = 1062, 1146
We can also overcome all the error by giving the value 'ALL' for the above variable. But not recommended. 
20. Upgrading MySQL
As a general rule, to upgrade from one release series to another, you should go to the next series rather than 
skipping a series. To upgrade from a release series previous to MySQL 5.0, upgrade to each successive release 
series in turn until you have reached MySQL 5.0, and then proceed with the upgrade to MySQL 5.1. For example, if 
you currently are running MySQL 4.1 and wish to upgrade to a newer series, upgrade to MySQL 5.0 first before 
upgrading to 5.1, and so forth.
If you perform a binary upgrade without dumping and reloading tables, you cannot upgrade directly from 
MySQL 4.1 to 5.1. This occurs due to an incompatible change in the MyISAM table index format in MySQL 5.0. 
Upgrade from MySQL 4.1 to 5.0 and repair all MyISAM tables. Then upgrade from MySQL 5.0 to 5.1 and check and 
repair your tables.
To upgrade from MySQL 5.0 to 5.1, use the items in the following checklist as a guide:
− Before any upgrade, back up your databases, including the mysql database that contains the grant 
tables.
− Read all the notes of upgrading document. These notes enable you to identify upgrade issues that 
apply to your current MySQL installation. Some incompatibilities discussed in that section require your 
attention before upgrading. Others should be dealt with after upgrading.
− Read change history as well, which provides information about features that are new in MySQL 5.1 or 
differ from those found in MySQL 5.0.
− After upgrading to a new version of MySQL, run mysql_upgrade. This program checks your tables, and 
attempts to repair them if necessary. It also updates your grant tables to make sure that they have the 
current structure so that you can take advantage of any new capabilities.
− If you upgrade an installation originally produced by installing multiple RPM packages, it is best to 
upgrade all the packages, not just some. For example, if you previously installed the server and client 
RPMs, do not upgrade just the server RPM.
− If you have created a user-defined function (UDF) with a given name and upgrade MySQL to a version 
that implements a new built-in function with the same name, the UDF becomes inaccessible. To correct 
this, use DROP FUNCTION to drop the UDF, and then use CREATE FUNCTION to re-create the UDF 
with a different nonconflicting name. The same is true if the new version of MySQL implements a builtin function with the same name as an existing stored function.
If you are cautious about using new versions, you can always rename your old mysqld before installing a 
newer one. For example, if you are using MySQL 5.0.13 and want to upgrade to 5.1.10, rename your current server 
from mysqld to mysqld-5.0.13. If your new mysqld then does something unexpected, you can simply shut it down 
and restart with your old mysqld.
If problems occur, such as that the new mysqld server does not start or that you cannot connect without a 
password, verify that you do not have an old my.cnf file from your previous installation. You can check this with the -
-print-defaults option (for example, mysqld --print-defaults). If this command displays anything other than the 
program name, you have an active my.cnf file that affects server or client operation.
If your MySQL installation contains a large amount of data that might take a long time to convert after an inplace upgrade, you might find it useful to create a “dummy” database instance for assessing what conversions 
might be needed and the work involved to perform them. Make a copy of your MySQL instance that contains a full 
copy of the mysql database, plus all other databases without data. Run your upgrade procedure on this dummy 
MySQL Database Administration
 104 
instance to see what actions might be needed so that you can better evaluate the work involved when performing 
actual data conversion on your original database instance.
It is a good idea to rebuild and reinstall the Perl DBD::mysql module whenever you install a new release of 
MySQL. The same applies to other MySQL interfaces as well, such as PHP mysql extensions and the Python 
MySQLdb module.
Known Issues:
1.mysql_upgrade attempts to to upgrade tables that are incompatible with the current version of MySQL. (It 
invokes mysqlcheck to check tables and, if necessary, repair them.) However this can fail for storage 
engines that do not support REPAIR TABLE, such as InnoDB, and leave tables in a nonupgradable state. 
To work around this problem, use ALTER TABLE tbl_name ENGINE=InnoDB to perform a “null” alter 
operation that rebuilds the table.
2.After a binary upgrade to MySQL 5.1 from a MySQL 5.0 installation that contains ARCHIVE tables: 
Before MySQL 5.1.42, accessing those tables will cause the server to crash, even if you have run 
mysql_upgrade or CHECK TABLE ... FOR UPGRADE. 
As of MySQL 5.1.42, the server will not open 5.0 ARCHIVE tables at all. 
In either case, the solution is to use mysqldump to dump all 5.0 ARCHIVE tables before upgrading, and 
reload them into MySQL 5.1 after upgrading. 
3.Dumps performed by using mysqldump to generate a dump file before the upgrade and reloading the file 
after upgrading are subject to the following problem: 
Before MySQL 5.0.40, mysqldump displays SPATIAL index definitions using prefix lengths for the indexed 
columns. These prefix lengths are accepted in MySQL 5.0, but not as of MySQL 5.1. If you use mysqldump from 
versions of MySQL older than 5.0.40, any table containing SPATIAL indexes will cause an error when the dump file 
is reloaded into MySQL 5.1 or higher. 
For example, a table definition might look like this when dumped in MySQL 5.0: 
CREATE TABLE `t` (
`g` geometry NOT NULL,
SPATIAL KEY `g` (`g`(32))
) ENGINE=MyISAM DEFAULT CHARSET=latin1
The SPATIAL index definition will not be accepted in MySQL 5.1. To work around this, edit the dump file to 
remove the prefix: 
CREATE TABLE `t` (
`g` geometry NOT NULL,
SPATIAL KEY `g` (`g`)
) ENGINE=MyISAM DEFAULT CHARSET=latin1
RPM’s Upgrade Process:
1.Download th RPM packages.
2.Take complete backup of all the databases including mysql database. This helps you in priventing loss of 
data in case if anything goes wrong.
3.Enter into the newly downloaded MySQL directory and use below command to upgrade the MySQL RPM 
packages.
[shell]# rpm -Uvh file.rpm
4.And after upgrading to a new version of MySQL you must run mysql_upgrade program. This program 
checks all the tables and attempts to repair them if necessary. It also updates the grant tables so that you 
can take advantage of new privileges or capabilities that might have been added. .
[shell]# mysql_upgrade
5.After upgrading the software its recommended to rebuild the tables for compatibility with the new version. But 
rebuild may not possible in OLTP databases. In this case at least we need to repair the table.
i) You can rebuild the tables using mysqldump utility.
ii) You can also use the below statement to rebuild the table with the same engine name.
MySQL Database Administration
 105 
mysql > ALTER TABLE tablename ENIGNE = <ENGINE TYPE>; 
Binary Upgrade Process:
However, always check the upgrade notes in the manual for incompatible changes, such as a binary 
incompatibility that might require some data to be dumped to text first before reloading. Before attempting any 
upgrade, please back up your databases, including the mysql database that contains the grant tables.
To begin with, this process will be much easier and less confusing for the future, if your data directory is 
located outside of the MySQL installation directory. By default, MySQL uses /usr/local/mysql/data for the data 
directory. To simplify upgrading, change the data dir to out side of installation dir by adding the following to the 
[mysqld] section of your my.cnf file:
[mysqld]
datadir = /usr/local/mysql-data
After changing this, shut down the server, move the existing data files to the new directory, and then start up 
mysqld again. Next, ensure that everything works with the data in the new data directory. Do all of this before 
attempting to upgrade. This way you are only changing one thing at a time, and thus should make this process 
easier.
Now that the data directory is independent of the installation directory, you can easily switch between different 
versions of MySQL. And you can simply shut down the old server and start up the new one once it is installed. As 
for installing the new version, you just need to download the file you are installing, copy it to the directory of your 
choice, extract the files, and create a symbolic link. For example, if you were going to install this to /usr/local:
# cd /usr/local
# tar zvxf /tmp/mysql-VERSION.tar.gz
# ln -s full-path-to-mysql-VERSION-OS mysql
If a symbolic link already exists for your previous version of MySQL, then you can delete the existing symbolic 
link first and then re-create it, or you can simply use the –f option to perform this automatically with the ln 
command.
# ln -sf full-path-to-mysql-VERSION-OS mysql
This is when you should also change the ownership of program binaries to root and the group attribute to the 
mysql group. Assuming you are still in (/usr/local), run the following commands:
cd mysql
chown -R root .
chgrp -R mysql .
The chown command changes the owner attribute of the files to the root user. The chgrp changes the group 
attribute to the mysql group. Since this is for an upgrade and we have recommended you move your data directory, 
this assumes that you have already changed those files appropriately. Now you just need to create the new my.cnf 
file. Usually, it’s sufficient just copy the one currently in use to the new installation. Be sure to have the new data 
directory specified in this my.cnf file.
Now, shut down the current mysqld
# mysqladmin -u root -p shutdown
Then start mysqld in your normal fashion. Since you have used symbolic links, the normal way in which you 
invoke mysqld (i.e., mysqld_safe &) will now use the new version of MySQL. To revert to the old version, follow the 
same steps, but point /usr/local/mysql to the old version instead of the new one.
Note: After starting the MySQL server repair all the tables.
Source Upgrade Process:
Download the latest version of MySQL to upgrade.
Extract the file and go to the specific directory and execute the below commands.
MySQL Database Administration
 106 
# ./configure –prefix=/usr/local/mysql (should be the same location of the existing MySQL installation)
# make
# make install 
