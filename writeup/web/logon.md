## logon
### 題目:
>The factory is hiding things from all of its users. Can you login as logon and find what they've been looking at?
***



### 思路:
> 當我隨便測試輸入密碼的時候發現都可以登入於是我案下F12檢查application裡面的cookie欄位發現我在按下登入的時候admin值會跳成False因此推估可能跟cookie的admin欄位有關

## cookie:
>Cookie 是您造訪過的網站所建立的檔案，可儲存您的瀏覽資訊，提供您更流暢方便的網路使用體驗。 啟用Cookie 後，網站就可讓您保持登入狀態、記住您的網站偏好設定，並提供您與所在地相關的內容。
## 解法
> 登入時將admin欄位改為True，重新整理


## flag:
>picoCTF{th3_c0nsp1r4cy_l1v3s_2e19dad3}