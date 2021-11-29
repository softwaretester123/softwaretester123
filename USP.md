###P3
```
#define _POSIX_SOURCE #define _POSIX_C_SOURCE 199309L #include<stdio.h> #include<unistd.h> int main() { int res; if((res = sysconf(_SC_CLK_TCK))== -1) perror("sysconf"); else printf("Number of clock ticks: %d\n",res); if((res=sysconf(_SC_CHILD_MAX))==-1) perror("sysconf"); else printf("Max. Number of child processes: %d\n",(res)); if((res = pathconf("/",_PC_PATH_MAX)) == -1) perror("pathconf"); else printf("Max path length: %d\n",res); if((res = pathconf("/", _PC_NAME_MAX)) == -1) perror("pathconf"); else printf("Max number of characters in file name: %d\n",res); if((res=sysconf(_SC_OPEN_MAX))==-1) perror("sysconf"); else printf("Max number of open files/processes: %d\n",res); return 0;
}
```
