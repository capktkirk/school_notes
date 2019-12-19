Dining-Philosophers Problem

* Consider 5 Philosophers
* They spend their lives thinking and eating
* They need two chopsticks to eat and don't release the chopsticks until they finished eating.

Five Chopsticks between Five Philosophers : 
  One left chopstick one right chopstick.

  Semaphore Solution:
    process P[i]
    while true do
    {
      THINK;
      PICKUP(CHOPSTICK[i], CHOPSTICK[i+1 mod 5]);
      EAT;
      PUTDOWN(CHOPSTICK[i], CHOPSTICK[i+1 mod 5]);
    }

TRYLOCK

This is known as Deadlock
* Deadlock occurs when there is no way for progress to be made as locks are held but not released.
* We'll discuss this further in two weeks.
* Key point : We don't want deadlock.

Only allow 4 of the 5 to be eating at the table.
Allow a philosopher to pick up her chopsticks only if both chopsticks are available.
* To do this, she must pick them up in a critical section.
* Lock them all out of chopsticks and only
* Use an asymetric solution
  * Number each philosopher (even and odds) that pick up left/right chopsticks.

  ###POSIX Mutex
  #include <pthread.h>
  pthread_mutex_t mutex
  /* Create the mutex lock : NULL is the attribute for setting up the Mutex */
  pthread_mutex_init(&mutex,NULL);
  /* aquire the mutex lock */
  pthread_mutex_lock(&mutex);
  
  /* critical section */
  /* unlock the lock */
  pthread_mutex_unlock(&mutex);
  
  
  destroy, trylock (get rid of the mutex when you are finished with it and check to see if the lock is in use.)

  posix semaphore assignment 6 (allowed to include semaphore.h)
  sem_t sem; /* the type */
  sem_init(&sem, 0, 1);
  sem_wait(&sem);
  /* Critical Section */
  sem_post(&sem);


###Conditional Variables:
Assignment 6 : You can use Conditional Variables for extra credit on assignment 5. You have to on Ass5

conditional variable (cv)

cv [ ] -> (p1)

You can use a conditional variable to queue up a bunch of processes that need to run when the conditional variable changes.

Ready Queue -> Run
with Conditional Variable waiting :


Monitor :
* Abstract Data Type (ADT)
* Encapsulates data with a set of functions to manipulate it.
* Synchronization happens inside the ADT
* Goal is to provide thread safe methods to access data.

Write own data-type with arrays (autovectorization flag)

monitor DiningPihlosophers {
enum{THINKING, HUNGRY, EATING}
state[5];
condition self[5];
void pickup(int i){
  state[i] = HUNGRY; test(i);
  if (state[i] != EATING)
    self[i].wait();
}
void putdown (int i){
  state[i] = THINKING;
  test((i + 4) % 5);
  test((i + 1) % 5);
}

void test(int i) {
  if((state[(i+4) %5] != EATING) && (state[i] == HUNGRY) && (state[(i+1) % 5) != EATING)){
    state[i] = EATING;
    self[i].signal();
  }
}

initialization code() {
  for (int i = 0; i < 5; i++){
    state[i] = THINKING;
  }
}


This allows you to use
DiningPhilosophers.pickup(i);
...eat...
DiningPhilosophers.putdown(i);


What is a monitor : It is an abstract data type representing a shared resource.
  * Semaphores can be used to _control access_ to a shared resource;
  * monitors _encapsulate_ the shared resource;
  * A monitor implements a shared data structure together with the (coarse-grained atomic) operations which manipulate the data structure.

In Java :

#Java Monitor :
  * Every object has a single lock with it.
  * When a method is declared to be synchronized ownership of the lock is required to call the method

Make shared anonymous with parent/child is the way to go (code example in class????)

Code Examples for Conditional Variables :

Conditional Variables :

Alternative Approaches :
  * Transactional Memory
    Came from database theory : 
      A *memory transaction* is a sequence of memory read-write operations that are atomic.
      If all are completed the result is committed to memory. (otherwise it's rolled back)
      The transactional memory ystem, not the developer, is responsible for guaranteeing atomicity.
      Database Theory of aquire/release.
  * OpenMP
    Similar to the compiler directive for parallelism
    #pragma omp critical
      Signifies a block of code is a critical section, the openMP sets up the lock.
      Single lock for the whole code area.
  * Functional Languages.
    Different than normal paradigms.
    Scala, Erlang, Haskell.
    Functional languages do not maintain state
      Once a variable has been defined, it's immutable.
    

