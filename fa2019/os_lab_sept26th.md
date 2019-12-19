Scheduling and Memory:

malloc and free;

virtual memory manager policy system.

General purpose schedulers :
  * SJF Scheduler
  * RR Scheduler
  * Multi-level Schedulers.

What if we need to schedule processes to handle real world events:
  * Real-time CPU Scheduling.
    * Soft real-time systems (clock on the computer is enough)
    * No guarantee, only that the process will be given 
      preference over noncritical processes.
    * Hard real-time systems.
      * Stricter requirements, task must be serviced by
        its deadline... Failure to meet deadline is the
        same as not scheduling at all.
  #RTS considerations :
    * Preemptive priority-based scheduler necessary
      * Why is it necessary?
    * What kind of RT processes can we have to schedule?
      * Unexpected - no real way to plan for these.
      * Periodic (Every few seconds check something.)
    * Potentially some strategies/information provided that we can us to handle this kind.
      * Slices up data, the action takes time, reacts and responds to stimuli.

## Example

p1 - Period = 50, time = 20
p2 - Period = 100, time = 35

deadline would overwhelm if p1 < p2 priority. (shortest job first is best.)

algorithm for real time scheduling
Rate-Monotonic RTS :
  * Always schedule the higher priority to the shorter period.


What if we change the system : p1 takes longer.
  Earliest-Deadline-First Scheduling,
  * Similar to Rate-Monotonic, run the one whose deadline is first.
  * Doesn't care about the period.
  Primary driver for deadline and hard-line time priority scheduling.

Hybrid : Take both systems, schedule the shorter period as long as it doesn't overstep a deadline.

Proportional Share Scheduling:
* Give T shares among all applications
* Give N shares to each application
  * Each application gets N/T of the total processor time.
* Works similar to "locks" in processes. Can only get shares of time if there
  are enough available for their request.



What is memory?
  Data storage.

Turing machine's defined memory as an infinite tape.

if memory isn't infinite, then how do we manage it?
  * Parkinson's Law: "Programs expand to fill the memory available to hold them."

