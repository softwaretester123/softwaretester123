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
