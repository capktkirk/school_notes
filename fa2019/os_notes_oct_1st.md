How do programs see memory?

By the end of the week talking about virtual memory:

Fourth Assignment : Decisions about evicting from physical memory.

Memory is rather simple/flat.
  * What is wrong with this?
  * With no abstraction how do we run more than one process?
  * Where do the parts of the program live?

Most memory is on the disk and gets loaded into RAM

[How](How) do we give each process it's own memory space?
  * Old way : Base register + limit
  * This gave us a narrow window to work with (you shouldn't
    be able to write beyond it, but you can.)
  * written specialized hardware to keep you from over-writing data.

  * Further abstraction:
    * Virtual Memory (every system does this essentially)
    * We will discuss Virtual Memory later.

  * 32 Bit addressing

    * Linux user/kernel memory split (3 Gigs User Mode Space, Kernel Space 1gig)
    * Windows, default memory split (kernel space 2gb, user mode space 2gb)
    * Windows booted with /3gb switch (1gb kernel space, 3 gb user mode space only
      applies to exe's flagged with large-address aware)

    Why is OxFFFFFFFF your largest value? It's all 1's.
    How about on 64? More F's.

  * Where do parts of the program live in memory?
    * Is that 4GB for one program or all programs?
    * Where does each program live?
      * What are the parts of the program that live in memory?
        * stack
        * heap
        * .txt (program code)
        * .data (predefined variables)
 | ======================  |
 | Kernel Space (1 gig)    |
 |                         |
 | Stack (grows down)      |
 |                         |
 | Memory mapping segment  |
 | (file mappings,         |
 | dynamic libraries)      |
 |                         |
 | ----------------------- |
 | Heap ^                  |
 | ----------------------- |
 | BSS Segment             |
 |                         |
 | ----------------------- |
 | Data Segment            |
 |                         |
 | ----------------------- |
 | Text Segment            |
 | ======================  |


About Linux Memory Mappings :

  Don't use gets();

  * Why does the stack grow down and the heap grow up?
  - You could limit the stack size by the program + heap
  * Why is there random space allocated in the memory image?
    * Let's talk about the security implications of this.
  -
  * Is there anything else strange?
  -
  * What happens if we try to access some section that isn't allocated?
  -


How do we resolve these issues?

* Virtual memory?
  * Thoughts on virtual memory?
  * What are potential benefits? :
    * Use physical DRAM as cache for disk. (Caching commonly used items.)
    * This provides us the ability to have reasonable fast memory process access.
    * Address space for process of a process can exceed physical memory size.
    * Sum of address spaces of multiple process can exceed physical memory.
  * Simplify Memory Management :
    * Multiple processes resident in memory with unique address space.
    * Only "active" code and data in actual physical memory.
    * Allocate more memory to process as needed.
  * Virtual Memory Goodness :
    * Provide memory protection.
    * Prevent process interference.
    * Privileges

* Old Virtual Memory :
  * Pointer table (point to start of regions of memory)
  * Keep track of block sizes
  * Difficult to share libraries between processes.
  * Requires contiguous allocation
  * No protection for "wild writes", nothing keeping you in your block.
* New Virtual Memory :
  * Separate Virtual Address Spaces.
  * All the same size.
  * Blocks are called pages.
  * Each process has it's own virtual address space.
  * Operating system controls how virtual pages are assigned to physical memory.
  * Virtual "Page Table" to find the physical address (A look up table.)
  * We can have shared libraries.


Once we hit a pagefault, we need to "Evict" a process from the physical memory to
load the new one. Once it pagefaults, it'll fix the memory, and restart at the instruction
that it failed on.

What is locality?
  * A process has a page in memory that is usable multiple times.
  * Different Kinds :
    * Spatial Locality (something you recently used is adjacent to something you need next)
    * Temporal Locality (something you've recently accessed is likely to be used again)

At any given point in time, programs tend to access a set of active virtual pages called the _working set_

if (working set size < main memory size)
  * good performance for one process after compulsory misses.

if (SUM(working set sizes) > main memory size )
  * Thrashing : performance meltdown where pages are swapped in and out continously.

Motivation #3 : Protection
Page table entry contains access rights information
Hardware enforces this protection (trap into OS if violation occurs)

VM Address Translation

n-1 virtual page number
p-1 page offset

n-1 translates to m-1 for physical page address.

Large page tables allocated per process :
  4kb (2^12) page size
  32 bit address space
  4 byte page table entry
  2^20 * 4B = 4MB page table per

Performance benefit of cache is lost.

Solutions :

  Common solution :
    multi-level page tables
    e.g 2-level tables (P6)
      Level 1 table : 1024 entries
      each of which points to a level 2 page table
      Level 2 table : 1024 entries
      each of which points to a virtual memory address to a physical memory address.


  translating with a k-level page table
  1,2,3...,k tables.

  

