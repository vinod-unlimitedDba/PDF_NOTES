



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
