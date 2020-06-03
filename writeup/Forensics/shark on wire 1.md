## shark on wire 1
### 題目:
>We found this packet capture. Recover the flag.



## 思路:
>將題目給的附件下載下來之後會發現是一個pcap，pcap檔簡單來說就是一個封包檔。通常這類的檔案可以使用wireshark來作封包分析

## 解法:
> 利用wireshark打開後點選**analyze**
> 在選**flow**最後點選**UDP STREAM**
> 然後再右下角的stream那邊找找，然後就會發現flag
## flag:
picoCTF{not_too_bad_of_a_problem}