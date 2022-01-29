# How to test the actions in shortcuts


## 目的


* 運用 捷徑（shortcuts） 裡的 動作（action） 來顯示變數內容，如同 C# 裡使用 Console.WriteLine() 。


* 概述：
  
  * `Quick Look` （快速查看） ：如其名快速查看變數內容 / 結果。

  * `Stop and Output`  （停止並輸出） ：停止捷徑程式，並且輸出變數內容，可以選擇僅顯示於開發介面，或如同 `Show Result` （顯示結果） 般，讓使用者看見此動作。

    * 複習 [Use the Show Result action to build Hello World](https://github.com/LPenny-github/CellPhoneAppNotepad/blob/main/iPhone/Shortcuts/Hello-world/Use-the-Show-Result-action.md)


## 預備


* 基礎建構捷徑方式，不再贅述：
 
  * [Use the Show Notification action to build Hello World](https://github.com/LPenny-github/CellPhoneAppNotepad/blob/main/iPhone/Shortcuts/Hello-world/Use-the-Show-Notification-action.md#%E5%9F%B7%E8%A1%8C)

* 官方文件

  * [Testing your actions in Shortcuts on iPhone or iPad](https://support.apple.com/guide/shortcuts/test-your-actions-apda75604f37/5.0/ios/15.0)

  * [Shortcut completion on iPhone or iPad](https://support.apple.com/guide/shortcuts/shortcut-completion-apda9578f70f/ios)


## 執行


先作出一個字串變數，然後使用 `Quick Look` 和 `Stop and Output` 顯示變數內容。

---

製作字串變數：

1. 搜尋 `文字`

   * 點擊 `文字` 這個搜尋結果
   
     * 輸入目標文字，諸如 "Hello World!"

2. 搜尋 `設定變數` 或找找看 下一個動作建議 有沒有 `設定變數`

   * 設定變數名稱，例如：打招呼

---

選擇任一種方式測試變數 "打招呼"：

1. 搜尋 `快速查看`

   * 選擇欲察看的變數，預設為上一個出現的變數，也就是 "打招呼"

1. 搜尋 `停止並輸出`

   * 選擇欲察看的變數，預設為上一個出現的變數，也就是 "打招呼"

   * 若未提供輸出的位置
     
     * 不執行任何動作（預設）：只有開發者在 **開發介面** 按 `▶` 才會看見此輸出

       * 如果你點選主畫面中的捷徑，是無法看到輸出內容的。

     * 回應：行為如同 `Show Result` 

       * 如果你點選主畫面中的捷徑，會出現帶有 變數內容 及 `完成` 鈕的橫幅通知

       * 但若你是在開發者介面點按 `▶` ，是不會看到橫幅通知的。
       
         也就是說，在開發者介面使用 `▶` 去跑捷徑， `不執行任何動作` 與 `回應` 的這兩者的行為看起來會像是一樣的。

     * 拷貝到剪貼板

---


## 驗證


* 手動測試

