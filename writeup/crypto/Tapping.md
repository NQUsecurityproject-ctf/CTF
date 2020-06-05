## Tapping
### 題目:
>Theres tapping coming in from the wires. What's it saying nc 2019shell1.picoctf.com 32273.

## 思路:
>根據我們連上看到的內容再加上題目給的提示我們可以知道這個是摩斯密碼
```console
runmdy@pico-2019-shell1:/problems/where-is-the-file_1_54878e9f5b7db0ddbaf642cdb5c9b3b5$ nc 2019shell1.picoctf.com 32273
.--. .. -.-. --- -.-. - ..-. { -- ----- .-. ... ...-- -.-. ----- -.. ...-- .---- ... ..-. ..- -. .---- -.... --... --... ..--- ..... --... ..--- ---.. --... } 
```

## 解法:
>找個線上摩斯解碼工具解碼

## 影片:
[hit me](https://youtu.be/av_wMgkIb7s)
## flag:
picoctf{m0rs3c0d31sfun1677257287}