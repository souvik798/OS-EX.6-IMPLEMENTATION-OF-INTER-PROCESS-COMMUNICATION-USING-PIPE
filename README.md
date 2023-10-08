OS-EX.6-IMPLEMENTATION-OF-INTER-PROCESS-COMMUNICATION-USING-PIPE
AIM:

To implement the interprocess communication using the pipe command.

ALGORITHM:

create a child process using the fork().

Create a simple pipe with C, we make use of the pipe() system call.

Create two file descriptor fd[0] is set up for reading, fd[1] is set up for writing

Close the read end of parent process using close() and perform write operation

Close the write end of child process and perform reading

Display the text.

PROGRAM:

#include<stdio.h>
int main()
{
  int fd[2], child ;
  char a[10];
  printf("\n Enter the string : ");
  scanf("%s",a);
  pipe(fd);
  child = fork();
  if(!child)
  {
    close(fd[0]);
    write(fd[1],a,5);
    wait(0);
  }

  else

  {
     close(fd[1]);
     read(fd[0],a,5);
     printf("The string received from pipe is : %s ",a);
  }

  return 0;
  }
OUTPUT:

image
RESULT:

Thus the implementation of interprocess communication using pipe command is successfully executed.

