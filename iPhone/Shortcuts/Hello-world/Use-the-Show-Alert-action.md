# Use the Show Alert action to build Hello World


## 目標


* 在 ios 15 作業系統的 iphone 上製作第一個 捷徑（shortcut）
  
  1. 名為 "Hello World!"

  1. 能夠顯示出 "安安洗洗睡睡？" ，並有 "取消" 與 "好" 兩個按鈕出現。

  1. 使用 `Show Alert`（顯示提示）。


## 預備


* `Show Alert`（顯示提示）：一種帶有 "取消" 和 "好" （也可以設定只有 "好"）的橫幅通知，在使用者點按前不會自動消失 / 上浮。

* 由於我們只需要把之前的作品，由 顯示通知 換成 顯示提示，為了精簡筆記，重複的部分請參酌：

  * [Use the Show Notification action to build Hello World](https://github.com/LPenny-github/CellPhoneAppNotepad/blob/main/iPhone/Shortcuts/Hello-world/Use-the-Show-Notification-action.md)

* 官方文件

  * [Use the Show Alert action in a shortcut on iPhone or iPad](https://support.apple.com/guide/shortcuts/use-the-show-alert-action-apdb9661c761/ios)


## 執行


* 下方點擊 `+ 加入動作` 

     * 最上方搜尋關鍵字 `顯示提示` 

       * 點擊 `顯示提示` 這個搜尋結果

         * 點一下這一行，編輯 "是否要繼續" 為 "安安洗洗睡睡？"

         * 點開 `>` ，可進階編輯
           
           1. 標題（預設為無，**橫幅顯示預設為粗體**）

           2. 是否顯示取消按紐（預設開啟）

           * **如果不確定顯示效果，可以善用最下方右側 `▶` ，跑跑看**


## 驗證


* 回到主畫面，手動點擊該捷徑，看見橫幅出現、比對橫幅中的文字。