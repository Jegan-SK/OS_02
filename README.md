# Linux-Process-API-fork-wait-exec-
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:

## C Program to create new process using Linux API system calls fork() and getpid() , getppid() and to print process ID and parent Process ID using Linux API system calls

```
#include <stdio.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <stdlib.h>

int main()
{
    pid_t pid;

    pid = fork();

    if (pid < 0)
    {
        printf("Fork failed!\n");
        return 1;
    }
    else if (pid == 0)
    {
        printf("\nChild Process\n");
        printf("Process ID: %d\n", getpid());
        printf("Parent Process ID: %d\n", getppid());
    }
    else
    {
        printf("\nParent Process\n");
        printf("Process ID: %d\n", getpid());
        printf("Child Process ID: %d\n", pid);

        wait(NULL);
    }

    return 0;
}
```
##OUTPUT


<img width="691" height="272" alt="image" src="https://github.com/user-attachments/assets/9bf08a9a-9df0-4647-a504-b10d4b8b2704" />







## C Program to execute Linux system commands using Linux API system calls exec() , exit() , wait() family

```
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/types.h>
#include <sys/wait.h>

int main()
{
    pid_t pid;
    int status;

    pid = fork();

    if (pid < 0)
    {
        printf("Fork failed!\n");
        exit(1);
    }
    else if (pid == 0)
    {
        printf("Child Process: Executing Linux commands\n");
        execlp("ls", "ls", "-l", NULL);

        perror("exec failed");
        exit(1);
    }
    else
    {
        wait(&status);
        printf("\nParent Process: Child process completed.\n");
    }

    return 0;
}
```
##OUTPUT

<img width="672" height="385" alt="image" src="https://github.com/user-attachments/assets/488a1fcb-3fd8-4e23-b246-0e01fe270596" />






# RESULT:
The programs are executed successfully.
