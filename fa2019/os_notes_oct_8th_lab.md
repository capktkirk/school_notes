Virtual paging assignment

simulation of paging

20 virutal pages (MAXPROCPAGES)
100 physicl pages (PHYSICALPAGES)
20 simultaneous processes (MAXPROCESSES)
128 memory unit page size (PAGESIZE)
100 tick delay to swap a page in or out(PAGEWAIT)

100 ticks to get something in and 100 ticks to get something out.

./test-basic
ctrl c dumps out data (the state of all of the pages of all of the processes)

Random Strategy might get you a good grade if you can't do something.

third file : "working" pager. A good example to see how it works.

all start as zero

long active : (0 inactive, 1 active)
long pc (value of the program counter for the process. Current page can be calculated as page = PC/PAGESIZE)
long npages (number of pages in the process memory space, 0 if inactive, 20 if active)
long pages([MAXPROCPAGES] a bitmap array representing the page map for a given process. If pages[X] is 0, page X is swapped out, swapping out or swapping in, if pages[X] is 1, page x is curretly swapped in.

Make sure if you're paging anything out, that it is in memory.

Key thing : look at memory : pageout(), wait 99 ticks, pagein() something. The memory will not be open until 99 ticks later.

math of pc/PAGESIZE will matter.

Data Needed :

When it was used

static variables :

initialized, tick, timestamps

timestamps is a twodimensional array you can find the least recently used (timestamps[proctmp\][pagetmp\]



0 - 127 128 - 256 -> ##
for 10 30
run 10 to 30 times.

run 500, run 500 contiguous instructions.
run 900
== 1400
(40% chance to go back to 500, 60% chance to run 131)

Now : 0
Next : 1
(We know we won't need anything else)

if we're at 0 (pageout everything but 0 and 1)


