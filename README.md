#include<stdio.h>
#include<sys/wait.h>
#include<stdlib.h>

int main(void)
{
pid_t pid1;
pid1=fork();
if(pid1==0)
{
sleep(5);
printf("I am child with delay pid=%d\n",getpid());
execl("/bin/ls","ls",NULL);
}
else{
int pid2;
printf("i am parent pid =%d\n",getppid());
pid2=wait(0);
printf("patrent saying..child %d exited/terminated normally\n",pid2);
printf("%d\n",getpid());
exit(0);
}
}
