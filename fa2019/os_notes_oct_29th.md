What kinds of problems arise from threaded programs?

Producer :
while (true){
/* produce an item next produced */
while (counter == BUFFER SIZE);
/* do nothing */
buffer[in] = next produced;
in = (in + 1) % BUFFER SIZE;
counter++
}

CONSUMER :
while(true){
while (counter ==0); /*do nothing*/
next consumed = buffer[out];
out = out +1 % buffer size
counter--;
}
}

Shared Counter (It's global between them)
Run into race conditions.
threaded libraries set everything up for you,
assignment6 you have to set everything up.

Interprocess communication

vector is threadsafe by default in C++

build your own bounded buffer for assignment 6
make a stack (counter is where you take things out and put things in.)

extra credit : synchronization (only worth 5)

Go into slides and write stuff down/read stuff.

Provide protocol to prevent two process from executing in their critical section at the same time.
Entry/Exit section.

Solution : 
  * Needs mutual exclusion :  Only one process can execute a critical section at a time.
  * Progress : If no process is executing in a critial section then if multiple processes request permission a decision of who gets to execute has to be made.
  * Bounded Wait : There exists a bound/limit on how long a process has to wait for access to execute it's critical section.

    Tangent :
    * A lot of things have these race conditions.
    * Steal something from database theory for one of the solutions.

  * Peterson's Solution :
    * Restricted to two processes
    * Two shared data items :
      * int turn
      * boolean flag[2]
    * Denote processes as Psub0 and Psub1
    * PsubI is the processes in execution
    * PsubJ is the other process.


turn    = 0
flag[0] = 0
flag[1] = 0

do{
flag[i] = true;
turn = j;
while (flag[j] && turn == j);
(critical section)
flag[i] = false;
(remainder section)

}while(true);

Psub0                             Psub1
flag[0] = 1                       flag[1] = 1;
turn = 1                          turn = 0;
while (flag[1] && turn == j)      while (flag[0] && turn == 0)
(fail)                            spinlock
critical section                  spinlock
..                                spinlock
..                                spinlock
..                                (while flag[j] && turn == j) breaks.
flag[0] = false;                  enter critical section now


Synchronization hardware
* Critical-section problem can be solved simply in a single-processor environment if we can prevent interrupts while a shared variable is modified.
* Assumption is with hardware instructions to provide synchronization we can insure no interrupts occur.



test_and_set
boolean test_and_set(boolean *target){
  boolean rv = *target;
  *target = true;
  return rv;
}

do{
  while (test_and_set(&lock)); /*do nothing*/
  /*critical section*/
  lock = false;
  /*remainder section*/
} while (true);

//Make critical section small to minimize waiting.

Why won't this work?
* Disabling interrupts on multiprocessor/core systems adds significant delays to the system.
* How do we solve this : 
  * Special hardware instructions that are atomic
  * Atomic instructions are instructions that act as one uninterruptable unit.

Another Instruction :

int compare and swap (int *value, int expected, int new value){
  int temp = *value;
  if(*value == expected){
    *value = new value;
  }
  return temp;
}

do{
  whie(compare and swap(&lock, 0, 1) != 0);
  /*do nothing*/
  /*critical section*/
  lock = 0;
} while(true);

Tangent : 5th and 6th assignments basically the same thing.
  producer = domain names. Putting it into a bounded buffer
  Consumer Threads are going to read out the host names.
  Write that into a single output file.
  At least 2 consumers, at least 1 producer thread.
  
  Once full producer stalls
  Once empty consumer stalls.
  
  Protect bounded buffer and output file.
  

How do we do this in software?
  * Do you think we get access to hardware-based instructions as programmers?
  * One Solution is Mutex Locks : Mutually Exclusive Locks.
    * Available as part of POSIX Pthread Library
    * We'll be discussing general form
    * Performed Atomically
    * Mutex Locks are the simplest of all synchronization tools

Mutex Locks:

aquire(){
while (!available);
wait
available=false;
}

release(){
  available = true;
}

do{
  aquire lock
    critical section
  release lock
    remainder section
} while(true);

On final you can ("lock_lock") ("unlock_lock")

Mutex's are known as Spinlocks :
  * Mutex implementation has a busy waiting for lock to become available
  * This busy waiting style of lockdown is known as _spinlock_
  * Why is a spinlock bad in a real system?
    * In a real system, it can lock things down. In reality it is only a problem on a huge system.
    * Can be okay for small critical sections.
  * Semphore : Spinlock : behave similar to mutex
  * provide more sophisitacted ways to do synchronization : 
    * It can be thought of as an integer.
    * Apart from initialization can only be accessed via two atomic operations :
      * Wait()
      * Signal()
wait(S){
  while(S<=0); (Busy wait)
  
}

Semaphore Initialization :
* A variety of choices;
* Binary Semaphores :
  * A max value of 1

You can use semaphores on project 5;

* Counting Semaphore
  * Max value some positive number
  * Locked on 0 for any semaphore.

Classical Sync problems :
  * Bounded-Buffer Problem
    * We introduced it last time, but is when we have a shared bounded buffer and need to manage a producer/consumer.
    * Use counting semaphores to keep track of empty full buffers.
    * Initialize with :
      * int n;
      * semaphore mutex = 1;
      * semaphore empty = n;
      * semaphore full = 0;
  * Readers-Writers Problem
    * Suppose you have a shared database/file among several processes
    * Some processes may only want to read
    * Others may want to update (read & write)
    * Initialize with : 
      * 
  * Dining-Philosophers Problem
