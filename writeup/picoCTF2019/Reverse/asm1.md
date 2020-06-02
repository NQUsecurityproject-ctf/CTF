## asm1
### 題目:
> What does asm1(0x4f3) return? Submit the flag as a hexadecimal value (starting with '0x'). NOTE: Your submission for this question will NOT be in the normal flag format. 
***
### 思路:
> 這題是一個簡單的組合語言稍微了解一下指令邏輯即可解出

```asm 
asm1:
	<+0>:	push   ebp
	<+1>:	mov    ebp,esp
	<+3>:	cmp    DWORD PTR [ebp+0x8],0x45d
	<+10>:	jg     0x512 <asm1+37>
	<+12>:	cmp    DWORD PTR [ebp+0x8],0x430
	<+19>:	jne    0x50a <asm1+29>
	<+21>:	mov    eax,DWORD PTR [ebp+0x8]
	<+24>:	add    eax,0x17
	<+27>:	jmp    0x529 <asm1+60>
	<+29>:	mov    eax,DWORD PTR [ebp+0x8]
	<+32>:	sub    eax,0x17
	<+35>:	jmp    0x529 <asm1+60>
	<+37>:	cmp    DWORD PTR [ebp+0x8],0x7cd
	<+44>:	jne    0x523 <asm1+54>
	<+46>:	mov    eax,DWORD PTR [ebp+0x8]
	<+49>:	sub    eax,0x17
	<+52>:	jmp    0x529 <asm1+60>
	<+54>:	mov    eax,DWORD PTR [ebp+0x8]
	<+57>:	add    eax,0x17
	<+60>:	pop    ebp
	<+61>:	ret    
```
我們在這邊簡單介紹會用到的指令，如果有興趣的話可以點擊後方連結查看更多[hit me](https://www.tutorialspoint.com/assembly_programming/assembly_conditions.htm)
- mov 
    - 將右邊的值填入左邊 
- cmp
    - 將前面的值與後面做比較(通常會搭配條件指令jg,jne....)
- jg
    - 大於等於跳
- jne
    - 不等於後面的值
- jmp
    - 無條件跳  

下面是mov  ebp,esp 這個指令在堆疊執行後的樣子
```

+------+
| ebp  |  <--- ebp
+------+
| ret  |  <--- ebp+0x4	
+------+
| 0x4f3|  <--- ebp+0x8
+------+
```
***
## 解法:

```asm 
asm1:
	<+0>:	push   ebp
	<+1>:	mov    ebp,esp
	<+3>:	cmp    DWORD PTR [ebp+0x8],0x45d	0x4f3跟0x45d比較
	<+10>:	jg     0x512 <asm1+37>				0x4f3>0x45 所以跳到+37
	<+12>:	cmp    DWORD PTR [ebp+0x8],0x430
	<+19>:	jne    0x50a <asm1+29>
	<+21>:	mov    eax,DWORD PTR [ebp+0x8]
	<+24>:	add    eax,0x17
	<+27>:	jmp    0x529 <asm1+60>
	<+29>:	mov    eax,DWORD PTR [ebp+0x8]
	<+32>:	sub    eax,0x17
	<+35>:	jmp    0x529 <asm1+60>
	<+37>:	cmp    DWORD PTR [ebp+0x8],0x7cd	0x4f3跟0x7cd比
	<+44>:	jne    0x523 <asm1+54>				0x4f3不等於0x7cd所以跳到+54
	<+46>:	mov    eax,DWORD PTR [ebp+0x8]
	<+49>:	sub    eax,0x17
	<+52>:	jmp    0x529 <asm1+60>
	<+54>:	mov    eax,DWORD PTR [ebp+0x8]		將ebp+0x8 的值移入eax暫存器
	<+57>:	add    eax,0x17						eax的值+0x17 --> 0x4f3+0x17=0x50a
	<+60>:	pop    ebp
	<+61>:	ret    
```
## flag:
>picoCTF{0x50a}