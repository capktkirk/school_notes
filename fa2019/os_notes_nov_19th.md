Jump into IPC :

Interprocess Communication 

What have we discussed so far?
One way for processes to talk to each other, Signals.

* Exception Control Flow
* Signals
* "It happened, do a thing"

Can we send signals for user defined purposes?
  * Yes
    * SIG_USR1, SIGUSR2

How do we send something more than a signal?
* Inter-process communication (IPC)
  * Shared Memory
  * Message Passing
    * Naming
    * Synchronization
    * Buffering
  * Sockets
    * Method of interprocessing communication stolen by networks.
  * Pipes
    * Named pipes
  * Why do we care about interprocess communication?
    * We can get more work done, information sharing, computation speedup, modularity, convenience.

Thoughts on how shared memory IPC works?

System calls to establish regoin of shared memory
 * Kind of like a specialized malloc so more than one process can share the memory
 * From this point all access are like any othe rmemory action.

After doing a shared value, it acts exactly like a normal memory thing.
This makes writing code simpler.

Drawbacks : Now we have race conditions.

Conditional Variables on the bounded buffer.


struct Stoof {
  char buf[max][sbufsize];
  int count;
  pthread_mutex_t block; //bounded lock
  pthread_mutex_t flock; //file lock
  cv fill;
  cv empty;
  File* of;
}


We need to initialize mutex attributes :

passing in unique attributes into mutex


