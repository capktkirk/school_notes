Final Practice Exam :

Put name

1) Dynamic Storage Allocation :
  The following problem concerns dynamic storage allocation
  Consider an allocator that uses an implicit free list. The layout of each allocated free memory block is as follows :
Header and footer, 32 bytes :

        31                      2 1 0
Header  | Block Size (bytes)    |   |


Footer  | BLock Size (bytes)    |   |

Each memory block, either allocated or free, has a size that is a multiple of eight bytes.

bit 0 - indicates the use of current block 1 for allocated 0 for free
bit 1 - indicates the use of the previous adjacent block: 1 for allocated, 0 for free
bit 2 - is unused and is always set to be 0.

Next Page : Block of memory that is large enough to be usable, small enough to fit on a piece of paper.

Free(0x400b010)
Steps to Solve :
  Find address
  it is n/a n/a
  free instruction call gets back the usable address in the pointer.
  Go to the preceding word to find the header (since the heap grows up)
  It is 16 blocks, it is currently allocated, and it is telling us the previous block is allocated. (011)
  Change the info on the block to representing it's allocation.


  Previous block is allocated
  Answer for 1 :

  32 010
  n/a n/a
  n/a n/a
  32 010
  16 011
  16 011


Question 2 :
  Question:
  pthread_mutex_t lock;
  (blank) threadfunction( (blank) pointer)
  { 
    ...
    (blank)
    //critical section
    (blank)
    ...
  }
  
// Question in class :
  There will be a few more blanks to fill in on this in the final.
  pthread_create(thread, void*(void*), *options);
//

  Answer :
  pthread_mutex_t lock;
  *void threadfunction(*void pointer)
  {
    ...
    pthread_mutex_lock(&lock);
    //critical section
    pthread_mutex_unlock(&lock);
    ...
  }


Question 3 (a):
//Variation on this, maybe additional tables, or other algorithims.
//What has screwed up previous students : LRU-K Least Recently Used - K (known) K is a variable for a number
//LRU-2 (second)

Timestamp on this question is related to the pager assignment, higher timestamp means a newer entry.

Find the oldest timestamp ( 9 - 6 ), evict it and replace it.

8   38
10  10
5   17
45  4
3   24
7   48
13  62
1   19
2   7

//The final will have an LRU-#, you will evict the number from the oldest, LRU-2 would evict 2 - 7 here, 
//LRU-3 would evict 10 - 10, etc.

Question 3 b) :
//Paging Requests : 12, 14, 16, 19, 13, 1, 10, 2, 6, 3

Acceptable Answer could be : Page out anything that's not on the list for this example, or specifically list out which ones and why. (Page out the numbers that do not come after the current page in.)

My Answer : Page out 5, 6, 7, 8, 9 because they are not potentially being used from the page. The rest will be used at some point in the paging requests.


Question 4 : What is an inode : A data structure on a filesystem on Linux and other Unix like operating systems.

//These won't be on the exam, but it will be a few definitions, so go over the definitions from class.
//Something about inodes, or other data structures mentioned in class.
// soft link == symbolic link. Nothing will be on symbol links or soft links.

Question 5 :
  Look for Cycles
  Solid Line is the request is being made : Locked the process.
  Dashed Line : Not locked
  a) Safe
  //B Look to see if the cycle is going to stay regardless of the other side of the diagram.
  b) Deadlock
  c) Unsafe

Question 6 :
  //First step is almost guaranteed to be safe.
  a)
  i.    Safe
  ii.   Safe
  iii.  Safe
  iv.   unsafe
  v.    unsafe

//Draw the arrows of the requests to see how it is acting and where the requests go.

  b)
  i.      Safe
  ii.     Safe
  iii.    Safe
  iv.     Unsafe
  v.      Unsafe
  vi.     Unsafe
  vii.    Unsafe
  viii.   Deadlock

//Go step by step, see the state
//It would only go back to a dotted line if something is "released"
//

Question "4" : Duplicate 4.
//This is a guess, he's covering semaphores next time.
a) No, there is a sem_wait(&s); and it holds until the thread is given it.

b) Yes, there is no sem_wait to keep the race condition from happening.

//Look up the way semaphores are handled, similar to pthreads.

Dec 12th continuation :

Last Question :
No semaphores on final.

a) It prevents a thread from dereferencing it, but not the way to increment in the loop.

b) Semaphore waits for something to post, the thread is created and it waits. It doesn't process the loop until there is an available semaphore.


