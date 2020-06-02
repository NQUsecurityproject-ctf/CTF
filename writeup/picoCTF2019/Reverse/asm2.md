## asm2
### 題目:
>What does asm2(0xe,0x22) return?

### 思路:
>此題比arm1多了一個參數，並在最後求出ebp-0x4的值。


```asm
asm2:
        <+0>:   push   ebp
        <+1>:   mov    ebp,esp
        <+3>:   sub    esp,0x10
        <+6>:   mov    eax,DWORD PTR [ebp+0xc]
        <+9>:   mov    DWORD PTR [ebp-0x4],eax
        <+12>:  mov    eax,DWORD PTR [ebp+0x8]
        <+15>:  mov    DWORD PTR [ebp-0x8],eax
        <+18>:  jmp    0x50c <asm2+31>
        <+20>:  add    DWORD PTR [ebp-0x4],0x1
        <+24>:  add    DWORD PTR [ebp-0x8],0xd1
        <+31>:  cmp    DWORD PTR [ebp-0x8],0x9087
        <+38>:  jle    0x501 <asm2+20>
        <+40>:  mov    eax,DWORD PTR [ebp-0x4]
        <+43>:  leave  
        <+44>:  ret    

```
這次多的指令
- jle 
    - 如果小於就跳
## 解法:
>根據指令來做邏輯判斷，為求詳細我們將指令拆成兩步驟，一步是mov類的，另一部分則是跳躍。

>        <+6>:   mov    eax,DWORD PTR [ebp+0xc] 
>        <+9>:   mov    DWORD PTR [ebp-0x4],eax
>        <+12>:  mov    eax,DWORD PTR [ebp+0x8]
>        <+15>:  mov    DWORD PTR [ebp-0x8],eax

做完以上指令後stack的狀態
```

+------+
| 0xe  |  <--- ebp-0x8
+------+
| 0x22 |  <--- ebp-0x4
+------+
| ebp  |  <--- ebp
+------+
| ret  |  <--- ebp+0x4	
+------+
| 0xe  |  <--- ebp+0x8
+------+
| 0x22 |  <--- ebp+0xc
+------+
```


>接下來進行跳耀的部分


>        <+18>:  jmp    0x50c <asm2+31>             無條件跳至+31
>        <+20>:  add    DWORD PTR [ebp-0x4],0x1     將ebp-0x4+0x1
>        <+24>:  add    DWORD PTR [ebp-0x8],0xd1    將ebp-0x8+0xd1
>        <+31>:  cmp    DWORD PTR [ebp-0x8],0x9087  讓ebp-0x8跟0x9087做比較
>        <+38>:  jle    0x501 <asm2+20>             若小於則跳至+20
>        <+40>:  mov    eax,DWORD PTR [ebp-0x4]     將ebp-0x4的值放入eax

如果有學過一些簡單的程式的話，就會發現這邊其實就是一個簡單的迴圈

經過計算讓ebp-0x8(0xe)=0x9087大概需要做B0(176)次，因此我們為了滿足條件要>0x9087的話還需多做一次，所以我們額外加1次

ebp-0x4(0x22)+B0+1 = d3

最後回傳的值為d3
## flag:

picoCTF{0xd3}


