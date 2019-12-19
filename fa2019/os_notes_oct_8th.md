###Dynamic Memory Allocation:

Prefetch, pre-evict mechanism for paging.

malloc/free (Use system call.)

Memory is not unbounded
* It must be allocated and managed
* Many aplications are memory dominated
  * Especially those based on complex, graph algorithms.

* Memory referencing bugs especially pernicious.
  * memory performance is not uniform.
  * Cache and virtual memory can greatly affect a programs running speed.

Dynamic Memory Allocation : Explicit vs Implicit
  * malloc and free in C
  * Implicit : application allocates but does not free space
  * E.g. garbage collection ni Java, ML or Lisp

Allocation in both cases memory allocator provides an abstraction of memory as a set of blocks.
Doles out free memory.

new and delete are C++ wrappers.

Dynamic Memory Allocation : Application : Dynamic Memory Allocator : Heap Memory.


Allocators request additional heap memory from the operating system using the sbrk function

kernel virtual memory
stack 



###Malloc


Malloc package void *malloc(size_t size)
returns a pointer to a memory space of that size.

realloc will resize a block. realloc(void *p, size_t size) where p is a pointer

Assumptions:
Assumptions made in this lecture :
  * Memory is a word addressed (each word can hold a pointer);

Must Align blocks so all alignment requirements are satisfied.

iideally constant time for malloc/free

If the heap makes good use of locality, everything else is better.

To understand the length of memory :

There will be a header attached to the memory.  

Standard method : Keep the length of a block in the word preceding the block. This word is often called the header-field or header
Requires an extra word for each block.

flip the least significant bit to declare if it is allocated. The 8 bits before the memory declares the size.


implicit list
explicit list : Among the free blocks using pointers within the freeblocks.
segregated free list

Method 4 : Blocks sorted by size.

Method 1 : Implicit list
  * Need to identify whether each block is free or alocated
    * Can use extra bit.

First Fit : Iterate through the heap and find the first open block of correct size.
Best Fit : Go through the list, and find the closest possible list. Always O(n)

coelesce/join : with next and/or previous block if they are free.

Doubly-linked list style :

Header & Footer (go both directions) this is called Boundary Tags.


        | 1 word  |   |
hdr     | size    | a |
        | payload |   |
        | padding |   |
ftr     | size    |   |

Knuth : Father of analysis of algorithms, The Art of Computer Programming, creator of TeX/LaTeX


