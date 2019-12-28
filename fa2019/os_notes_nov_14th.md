Storage/Filesystems/IO

Introduced Threads/Locks/Etc

Moving into the Final Component of the Semester : Files/Filesystems.

High Level : What is Storage :

  What kind of storage can we have?
  * Volatile and Nonvolatile :
    * Memory (cahce, ram, etc)
    * Storage (HDDs/SDDs/Magnetic tapes)

  Logical Blocks - Smallest block of data that is read/written in an HDD
  Seek Time :
    * Time to move the arm to the correct cylinder
  Rotational Latency : Time to rotate to the desired sector.
  Host Attached Storage : Storage physically in your computer
  Storage Area Network : Faster and higher speed for storage

How might we schedule use of storage?
  Disk Operation : Input or Output
  What the disk address is
  What memory address is?
  Quantity of data.

Easiest way to schedule : First Come First Server
SSTF Shortest Seek Time Find
SCAN Scheduling : Move arm farthest out postition to start then schedule requests as it moves in towards the middle 
  * reverse the process
Sometimes called "Elevator Algorithm"
There are a few extensions of this approach as well.


Low level formatting :
  Process of dividing disc up into sectors that disc controll can read and write.
  Writes on the header/foot details that the disc controll will use
  builds special data structure for disc controller
  possible for logic blocks size to be changed.
Was done when disc contorllers were separate from drive


What is RAID?
Reliable/Redundant Array of Independent Disks

Goals : Reliable, Redundant
      : Performance : RAPID : through parallelism
      : Levels are different method sof implementation for either one or both of the goals trying to be met.
      : Popular RAID :
        : RAID 0  : Spread everywhere, if it dies you're fucked.
        : RAID 1  : Mirror data across multiple disks for quick speed of reading, same amount of writes.
        : RAID 5  : Parity, write "Rows" across the disks, and you can see the row as a single disk over multiple disks.
        : RAID 10 : It's a RAID 0 spread over RAID 1 striping.
        
