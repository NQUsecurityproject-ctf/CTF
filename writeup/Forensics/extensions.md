## extensions
### 題目:
>This is a really weird text file TXT? Can you find the flag?



## 解法:
>我們將txt文件利用file指令得知他是一個png檔，只是被改了檔名，把檔名改回png後打開就會有flag
```
file flag.txt
flag.txt: PNG image data, 1697 x 608, 8-bit/color RGB, non-interlaced
```
## flag:
picoCTF{now_you_know_about_extensions}