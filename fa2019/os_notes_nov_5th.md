Midterm Overview :

Question 4 :

int pid = 0;
void sigchild (int s)
{
  if (pid) kill ( pid, SIGHUP );
}

void sighup (int s)
{
  if (pid kill ( pid, SIGHUP );
}

main() {
  int status;
  signal (SIGCHLD, sigchld);
  signal(SIGHUP, sighup);
  int i;
  for(i = 0; i <= 2; i++){
    if ((pid = fork()) == 0){
      KILL( getppid(), SIGHUP );
      exit(0);
    }
  }
  wait(&status);
}


