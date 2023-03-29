



CHAPTER3 Introduction to the RMAN Architecture
----------------

control file thus separates its internal data into two types of records:
circular reuse records and noncircular reuse records. Circular reuse records are
records that include information that can be aged out of the control file if push
comes to shove.


Noncircular
reuse records are those records that cannot be sacrificed. If the control file runs
out of space for these records, the file expands to make more room. These
records include datafile and log file lists.

record of RMAN backups in the control file falls into the category of
circular reuse records, meaning that the records will get aged out if the control
file section that contains them becomes full. 

catastrophic to a recovery situation: without the record of the backups in the control file, it is as
though the backups never took place. Remember this: if the control file does not
have a record of your RMAN backup, the backup cannot easily be used by
RMAN for recovery. There is a command called catalog that makes it possible
to refresh the control file records,



Snapshot Control File
--

Control file is busy with operating updating scn when checkpoint happened and other sorting all metadata. 
control file is always changing rman need consistent image to work rman will create the snapshot control file while 
taking backup and resync operations 

At the beginning of these operations, RMAN refreshes the snapshot control file from the actual control file, 
thus putting a momentary lock on the control file.RMAN switches to the snapshot and uses it for the duration of
the backup; in this way, it has read consistency without holding up database activity.



In RMAN lingo, the channel is the server process at the target database that coordinates the
reads from the datafiles and the writes to the specified location during backup.



RMAN in Memory
RMAN builds buffers in memory through which it streams data blocks for
potential backup. This memory utilization counts against the total size of the
PGA and, sometimes, the SGA.


There are two kinds of memory buffers. 
Input buffers are the buffers that are filled with data blocks read from files that are
being backed up. 

Output buffers are the buffers that are filled when the memoryto-memory write occurs to determine whether a particular block needs to be backed up. When the output buffer is filled, it is written to the backup location.


Input Memory Buffers
When you are backing up the database, the size and number of input memory
buffers depend on the exact backup command being executed


Primarily, they
depend on the number of files being multiplexed into a single backup.
Multiplexing refers to the number of files that will have their blocks backed up to
the same backup piece.



keep the memory allocation within reason, the following rules are applied to the memory buffer sizes based on the number of files being backed up together (this is known as multiplexing):

If the number of files going into the backup set is four or less, then RMAN
allocates four buffers per file at 1MB per buffer. The total will be 16MB or
less.

If the number of files going into the backup set is greater than four but no
greater than eight, then each file gets four buffers, each of 512KB. This
ensures that the total remains at 16MB or less.

If the number of files being multiplexed is greater than eight, then RMAN
allocates four buffers of size 128KB. This ensures that each file being
backed up will account for 512KB of buffer memory.


The formula for the number of input buffers is slightly different if you are
using ASM. In this case the number of buffers that will be created is the same as
the number of physical disks in the ASM disk group. In this case, the size of
these buffers is dependent on the operating system that the database is running



Memory Buffers on Restore
During a restore from a disk backup, the input buffers will be 1MB, and RMAN
will allocate four buffers per channel. When restoring from tape, RMAN
allocates four input buffers with a size of BLKSIZE, which defaults to 256KB.
The output buffers on restore are always 128KB, and there will be four of them
per channel.



CHAPTER4 Oracle Database 12c Multitenant

maxpiecesize parameter, you can control the size of a backup set piece.

control the maximum number of files that RMAN can open at one time with the maxopenfiles parameter.

    Configure channel 1 d1 device type disk  maxpiecesize 100m maxopenfiles 8 rate 100mb;

the difference between the maxpiecesize
parameter and the maxsetsize parameter: maxpiecesize limits the size
of the individual backup set pieces and has no impact on the overall
cumulative size of the backup. The maxsetsize parameter, on the other
hand, can and will limit the overall size of your backup,


![image](https://user-images.githubusercontent.com/108070848/228440241-d43927a8-5e25-4e46-8957-c96f8e86aa16.png)



maxsetsize to limit the size of the entire backup
that is being created. While your database might be smaller than the
maxsetsize defined initially, it could quickly grow beyond the
maxsetsize, causing your database backups to fail


exclude specific tablespaces during an automated backup,
which Oracle allows you to do with the configure command.

configure exclude for tablespace old_data

When enabled, backup optimization will cause Oracle to skip
backups of files that already have identical backups on the device being backed
up to. Here

configure backup optimization on;

SNAPSHOT CONTROL file is a pointin-time
copy of the database control file that is taken during RMAN backup operations.
The snapshot control file ensures that the backup is consistent to a given point in
time.

if you add a tablespace or datafile to a database after the backup has
started (assuming an online backup, of course), that tablespace or datafile will
not be included in the backup


Using the Format String
-----------


%U syntax element in the previous example tells RMAN to substitute a systemgenerated
unique identifier for the filename. %U then keeps each backup
filename unique.



%a    ----------    Indicates the activation ID of the DB should be substituted 
%b     --------     spicifies name without any directory paths can only be used with set newname 
%c     -------     spicifies the copy of the backup piece within  a set of duplexed backup piece 
%d     --------     indicates name of the database should be subsituted 
%D      -------     indiacted current  day of the month fron the gregrian calendar  
%e      -----      indiacted archive log sequence 
%f     -----       Indicates absolute file number  should be substitute 
%F     -------     provide a unique and repeatable name combines DBID 

%h  ------------  Indicate archive redo log  thread number

%I  ---------- Indiactes that DBID should be subsituted 

%M ------    Indiactes the month gregorain calendar in the format MM

%N  ----  Indiactes the tablespace name be substitute 

%n ------ Indicates  name of the database ,padded on the right with x character 

%p   -----  piece no with backup set should be substitute value start with 1 increment by 1

%s   -------  Indicates that backup set substitute

%t  -------- indicate the timestamp %T indiacte that year month  format YYYYMMDD

%u  ---------  Indicate eight-character name consisting compression representation of the backup set or image 


%U default naming pattern provide a system -generated unique filename for Rman related file 

%Y -- indicate that year in the format YYYY should be substitute 






































