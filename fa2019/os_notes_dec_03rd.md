Posix Inode :
* Size
* Device ID
* User ID
* Group ID
* file mode
* file protections
* time stamps
* link count
* pointers to disk blocks

Inode Cat Example : 

Posix Inode to find the symbolic links etc

What does a file system provide an OS : 
* Organization
* When things are modified
* Size/Data on file

##Newer stuff : Different file systems.

FAT32 :
  Three different sections for FAT32
    * Reserved Sectors
      * Very beginning of drive addressing
      * First reserved sector is boot sector
      * Number of reserved sectors defined in boot sector, but typically 32 for FAT32
    * Fat Region
      * Maps of the data region
      * Usually contains 2 copies
    * Data Region
      * Where all the file/directory data is stored
  * Nearly all OS support FAT
  * Only can support up to 4GB files
  * Can only support up to 2 TiB volume
  * Date Range : 1980-01-01 to 2099-12-31
  * Date Resolution :
    * 2 seconds for last modified time
    * 10ms for creation time
    * 1 day for access date
    * 2 seconds for deletion time

Windows NTFS :
  * Uses B+ trees to index file system data
  * Has Master File Table stores all file, directory and metafile metadata
  * Date Range : 1601-1-1 to 60056-06-28
  * Date Resolution 100ns

What do we want in a future file system?

Bigger file size, more data, protection for failing systems


ZFS :
  * Logical Volume Manager (LVM) from Sun
  * Designed to solve data integrity issues not solved by conventional filesystems and what RAID commonly fails to solve as well.
  * Timestamp resolution : 1ns


  All modern file systems are similar to ZFS
  
  
BTRFS :
  * Stands for B-Tree File System :
    * Developed by Oracle: worked on by google and others
  * It's a GPL licensed experimental copy-on-write filesystem for Linux
  * Intended to address lack of the following in linux filesystems : 
    pooling
    snapshots
    checksums
    multi-device spanning


Apple_File_System is basically ZFS or BTRFS

Modern File Systems ^^^^^^^^^^^


Google File System :
  * Key Observations
    * Expect hardware to fail
    * Files can be massive
    * Files tend to be mutated by appending new data versus overwriting existing
    * Designing the applications to make use of the FS adds flexibility 


Memory File System

Distributed File System in the RAM


Properties of Virtual Machines :

Partitioning, Isolation (run motiple operating systems, divide system resources, provide fault and security isolation, preserve performance with advanced resources, encapsulation, saves the entire state of the virtual machine.)


