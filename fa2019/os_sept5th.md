Processes :

  Kernel Hacking Write Up : Due Sept 8th (3 days)
  Git to turn in assignment : 

  How do we provide the illusion of multiple CPU's : 
    * Run them one at a time really fast (background and foreground.)
    * Context Switching : Swap what is "currently" running and where it is running.
    * Edgecases because of context switching where the program might not work.
    * Logical Control Flow :

        Time  Process A   Process B    Process C
        |........|................................
        |.....................|...................
        |..................................|......
        |........|................................
        |.....................|...................

    * Concurrent : When they overlap in time (processes that are running at the same time
      but not active.
    * Sequential : When they run back to back, not at the same time.
    //Exam : There will be discussions on WHY to do things, not the definition of things.
    * How do we preserve a process State : 
      ^ Save stuff to registers to keep it.
    * Everything in the process will go through a Process Control Block somewhere (RAM, Disk, "Memory" etc)
      ^ Process State - Running, waiting, etc, this is the data structure for scheduling.
      ^ Program Counter, CPU registers, memory management, I/O, etc.
    * Interrupting must handled.
    * Process API (abstract generally)
      ^ Create
      ^ Destroy
      ^ Wait
      ^ Status
      ^ Misc Control
    * What does a process memory image look like?
      ^ Registers
    * Fork : 
      ^ int fork(void)
      ^ creates a new process(child process) that is identical to the calling process(parent process)
      ^ returns 0 to child process
      ^ returns child's pid to the parent process
        # if (fork() == 0){
            printf("hello from child\n");
          }
          else {
            printf("hello from parent\n");
          }
      ^ With diagrams to see it splitting.


