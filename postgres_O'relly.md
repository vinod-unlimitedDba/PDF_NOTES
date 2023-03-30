


catalog
Catalogs are system schemas that store PostgreSQL built-in functions and metadata. Each database is born containing two catalogs: pg_catalog, which has all the
functions, tables, system views, casts, and types packaged with PostgreSQL; and
information_schema, which consists of ANSI standard views that expose Post‐
greSQL metainformation

 information_schema catalog is one you’ll also find in MySQL and SQL Server.
The most commonly used views in the PostgreSQL information_schema are col
umns, which lists all table columns in a database; tables, which lists all tables (in‐
cluding views) in a database; and views, which lists all views and the associated SQL
to build rebuild the view. 



extension
Introduced in PostgreSQL 9.1, this feature allows developers to package functions,
data types, casts, custom index types, tables, GUCs, etc. for installation or removal
as a unit. Extensions are similar in concept to Oracle packages and are the preferred
method for distributing add-ons


table
Tables are the workhorses of any database. In PostgreSQL, tables are first of all
citizens of their respective schemas, before being citizens of the database


foreign table and foreign data wrapper
Foreign tables showed their faces in version 9.1. These are virtual tables linked to
data outside a PostgreSQL database. Once you’ve configured the link, you can query
them like any other tables.

tablespace
A tablespace is the physical location where data is stored. PostgreSQL allows ta‐
blespaces to be independently managed, so you can easily move databases or even
single tables and indexes to different drives.


function
Functions in PostgreSQL can return a scalar value or sets of records. You can also
write functions to manipulate data; when functions are used in this fashion, other
database engines call them stored procedures.


operator
Operators are symbolic, named functions (e.g., =, &&) that take one or two argu‐
ments and that have the backing of a function. In PostgreSQL, you can invent your
own.


data type (or just type)
Every database product has a set of data types that it works with: integers, characters,
arrays, etc. PostgreSQL has something called a composite type, which is a type that
has attributes from other types.


cast
Casts are prescriptions for converting from one data type to another. They are
backed by functions that actually perform the conversion.



sequence
A sequence controls the autoincrementation of a serial data type. PostgresSQL au‐
tomatically creates sequences when you define a serial column, but you can easily
change the initial value, increment, and next value. 


row or record
We use the terms rows and records interchangeably. In PostgreSQL, rows can be
treated independently from their respective tables. This distinction becomes ap‐
parent and useful when you write functions or use the row constructor in SQL



rule
Rules are instructions to substitute one action for another. PostgreSQL uses rules
internally to define views. As an example, you could create a view as follows:

   CREATE VIEW vw_pupils AS SELECT * FROM pupils WHERE active;
   
Behind the scenes, PostgresSQL adds an INSTEAD OF SELECT rule dictating that
when you try to select from a table called vw_pupils, you will get back only rows
from the pupils table in which the active field is true.   
   
   
   
   
   
   
   The main configuration files that control basic operations of a PostgreSQL server instance are:
postgresql.conf
------
Controls general settings, such as memory allocation, default storage location for
new databases, the IP addresses that PostgreSQL listens on, location of logs

Version 9.4 introduced an additional file called postgresql.auto.conf,
which is created or rewritten whenever you use the new ALTER SYSTEM SQL com‐
mand. The settings in that file override the postgresql.conf file.

pg_hba.conf

Controls security. It manages access to the server, dictating which users can log in
to which databases, which IP addresses or groups of addresses can connect, and
which authentication scheme to expect.

pg_ident.conf

If present, maps an authenticated OS login to a PostgreSQL user. People sometimes
map the OS root account to the postgres superuser account. Each authentication
line in pg_hba.conf can dictate usage of a different pg_ident.conf file.


 listen_addresses
Informs PostgreSQL which IP addresses to listen on. This usually defaults to lo
calhost or local, but many people change it to *, meaning all available IP ad‐
dresses.

max_connections
The maximum number of concurrent connections allowed.

shared_buffers
Defines the amount of memory shared among all connections to store recently
accessed pages. This setting profoundly affects the speed of your queries.
  
effective_cache_size
An estimate of how much memory you expect to be available in the OS and Post‐
greSQL buffer caches. This setting has no effect on actual allocation, but query
planner figures

work_mem
Controls the maximum amount of memory allocated for operations such as sorting,
hash join, and table scans. The optimal setting depends on how you’re using the
database, how much memory you have to spare, and whether your server is dedi‐
cated to PostgreSQL or not.


maintenance_work_mem
The total memory allocated for housekeeping activities such as vacuuming (prun‐
ing records marked for delete). You shouldn’t set it higher than about 1 GB. Reload
after changes.

    ALTER SYSTEM set work_mem = 8192;
  
  you may need to restart the service. If just need to reload it, here’s a convenient command:

SELECT pg_reload_conf();
    

pg_hba.conf
The pg_hba.conf file controls which and how users can connect to PostgreSQL databa‐
ses. Changes to the file require a reload or a server restart to take effect. 


Example 2-3. Sample pg_hba.conf
# TYPE DATABASE USER ADDRESS METHOD
# IPv4 local connections:
host all all 127.0.0.1/32 ident


Authentication method. The usual choices are ident, trust, md5, and pass
word. Version 9.1 introduced the peer authentication method. The ident and
peer options are available only on Linux, Unix, and the Mac, not on Windows.
More esoteric options, such as gss, radius, ldap, and pam, may not always be
installed.


IPv4 syntax for defining network range. The first part—in this case,
192.168.54.0—is the network address, followed by /24 as the bit mask. In our
pg_hba.conf, we allow anyone in our subnet of 192.168.54.0 to connect as long
as they provide a valid md5 hashed password.


IPv6 syntax for defining network range. This applies only to servers with IPv6
support and may prevent pg_hba.conf from loading if you add this section
without actually having IPv6 networking.



“I edited my pg_hba.conf and now my server is broken.”
Don’t worry. This happens quite often, but it’s easily recoverable. This error is generally
caused by typos or by adding an unavailable authentication scheme. When the post
gres service can’t parse pg_hba.conf file, it blocks all access for safety or won’t even start
up. The easiest way to figure out what you did wrong is to read the log file. This is located
in the root of the data folder or in the pg_log subfolder.



# Authentication methods

PostgreSQL gives you many choices for authenticating users
 trust, peer, ident, md5, and password. There is also reject, which applies an immediate denial.


trust
The least secure of the authentication schemes. It allows people to self-identify and
doesn’t ask for a password. As long as the request meets the IP address, user, and
database criteria, the user can connect. 

md5
Very common, requiring an md5-encrypted password to connect.
password
Uses clear-text password authentication.

ident
Uses pg_ident.conf to see whether the OS account of the user trying to connect has
a mapping to a PostgreSQL account. No password is checked.

peer
Uses the client’s OS name from the kernel. It is available only for Linux, BSD, Mac
OS X, and Solaris, and can be used only for local connections

Managing Connections
-----

Every once in a while, someone else (never you, of course) will execute a query that he
didn’t intend to and end up hogging resources. You could also run into a query that’s
taking much longer than what you have patience for. 

If one of these things happens,
you’ll want to cancel the query on the connection or kill the connection altogether.

we find ourselves resorting to three SQL commands to cancel
running queries and terminate connections. Here is a typical sequence to follow:

1. Retrieve a listing of recent connections and process IDs:

               SELECT * FROM pg_stat_activity;
               
 2. Now cancel all active queries on a connection: This does not terminate the connection itself, though.              

               SELECT pg_cancel_backend(procid)

3. Kill the connection:
      
      SELECT pg_terminate_backend(procid)
      
      
 PostgreSQL lets you embed functions that perform actions within a regular SELECT
query. So, although pg_terminate_backend and pg_cancel_backend can act on only
one connection at a time, you can kill multiple connections by wrapping them in a
SELECT.


    SELECT pg_terminate_backend(pid) FROM pg_stat_activity WHERE usename = 'some_role';

or before version 9.2:

    SELECT pg_terminate_backend(procpid) FROM pg_stat_activity WHERE usename = 'some_role';
    
    
 Roles
 ----
PostgreSQL represents accounts as roles. Roles that can log in are called login roles. Roles
can be members of other roles; roles that contain other roles are called group roles. 
 
 group roles can be members of other group roles and so on ad infinitum, but don’t
go there unless you have a knack for hierarchical thinking.)


Note:

Recent versions of PostgreSQL no longer use the terms users and
groups. You will still see these terms bandied about on discussion
boards; just know that they mean login roles and group roles re‐
spectively


Inheriting rights from group roles
One quirk (or convenience) in PostgreSQL is the ability to specify that a group role not
pass its rights to member roles. To avoid having to remember the default value, you
should always append the INHERIT keyword if you want members to inherit the rights
of the parent role, and NOINHERIT if you don’t want them to inherit the rights of the
parent role.


SET ROLE royalty;

Keep in mind that this is per-connection session and not a permanent delegation of rights


A more powerful impersonation than SET ROLE some_role is SET SESSION AUTHORI
ZATION some_role. The main differences between SET ROLE and SET SESSION AUTHOR
IZATION are:
• Only superusers can execute SET SESSION AUTHORIZATION, and it allows them to
impersonate any user regardless of role membership.
• SET SESSION AUTHORIZATION changes the values of the current_user and ses
sion_user variables to those of the user being impersonated.

 
    

CHAPTER 2 Database Administration



Template Databases
A template database is, as the name suggests, a database that serves as a model for other
databases. When you create a new database, PostgreSQL copies all the database settings
and data from the template database into yours.


You should never alter template0 because it is the immaculate mod‐
el that you’ll need to copy from if you screw up your templates. Make
your customizations to template1 or a new template database you
create.



The basic syntax to create a database modeled after a template is:

        CREATE DATABASE my_db TEMPLATE my_template_db;

PostgreSQL restricts the database from being
edited or deleted. Any role with CREATEDB rights can use the database. To make any
database a template, run the following SQL as a superuser:

     UPDATE pg_database SET datistemplate = TRUE WHERE datname = 'mydb';

Using Schemas
Schemas organize your database into logical groups. If you have more than two dozen
databases on your server, consider cubbyholing them into schemas in a single database.

Installing Extensions
---

Getting an extension into your database takes two installation steps. First, download
the extension and install it onto your server. Second, install the extension into your
database.

Step 1: Installing on the server

installation of extensions on your server,overall idea is to down‐
load binary files and requisite libraries, then copy the respective binaries to the bin and
lib folders and the script files to share/extension (versions 9.1 and above) or share/
contrib (pre-9.1). This makes the extension available for the second step.

> To check already available extensions on server
      SELECT * FROM pg_available_extensions;

Step 2: Installing into a database (pre-9.1)

As an example, on a CentOS running version 9.0, to run the SQL script for the pgAdmin
pack extension, type the following from the OS command line:
psql -p 5432 -d postgres -f /usr/pgsql-9.0/share/contrib/adminpack.sql

Step 2: Installing into a database (version 9.1 and later)
The new extension support makes installation much simpler and more consistent. Use
the CREATE EXTENSION command to install extensions into each database. The three big
benefits are that you don’t have to figure out where the extension files are kept (share/
extension),

  CREATE EXTENSION fuzzystrmatch;

extensions must be installed by a superuser. Most extensions fall into this genre.

We suggest you create one or more schemas to house extensions to keep them separate
from production data. After you create the schema, install extensions into it through a
command like:

    CREATE EXTENSION fuzzystrmatch SCHEMA my_extensions;

Upgrading to the new extension model

 using a version of PostgreSQL older than 9.1 and restored your old da‐
tabase into version 9.1 or later during a version upgrade, all extensions should continue
to function without intervention.


For example, suppose you had installed the tablefunc extension (for cross-tab queries)
to your PostgreSQL 9.0 in a schema called contrib, and you’ve just restored your da‐
tabase to a 9.1 server. Run the following command to upgrade:

         CREATE EXTENSION tablefunc SCHEMA contrib FROM unpackaged;

This command searches through contrib, finds all components for the extension, and
packages them into a new extension object so it appears in the pg_available_exten
sions list as being installed.


Popular extensions
------

btree_gist
Provides GiST index-operator classes that implement B-Tree equivalent behavior
for common B-Tree services data types.

btree_gin
Provides GIN index-operator classes that implement B-Tree equivalent behavior
for common B-Tree serviced data types. 

postgis
Elevates PostgreSQL to a PostGIS in Action state-of-the-art spatial database out‐
rivaling all commercial options. OGC GIS data, demo‐
graphic statistics data, or geocoding, you don’t want to be without this one.



fuzzystrmatch
A lightweight extension with functions such as soundex, levenshtein, and meta
phone for fuzzy string matching.

hstore
An extension that adds key-value pair storage and index support, well-suited for
storing pseudonormalized data. If you are looking for a comfortable medium be‐
tween a relational database and NoSQL, check out hstore.



dblink
Allows you to query a PostgreSQL database on another server. Prior to the intro‐
duction of foreign data wrappers in version 9.3, this was the only supported mech‐
anism for cross-database interactions.


pgcrypto
Provides encryption tools, including the popular PGP. It’s handy for encrypting
credit card numbers and other top secret information stored in the database.



xml
An extension that added an XML data type, related functions, and operators. The
XML data type is now an integral part of PostgreSQL, in part to meet the ANSI SQL
XML standard.































