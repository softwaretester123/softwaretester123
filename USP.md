# P3
```

#define _POSIX_SOURCE
#define _POSIX_C_SOURCE 199309 L
#include <stdio.h>
#include <unistd.h>

int main()
{
  int res;
  if ((res = sysconf(_SC_CLK_TCK)) == -1) perror("sysconf");
  else printf("Number of clock ticks: %d\n", res);
  if ((res = sysconf(_SC_CHILD_MAX)) == -1) perror("sysconf");
  else printf("Max. Number of child processes: %d\n", (res));
  if ((res = pathconf("/", _PC_PATH_MAX)) == -1) perror("pathconf");
  else printf("Max path length: %d\n", res);
  if ((res = pathconf("/", _PC_NAME_MAX)) == -1) perror("pathconf");
  else printf("Max number of characters in file name: %d\n", res);
  if ((res = sysconf(_SC_OPEN_MAX)) == -1) perror("sysconf");
  else printf("Max number of open files/processes: %d\n", res);
  return 0;
}
}
```
# P4
### Writer
```
#include <stdio.h>
#include <fcntl.h>
#include <sys/stat.h>
#include <unistd.h>
#include <sys/types.h>

int main()
{
  int fd;
  char buf[1024];
  char *myfifo = "/tmp/myfifo";
  mkfifo(myfifo, 0666); /*create the FIFO (named pipe) */
  printf("Writer Process started:\n Run Reader process to read the FIFO File\n");
  fd = open(myfifo, O_WRONLY);
  write(fd, "USP-CSE", sizeof("USP-CSE")); /*write "USP-CSE" to the FIFO */
  close(fd);
  unlink(myfifo); /*remove the FIFO */
  return 0;
}
```
###Reader
```
#include <stdio.h>
#include <fcntl.h>
#include <sys/stat.h>
#include <unistd.h>
#include <sys/types.h>
#define MAX_BUF 1024
int main()
{
  int fd;
  char *myfifo = "/tmp/myfifo"; /*A temp FIFO file is not created in reader */
  char buf[MAX_BUF];
  fd = open(myfifo, O_RDONLY);
  read(fd, buf, MAX_BUF);
  printf("Writer: %s\n", buf);
  close(fd);
  return 0;
}
```
# P5
```
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
#include <string.h>

int main(int argc, char *argv[])
{
	if (argc < 3 || argc > 4 || (argc == 3 && (!strcmp(argv[1], "-s"))))
	{
		printf("―Incorrect syntax
			for link creation\ n");
		return 1;
	}

	if (argc == 4)
	{
		if ((symlink(argv[2], argv[3])) == -1)
			printf("―Cannot create symbolic links\ n");
		else
			printf("―Symbolic links created\ n");
	}
	else
	{
		if ((link(argv[1], argv[2])) == -1)
			printf("―Cannot create hard links\ n");
		else
			printf("―Hard links created\ n");
	}

	return 0;
}
```

# P6
```
#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>

int main()
{
	int pid;
	pid = fork();	//Create a child process 
	if (pid < 0)
	{
		printf("Fork error\n");
		exit(0);
	}
	else if (pid == 0) exit(0);	//This is the child process. Exit immediately 
	sleep(2);	//This is the parent process. Sleep for a minute 
	system("ps -o pid,ppid,state,tty,command");
}
```
