## whats-the-difference
### 題目:Can you spot the difference? kitters cattos.
***
### 解法:
> 打開兩張圖片可以發現兩者是相似的只是cattos那張有些不同
>* 我們可以從以下兩種方法則一 
>    -	1.將2進位轉16進位在用diff比較
>    -  2.用cmp指令來比較
>  
> 本文採用第二種
> cmp -lc  指令可以將兩者不同的部分列出來   
> -l是將內容行列式列出   
> -c 是將內容轉成ascii  
>我們可以清楚可見從左數過來第五行就是我們的flag
```console
runmdy@pico-2019-shell1:/problems/whats-the-difference_0_00862749a2aeb45993f36cc9cf98a47a$ cmp -lc kitters.jpg cattos.jpg 
  49734 231 M-^Y 160 p
  49735 235 M-^] 151 i
  49736 230 M-^X 143 c
  49737 310 M-H  157 o
  87663  12 ^J   103 C
 162650 364 M-t  124 T
 175231 153 k    106 F
 175232 261 M-1  173 {
 211986 230 M-^X 164 t
 211987 222 M-^R 150 h
 211988  15 ^M    63 3
 211989 330 M-X  171 y
 284427 122 R    162 r
 292340 174 |     63 3
 292341 371 M-y  137 _
 331830 216 M-^N 141 a
 331831 365 M-u   65 5
 426632 346 M-f  137 _
 439903 360 M-p  144 d
 515770 112 J     61 1
 515771 252 M-*  146 f
 583608 341 M-a  146 f
 640996 310 M-H   63 3
 688795  77 ?    162 r
 688796 107 G     63 3
 702943  23 ^S   156 n
 751424 243 M-#  164 t
 754731  61 1    137 _
 754732 113 K     64 4
 754733 274 M-<  163 s
 754734 304 M-D  137 _
 796226  43 #    142 b
 871159 256 M-.  165 u
 871160   6 ^F    67 7
 871161 316 M-N   67 7
 871162 346 M-f   63 3
 927506 347 M-g  162 r
 927507 212 M-^J 137 _
 927508 122 R     64 4
 994666 376 M-~  156 n
 994667  43 #    144 d
 994668 377 M-^? 137 _
1068577 234 M-^\ 152 j
1068578 344 M-d   63 3
1068579 203 M-^C  61 1
1068580 222 M-^R  61 1
1068581 162 r    171 y
1101444   5 ^E   137 _
1101445 173 {    141 a
1101446   7 ^G   163 s
1101447 300 M-@  154 l
1171017  53 +    153 k
1171018 147 g    152 j
1171019 356 M-n  146 f
1241182  51 )    144 d
1241183 224 M-^T 163 s
1241184 200 M-^@ 141 a
1241185 106 F    154 l
1272572 217 M-^O 153 k
1272573 156 n    146 f
1337150   4 ^D   163 s
1410459 345 M-e  154 l
1410460 340 M-`  153 k
1460208   5 ^E   146 f
1510914 237 M-^_ 154 l
1567157 322 M-R  153 k
1567158 100 @    152 j
1567159  42 "    144 d
1567160 220 M-^P 163 s
1567161 205 M-^E 146 f
1581925 315 M-M  144 d
1581926 244 M-$  163 s
1581927 215 M-^M 172 z
1581928 147 g    155 m
1581929 257 M-/  172 z
1677065 176 ~     61 1
1677066 341 M-a   60 0
1764510 357 M-o   65 5
1764511 210 M-^H  64 4
1764512  31 ^Y    70 8
1766742  13 ^K   175 }
```
>然後我們可以使用awk 跟 tr 做處理
awk'{print$5}' | tr -d '\n'
```console
runmdy@pico-2019-shell1:/problems/whats-the-difference_0_00862749a2aeb45993f36cc9cf98a47a$ cmp -lc kitters.jpg cattos.jpg | awk '{print$5}' | tr -d '\n'
picoCTF{th3yr3_a5_d1ff3r3nt_4s_bu773r_4nd_j311y_aslkjfdsalkfslkflkjdsfdszmz10548}

```
## flag:  
**picoCTF{th3yr3_a5_d1ff3r3nt_4s_bu773r_4nd_j311y_aslkjfdsalkfslkflkjdsfdszmz10548}**
