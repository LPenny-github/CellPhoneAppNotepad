# Set a timer


## 目的


做兩個關於 倒數計時器 的應用，一個是 番茄鬧鐘，另一個是運動計時。

1. 養成好習慣。

   * 提示醒目：藉由發布在主畫面（聳動的圖示或標語？）或做成小工具來達成
   * 好操作
   * 及時反饋


## 預備


* 決定 番茄鬧鐘 要設幾分鐘。

* 決定 每天、每次運動 要設幾分鐘。


## 執行


番茄鬧鐘：

1. `數字` 

2. `顯示通知` ：修改字串為 "開始倒數計時 `@數字` 分" 。

3. `啟動計時器` ：
   
    * 選取 `@數字` 變數
    * 點一下 "分鐘" ，可選擇 "秒"、"分鐘"、"小時"


* **附帶說明** ：也可以直接把數字寫死在 `啟動計時器` 裡。

  * 為了簡單且有效確認是否有啟動番茄鬧鐘，增加步驟 2 `顯示通知` （2022/02/27）。

  * 因為鬧鐘設定 移到/合併 至 `健康` app （Health），所以無論手機背景聲音設定為何，鬧鈴內建是最大聲（也就是遵循 `健康` app 裡的設定）；而且使用 `設定背景聲音音量` 無效 （2022/05/13）。

---

運動計時器：一天運動共 30 分鐘，每次運動 10 分鐘。

1. 讓捷徑的通知顯示在通知中心

   * 設定 > 通知 > Siri 建議 > 捷徑 (打開)

1. 10 分鐘的番茄鬧鐘（自行參考上方做法）

1. `顯示通知`

   * 可參考之前的筆記： [Use the Show Notification action to build Hello World](https://github.com/LPenny-github/CellPhoneAppNotepad/blob/main/iPhone/Shortcuts/Hello-world/Use-the-Show-Notification-action.md)


* **注意** 無論是放在 `啟動計時器` 的前或後， `顯示通知` 會跑在倒數計時前面，所以實際運行會是： 

  橫幅通知 和 通知中心顯示通知 >> （倒數計時中） >> 計時結束的鈴響


## 驗證


手動驗證。