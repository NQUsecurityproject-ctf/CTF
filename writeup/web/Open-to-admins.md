## Open-to-admins
### 題目:
>This secure website allows users to access the flag only if they are admin and if the time is exactly 1400.
***
### 思路:
>根據題目說明將身分改成admin並且將時間標記改成1400，再結合提示去修改cookie
***
### 解法:
在瀏覽器中打開發人員工具(本題以chrom為例)，點選**application**，左邊有個**cookie欄位**，打開後在NAME欄位下案右鍵選**add new**新增兩個cookie，**admin**跟**time**，前面的值為true後面為**1400**，重新整理瀏覽器後按下flag即可取得。

|Name|Value|
|:-----|:-----|
|admin|true|
|time|1400|
***
## 影片:
[hit me](https://youtu.be/n228SS-ZOlE)
***
## flag:
>picoCTF{0p3n_t0_adm1n5_cc661e91}