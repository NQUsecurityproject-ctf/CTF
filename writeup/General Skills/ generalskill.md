## 2Warm - Points: 50

Can you convert the number 42 (base 10) to binary (base 2)?

### Flag:

```
picoCTF{00101010}
 ```
***
## Lets Warm Up - Points: 50

If I told you a word started with 0x70 in hexadecimal, what would it start with in ASCII?

### Flag:

```
picoCTF{p}
```
***
## Warmed Up - Points: 50

What is 0x3D (base 16) in decimal (base 10).

### Flag: 

```
picoCTF{61}
```
***
## Bases - Points: 100

What does this *bDNhcm5fdGgzX3IwcDM1* mean? I think it has something to do with bases.

> 解題想法: 用base64 解密 

### Flag:

```
picoCTF{l3arn_th3_r0p35}
```
***
## First Grep - Points: 100

Can you find the *flag* in file? This would be really tedious to look through manually, something tells me there is a better way.

> 解題想法: 將 flag 直接打開之後發現大量的字符，可以使用*grep*指令將想要的字元過濾出來

```
cat file | grep picoCTF
```
### Flag:

```
picoCTF{grep_is_good_to_find_things_887251c6}
```
***
## Resources - Points: 100

We put together a bunch of resources to help you out on our website! If you go over there, you might even find a flag! https://picoctf.com/resources

> 解題想法: 直接點開連結，就可以看到Flag

### Flag:

```
picoCTF{r3source_pag3_f1ag}
```
***
## strings it - Points: 100

Can you find the flag in file without running it? You can also find the file in /problems/strings-it_0_b76c77672f6285e3a39c188481cdff99 on the shell server.

> 解題想法: 根據提示使用strings指令後會發現大量字串因此配合*grep*指令過濾想要的內容

```
strings strings | grep picoCTF
```

### Flag:

```
picoCTF{5tRIng5_1T_f1527258}
```
***
## what's a net cat? - Points: 100

Using netcat (nc) is going to be pretty important. Can you connect to 2019shell1.picoctf.com at port 4158 to get the flag?

> 解題想法: 利用*nc*指令連接

```
nc 2019shell1.picoctf.com 4158
```
### Flag:

```
picoCTF{nEtCat_Mast3ry_700da9c7}
```
***
### Based - Points: 200

To get truly 1337, you must understand different data encodings, such as hexadecimal or binary. Can you get the flag from this program to prove you are on the way to becoming 1337? Connect with nc 2019shell1.picoctf.com 28758

> 解題想法: 根據題目需要將不同的型態轉成字串，可以利用線上解碼器來解題

### Flag:

```
 picoCTF{learning_about_converting_values_4b4e293e}
```
***
## First Grep: Part II

題目:
> Can you find the flag in /problems/first-grep--part-ii_1_4496a9af2273007b52d4a1adec323b76/files on the shell server? Remember to use grep.

## 解題想法:
> 進到該目錄會發現眾多目錄，我們可以利用grep來搜尋

```
grep -r  picoCTF files*
```
## flag:
>picoCTF{grep_r_to_find_this_af11356f}
***
## where-is-the-file

## 題目:
> I've used a super secret mind trick to hide this file. Maybe something lies in /problems/where-is-the-file_1_54878e9f5b7db0ddbaf642cdb5c9b3b5.

## 解法:
利用ls -al顯示隱藏檔案  
再利用cat 看其內容
```console
runmdy@pico-2019-shell1:/problems/where-is-the-file_1_54878e9f5b7db0ddbaf642cdb5c9b3b5$ ls
runmdy@pico-2019-shell1:/problems/where-is-the-file_1_54878e9f5b7db0ddbaf642cdb5c9b3b5$ ls -al
total 80
drwxr-xr-x   2 root       root        4096 Sep 28  2019 .
drwxr-x--x 684 root       root       69632 Oct 10  2019 ..
-rw-rw-r--   1 hacksports hacksports    39 Sep 28  2019 .cant_see_me
runmdy@pico-2019-shell1:/problems/where-is-the-file_1_54878e9f5b7db0ddbaf642cdb5c9b3b5$ cat .cant_see_me 
picoCTF{w3ll_that_d1dnt_w0RK_3e782057}
```
## flag:
picoCTF{w3ll_that_d1dnt_w0RK_3e782057}

