=------------- LAB ------------=

Carnegie Mellon Code Examples (ECF)

sigchild handler : Basically does what ours should do to start out with.

trace 3 with foreground job : add to it what I need.

sigchild lead the job.

eval : first function to implement.
  quit should be handled with built in command. (exit(0))
  if not a builtin command fork out a child to execv
  background jobs should not ignore SIGINT or SIGTSTP
  if you make them ignore SIG_IGN they will persist to ignore signals no matter what.
  execv child.

  deletejob in shell.c is similar to what we want to do.

  add the jobs to joblist, added as foreground, we wait. while foreground pid == jobslist pid we wait.
  deletejob needs some error handling.
  race condition : Need to add before delete.
  * shell -> fork() ---|__________
                       |
                       |___________
  procmask() on Tuesday

  sigstp_handler doesn't do anything but send a signal out to the foreground job
  sigint_handler doesn't do anything but send a signal out to the foreground job.
  They can be identical.
  send signal to fgpid
  fgpid in the jobs library will get you the foreground job (0 if it doesn't exist)
  don't signal 0
  
  block all signals right before forking (only if you are about to fork) so call before
  forking.

  block signals only on not builtincommand

  
  right before you fork :
  sigemptyset(&mask);
  sigaddset(&mask, SIGCHILD);
  sigprocmask(SIG_BLOCK, &mask, NULL);
  /* Something like this */



  demo purposes : 
  procmask.c


  #include "csapp.h"
  void handler(int sig)
  {
    pid_t pid;
    int status
    while (pid_
 
