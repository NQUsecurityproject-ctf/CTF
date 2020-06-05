## Irish-Name-Repo 1
### 題目:
>Do you think you can log us in? Try to see if you can login!

## SQL注入:
> 在輸入的字串之中夾帶SQL指令，在設計不良的程式當中忽略了字元檢查，那麼這些夾帶進去的惡意指令就會被資料庫伺服器誤認為是正常的SQL指令而執行，因此遭到破壞或是入侵。

## 解法:
>為了繞過帳號密碼的判定我在這邊做一個經典的sql注入
在帳號的部分輸入admin
在密碼的地方打上'or 1 = 1 --


## 影片:
[hit me](https://youtu.be/LFIq-0WD0uk)

## flag:
picoCTF{s0m3_SQL_0397f20c}