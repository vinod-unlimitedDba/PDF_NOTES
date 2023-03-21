


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


   
   
   

CHAPTER 2 Database Administration
