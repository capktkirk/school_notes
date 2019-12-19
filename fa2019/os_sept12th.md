Zombies :
Idea
* When process terminates, still consumes system resources
  - Various tables maintained by OS
* Called a "Zombie"
  - Living corpse, half alive and half dead

Reaping
* Performed by parent on terminated child
* Parent is given exit status information
* Kernel discards process

Parents have to reap the children.

What if parents don't reap?

* If any parent terminates without reaping a child, then child will be reaped by init process
* Only need explicit reaping for long-running processes
  - E.g., shells and servers

wait : Synchronizing with children
  int wait(int *child_status)
    ^ suspends current process until one of its children terminates
    ^ return value is the pid of the child process rhat terminated if child_status != NULL, then the object 
      it points to will be set to a status indicating why the child process terminated

  You can parse out pieces of the integer returned to get information based on the termination process
    ^ This is how you'll handle it for the shell assignment.
    ^ Another function will be more useful.

Example : 

  void fork9() {
    int child_status;
    if (fork() == 0){
      printf("HC : hello from the child\n");
    }
    else{
      printf("HP : hello from the parent\n");
      wait(&child_status);
      printf("CT : child has terminated\n");
    }
  printf("Bye\n");
  exit();
  }

Example 2 :

/////

Shell assignment, don't care about order, just that all children get reaped.

waitpid() method is more useful.

waitpid(pid, &status, options)
  * can wait for specific process
  * various options
    VALUES OF PID : 
    ** < -1 : meaning wait for any child process whose process group ID is equal to the absolute value of pid
    **   -1 : meaning wait for any child process
    **    0 : meaning wait for any child process whose process group ID is equal to that of the calling process
    ** >  0 : meaning wait for the child whose process ID is equal to the value of pid
    VALUES OF OPTIONS :
    ** WNOHANG
    ** WUNTRACED
    ** WCONTINUED
    ** WIFEXITED
    **
  We will be using waitpid for any child.

Shells and Signals   :

Fork
Exit
Wait

Above are system calls.

How to execute a new program :
We want the child to run a different program.

function execl

int execl(char *path, char *arg0, char *arg1 ....., 0)
  *loads and runs executable at path with args
    ** path is the complete path of the executable
    ** arg- becomes the name of the process
execv is better mayble. You can use argv[0]

When someone types in ls, it'll go to fork() and run execv(/bin/ls) or whatever argument.

all shells

int main(){
  char cmdline[MAXLINE];
  while (1) {
    printf("> ");
    Fgets(cmdline, MAXLINE, stdin);/* READ IN LINE */
    if (feof(stdin))
      exit(0);
    eval(cmdline); /* EVAL LINE */
}

Simple Shell example takes care of foreground, but not background.

  Will become zombies when they terminate
  will never be reaped
  creates a memory leak that will eventually crash the kernel


Solution : Use a signal

sigchld_handler : Catches SIGCHILD signals

signals are in a vector

SIGINT, SIGKILL, SIGSEGV, SIGALRM, SIGCHILD are all signals in that vector. We will create a function that handles a function when the signal is sent.

Sending a Signal : 
  * Kernel sends signal to a destination process by updating some state in the context of the destination process.
  * Kernel sends a signal for one of the following reasons : 
    ~ Kernel has detected a system event such as divide-by-zero (SIGFPE) or the termination of a 
      child process (Sigchild)
    ~ Another process has invoked the kill system call to explicityl request the kernel to send a 
      signal to the destination process.

  There is only one bit that is flipped so we need to have a handler that kills all the children since it will only signal if one has died (when there could be 30)

  Tripping Point : Process calling KILL doesn't necessarily mean the process dies.

  * A destination process receives a signal when it is forced by the kernel to react in some way to the delivery of the signal.
  * Three Possible Ways to React :
    ~ Ignore
    ~ Terminate
    ~ Catch the signal by executing a user-level function called a signal handler.
      Akin to a hardware exception handler being called in response to asynchronous interrupt.

A signal is pending if it has been sent but not yet received.
  * There can be at most one pending signal fo any particular type.
  * Important: Signals are not queued.
    ~ If a process has a pending signal type of k, then subsequent signals of type k
      that are sent to that process are discarded.
  * A process can block th ereceipt of certain signals.
    ~ Blocked signals can be delivered, but will not be recieved until the signal is unblocked.
  
