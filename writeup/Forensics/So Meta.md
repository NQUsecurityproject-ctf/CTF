## So Meta

題目:
> Find the flag in this picture.
***
### 思路:
> 打開是一個圖片，根據提示**metadata**可以得知flag在圖片中。
> 補充 :[Metadata](https://zh.wikipedia.org/wiki/%E5%85%83%E6%95%B0%E6%8D%AE)  
>**MetaData**是指描述資料的資料，如果想了解更多可以點超連結
***


### 解法:
> 利用**strings**指令將圖片轉為字串，再用**grep**過濾即可得到flag

```console
runmdy@pico-2019-shell1:/problems/so-meta_2_da856426d694a4f0637bf1b169d8524e$ strings pico_img.png  | grep "picoCTF"
picoCTF{s0_m3ta_3d6ced35})

```