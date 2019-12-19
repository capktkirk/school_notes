Conditional Variables :

A conditional variable put it in a variable.
[CV] -> P1

Current Assignment :

Busy Waiting

GetLock()
while(full){
  Unlock()
  Sleep()
  GetLock()
}

Not Busy Waiting 
[CV]->P1 
Goes to sleep until a change happens, then acts.

* Syncrhonization tool that can :
  * Unlock itself if a condition isn't met
  * Block until woken up
  * relock itself and check for the condition being met upon waking.

* Monitor : Abstract Data Type
  * Abstract Data Type (ADT)
  * Encapsulates data with a set of cuntions to manipulate it
  * Snynchronization happens inside the ADT
  * Goal is to provide thread safe methods to access data.

Vector is an abstract data type.

Java Monitor :
  * Every object has associated with it a single lock
  * When a method is declared to be synchronized ownership of the lock is required to call the method.
  * Slap synchronized on it and it works.

Implementation of Dining Philosopher.

POSIX Conditional variables
  int pthread_cond_init(pthread_cond_t *cond, const pthread_condattr_t *attr)
  etc,etc,etc
  pthread commands :
  pthread_cond_destroy
  pthread_cond_wait
  pthread_cond_signal
  pthread_cond_broadcast



producer (get the stuff and put it in the bounded buffer)
consumer (print or act on the stuff in the bounded buffer)

char hostname[SBUFSIZE]

Can use dynamic memory, or not. Both are acceptable.

Code Example :
One Producer/One Consumer, No check for if someone already consumed it.


Guildeline : Use a while (not if)
That will make it so that no code will try to reap if data is empty.

Bad : Using the same conditional variable for both (for bad2 example)

Two conditionals

cond_t empty, fill;
mutex_t mutex;


C11 CV Example
* template <class Predicate >
* void wait(std::unique_lock<std::mutex>& lock, Predicate pred);
* predicate which returns false if the waiting should be continued. The signature of the predicate function should be equivelant to the following bool period();

Go : 

channel allows you to do multithreading in Go
var done = make(chan bool)
var msgs = make(chan int)

BLocking by design


