Threads : What are they good for? 
  * Responsiveness.
  * Resource Sharing
  * Economy of scale
  * Scalability

Midterm Nextweek (Thursday)

What is a thread :
  _Code_ _Data_ _Files_
  Registers
  *Stack*

Multithread
        _Code_ _Data_ _Files_
  Registers   Registers   Registers
  Stack       Stack       Stack


Pass your data pointers to a thread access.
Don't do global (you can do it otherwise)

How might we use this for a client-server model?

Signals/Wait entire midterm

Serial vs Parallel :
  * Serial components of a programs are ones that need to be completed in order and can't be done in parallel.
  * Parallel components of a program are pieces ofa program that can be done in any order.

Multicore Programming
  * What does having multiple processors or multiple cores on a single chip provided u s over a single processor/core systems with threads
    * Concurrent vs Parallel - 
      Concurrent runs at the same time, parallel runs one then the other.
    * Speed up? How much of an improvement?
    * Amdahl's Law:
      * S - portion of program that is serial
      * N - number of processing cores
      * speedup <= 1/(S + (1 - S)/N)

What makes this hard?
  * Identifying Tasks :
    * How do we identify the parts of an application that are independent and can run in parallel?
    * How do we identify computations that can be done in parallel?
  * Balance :
    * Is it worth making a task run as a separate thread?
  * Data Splitting :
  * Data Dependency :
    * What happens if tasks depend on data from other tasks?
    * How do we insure this dependency is met?
  * Testing and Debugging :
    * Likely be the most difficult part
  * Excited to get started ??


Data vs. Task
  * Data Parallelism:
    * Focuses on distributing subsets of same data across numerous courses :
      * Calculations on same data
  * Task Paralellism:
    * Focuses on distributing tasks across numerous cores:
      * Unique Tasks

Thread Models :
  * Ways threads can be impleented by the system
  * Describe kernel to user thread mappings:
    * One-to-Many
    * One-to-One
    * Many-to-Many
    * Two-level Model

One-to-Many     : Maps many user threads to one kernel thread
                : Management done by thread library
                : Entire process has to block if a thread calls a blocking system call.

One-to-One      : One kernel thread fo every user thread
                : Provides more concurrency as no longer have to block more than the single thread that called the blocking system call.
                : More overhead, restricts number of threads you can have.
Many-to-Many    : Multiplexes many user-level threads to a smaller or equal number of kernel threads.
                : Number of kernel thraeds can vary/be defined base on system type.
                : Doesn't suffer shortcomings of previous two models.
Two-level Model : Same as many-to-many but also allows a user thread to be bound to a kernel thread.


Thread libraries :
  * Provide programmers API for creating/managing threads.
  * Three Main Libraries :
    * POSIX Pthreads:
      * POSIX STANDARD (IEEE1003.1c)
      * Defines a specification not implementation
      * Portability Operating System Interface

    * Windows Threads
    * Java Threads:
      * Java Threads API is generally implemented using what is on the system.

Explicit Threads :
  PThreads and other libraries provide us with the ability to explicitly define threads and how many threads we create.
  What do programmers have to keep track of?
  What do we get data back from threads?

OpenMP
* Set of compiler directives as well as API for programs written in C, C++, or FORTRAN
* Does more than just identify parallel sections of code but that's what we're going to discuss for the moment
* Only need to identify with compiler directive for it to work.

Can use the #pragma omp parallel for directive


