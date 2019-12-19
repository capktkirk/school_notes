Notes :

Questions :
  

Pivoting from the signals to scheduler.

CPU/IO Burst :
  * CPU scheduling works due to observed trait of processes.
  * Swtch between CPU execution and I/O wait.
    The split between CPU execution and I/O is about 50/50
    
    
  Preemptive vs non-preemptive scheduling :
    How we make the decisions on who or what can be released to the processor.
    Scheduling Decisions are :
      * Non-preemptive if:
        * When a proces switches from the running state to the waiting state (for example, as a result of an I/O request or invocation of wait() for termination fo child process.)
        * when process terminates.
      * Preemptive if: (Modern OS's added this) :
        * When a process switches from running state to ready state (for xample when an interrupt occurs)
        * When a process switches from waiting state to ready state (for example, at completion of I/O)
        * Preemptive scheduling can lead to race conditions.

    What kinds of criteria should a scheduler satisfy?
      * CPU Utilization
      * Throughput
      * Turnaround time
      * Waiting time
      * Response time

    We'll use these criterion to discuss effectiveness of the variety of scheduling algorithms.

    Simplest Schedule :
      First-Come, First Served (FCFS)
    * Implemented with FIFO Queue
    * Example: 
      Burst Time is the amount of time the process uses before giving up the CPU
      GANT CHART :
      [______________ P1 ____________ | _____ P2 _____ | ____ P3 ____]
      0                              24                27            30
      avg waittime is 0 + 24 + 27 divided by number of processes (3) : 17/ms

      *Process*     :   *Burst Time*    : *E1 Arrival Order*    : *E2 Arrival Order*
      P1          :   24            : 1                   : 3
      P2          :   3             : 2                   : 1
      P3          :   3             : 3                   : 2

    If P2, then P3, then P1, the wait-time would be 3 instead.

    What was the problem with FCFS : Doesn't determine the fastest way to load things.
    * How to solve?
    * If the scheduler has an idea about the burst time, it can make decisions on how to schedule
      the processes.

    * Use FCFS to break times (shortest job first)

    _*SHORTED JOB FIRST*_ SJF
    Example :
    Process : Burst Time
        P1  :   6
        P2  :   8
        P3  :   7
        P4  :   3

      Queue : [ _ P1 _ | _ P2 _ | _ P3 _ | _ P4 _ ] avg waittime = 7
      SJF   : [ _ P4 _ | _ P1 _ | _ P3 _ | _ P2 _ ] avg waittime = 5.3~

      Where do we determine burst time?
      We use an exponential average.
      SJF Prediction gets close enough. (Approx. Burst time)

      Preemptive SJF :


      *Process*     :   *Arrival Time*    : *Burst Time*
      P1          :   0               : 8
      P2          :   1               : 4
      P3          :   2               : 9
      P4          :   3               : 5

      Premptive SJF   : [ _ P1 _ | _ P2 _ | _ P4 _ | _ P1 _ | _ P3 _ ] avg waittime = 6.5
                        0       1         5        10       17       26

      What if it was just SJF : 7.5/ms

      Priority on burst time will cause starvation which means the largest burst times may never
      get to run. (There needs to be a "time waiting" to keep value.)


##Priority Scheduling:

  Priority Queue.
  Define it by a number/int value.
  Fixed range, 0 to something.
  Figure out if 0 is highest or lowest. (usually the highest)


      *Process*     :   *Burst Time*    : *Priority*
      P1          :   10              : 3
      P2          :   1               : 1
      P3          :   2               : 4
      P4          :   1               : 5
      P4          :   5               : 2


      Priority Queue  : [ _ P2 _ | _ P5 _ | _ P1 _ | _ P3 _ | _ P4 _ ]
                        0       1         6        16       18       19

  Indefinite Blocking or Starvation are a problem in Priority queues.

  Modern schedulers are hybrids.

  As time goes on, you can increase the priority of a process if it isn't being
  processed. This process is called *Aging*

  Round Robin Scheduler : Most common used on computers.
  * Everyone gets a specific amount of time.
  * Preemption is required to enable system to switch between processes.
  * Designate a small unit of time (time slice or quantum)
    * A time quantum is generally 10-100ms in length.
    * Usually scheduled to be about 80% of the bursts of the processes.
    * Think of ready queue as a circular queue.1
