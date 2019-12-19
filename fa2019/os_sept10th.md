  Processes and Process memory, need an API, something to destroy/manage processes :
  command fork() that creates copy of memory stack (the processes have the same process counter)
  It copies only on the case that you write (It's faster not to copy)
  fork returns (0) to the child process, and the child ID to the parent.

  if (fork() == 0){
  }
  else{
  }

  Process fork : 




               __________C1 = 2___________ Returns 0
              |
              |
            c | 1
              |
              |
  x()_________|______C0 = x()_____________  Returns the Child ID



  Difference process_

  void fork2(){
    printf("L0\n");
    fork();
    printf("L1\n");
    fork();
    printf("Byte\n");
}

    Process --> fork (P0 and P1)
      P0 ----> FORK (P0, P2)
      P1 ----> FORK (P1, P3)
      POSSIBLE :   L0 (0-2 TIMES)
                   L1 (0-2 TIMES)
                   P0 ---> BYE 
                   P1 ---> BYE
                   P2 ---> BYE
                   P3 ---> BYE


L0L1BBL1BBB


  void fork2(){
    printf("L0\n");
    fork();
    printf("L1\n");
    fork();
    printf("L2\n");
    fork();
    printf("Byte\n");
    }

Start at the beginning, mark where you fork, don't go backwards.

  void fork2(){
    printf("L0\n");
    if (fork() == 0){
      printf("L1\n");
      if (fork() == 0){
        printf("L2\n");
        fork();
      }
    }
    printf("Byte\n");
  }

  Output : L0->(L1 or Bye)->(L2 or Bye)->(Whatever wasn't finished in prevoius processes)->Bye->Bye
  if (!fork()); means it nots anything but zero, same as if (fork() == 0)

  new functions :

  void ext(int status)
    exits a process, normally returns with a status 0
  void atexit void ((*func) (void))
    registers functions to be executed upon exit
    takes a function pointer that takes a void and a void
    threading library function casting
    register the function you pass it to run before the overall process exits.
    clean up or logging functional.

    void cleanup(void) {
      printf(cleaning up\n"};
    }
    void fork6() {
      atexit(cleanup);
      fork();
      exit(0);
    }

    fork -> exit() (cleaning up) -> exit() (cleaning up)


    exceptional control flow :
      * mechanisms for exceptional control flow exists at all levels of a computer
    low level mechanism
      * exceptions/interrupts
        - change in control flow in response to a system event (change of system state)
      * Combination of hardware and OS software

    high level mechanisms
      * Process context switch
      * Signals
      * non local jumps (setjmp/longjmp), try/except blocks
      * Implemented by either :
        - OS software context switch and signals
          ^ These kind of things will be using for our first assignment
          ^ C language runtime library nonlocal jumps.
      OS will send a signal to a parent process when a child is terminated
      
      Exceptions : a transfer of control to the OS in response to some event.


      Interrupt Vetors : An index of exceptions : Each type of event has a unique event number K
                         Index into ump table (aka interrupt vector)
                         Jump table entry k points to a function
                         Handler K is called each time exception k occurs.

      Asynchronous Exceptions (Interrupts)
      Caused by events external to the processor
        * Indicated by setting the processor's interrupt pin
        * handler returns to "next" instructions
      Examples :
        * I/O interrupts
          - hitting ctl-c at the keyboard
          - arrival of a packet from a network
          - arrival of a data sector from a disk

      Synchronus Exceptions :
        * Traps :
          - Intentional, Example : System calls, breakpoint traps, special instructions, control to next
        * Faults :
          - Unintentional but possibly recoverable. Seg faults, page faults, protection faults, 

        * Aborts : 
            - Unintentional and unrecoverable
            - parity error, machine check, aborts current program

        Trap example : User calls open(filename, options)
        OS mus tfind or create a file, get it ready for reading/writing
        returns integer file descriptor
