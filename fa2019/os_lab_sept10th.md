waitfg will be three lines, 17 lines of comments.

tsh.c is the only file to turn in.

goal is to learn to fork, deal with signals, terminating processes

Sixteen trace files, 16 tests. Shell driver written in perl came with the lab.

// command
// make test01 ./sdriver.pl -t trace01.txt -s ./tsh -a "-p"

---tshref is a fully functional version of the code.
---the test files bulid on each other.

* one signal handler if you do it wrong you will fuck yourself.

---helper functions : 

---already written : 
parseline : cmdline in eval already done. Returns a true or false, whether it should be background or foreground. 
foreground is just a waitloop until the user gets the prompt back.
an & means it is a background shell. Print out the process id, job id and the user input.

* jobs, fg, bg are built in shell functions. fg or bg will move a stopped process into either bg or fg to resume. 

#include<signal.h>
#include<sys/types.h>
#include<sys/wait.h>

Only includes to be used.

* Helper library signal.h is a helper function for signals for the rest of the semester.

* Parse gives you the argv, and helps process the data. Argv for your new process. 
//Keeping track of processes currently running info
//#define UNDEF 0	/*undefined*/
//#define FG 1		/*foreground*/
//#define BG 2
//#define ST 3

struct job_t{
	pid_t pid;
	int jid;
	int state;
	char cmdline[MAXLINE];
};
extern struct job_t jobs[MAXJOBS];

You can reference jobs

array to keep track of jobs

--helper functions :
	--clearjob(zero out a job), initjobs(make jobs 0), maxjid(returns maximum job id), 
	  addjob(creates a new job to the list), deletejob(deletes a job from the list), 
	  fgpid (the pid in foreground), *getjobpid(get a pointer to a job via process id), 
	  *getjobjid(get a pointer to a job via job id), pid2jid(take a pid and turn it to a jid),
	  listjobs(list all jobs)

--make tests will run every single trace.

never evoke a SIG, it should only run when a signal is recieved.

ctl-z, ctl-c
