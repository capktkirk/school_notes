Schedulers :

What are the issues with RR Scheduling?

F(p, waittime) : A function to deal with priority waittimes.

Function(Priority, Waittime)

There is an instance of a scheduler that has priority and aging (it doesn't get rescheduled to
it's original position, due to Dixon's oversight.)

Round Robin as a solution :
Time Quanta's : 
  * With small time quanta the overhead of context switching would be noticable.

Why might we want to schedule some differently?
  * System Process
  * Foreground Jobs
    * Interactive Processes
    * Interactive editing processes
  * Background
    * Batch Processes
  * Student processes (Example from old book)
  * Acronyms for schedulers : SLURM and FLUX scheduling on super computers. TACC (Another scheduler)
* Multilevel Queue
  * Highest Priority
    * system -> interactive -> interactive editing -> batch -> student
  * How might we implement a multi-leve queue?
    * Absolute priority - no process in lower priority queues can run until higher priority queues are empty
      * What is the drawback of this style? low-priority may not run, we need aging.
      * Then you bump it up in priority, and then return the priority to where it was.
    * Time Slicing among queues
    * Alternatively what happens if we have a process lasting too long?
      * Reverse aging : It loses priority.


##Shared CPU Time : Multi-processor scheduling :
  * Asymmetric Multiprocess
    * A single chip on a "compute" card is the one that handles all the other nodes scheduling.
  * How do we make sure we don't schedule the same process twice?
  * How do we ensure processes aren't lost from the ready queue?
  
  * Shared M Process
    * Potentially shared data structure with ready queue
    * Load balancing across processors.
    * NUMA = Non-uniform memory access speeds (NUMA).
