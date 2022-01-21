# What is the touch command's equivalent in PowerShell?


答案： `code .gitignore`


## 問題

為一個剛加上 git 的專案，加入 .gitignore 。

* 印象中：
  
  * 要先加入 `.gitignore` 檔案（，然後再為它加入內容）。
  
  * 可以用 Windows 或 VS Code 裡的 PowerShell 完成。

  * 我用過。

## 探索

* Google 關鍵字：
  
  * add .gitignore
  
  * vscode add .gitignore
  
  * vscode powershell add .gitignore
  
## 結果 != 解法：完全無法執行

* Google 結果：

  1. `touch .gitignore` （for Linux）
       * **但我的作業系統是 Windows 10**

  2. 手動在資料夾加入 `.gitignore.txt`
       * **我希望可以用 Windows 或 VS Code 裡的 PowerShell 完成**


## （第二輪）問題

由上述第一項 Google 結果，用英文把問題重整為：

What is the **touch** command's **equivalent** in powershell?

（因為要找英文資料所以把問題用英文組織一遍，再抽取關鍵字來搜尋）

## （第二輪）探索

* 想法：

  1. 如果知道 `touch` 在 Linux 的行為，那有可能可以猜出同等在 PowerShell 的指令？
       
       * 重塑 Google 關鍵字：
       
         * man touch
       
           * man 是 manual（手冊） 的簡寫

  2. 重塑 Google 關鍵字：
       
       * **touch equivalent** powershell
       
       * powershell **equivalent of touch**

## （第二輪）結果 != 解法：可以解決問題但不是我想像中的

* 想法的實作結果：

  1. touch：
     
     * 在 Linux 環境中， `touch fileName` ：
     
       * 如果該檔案存在，則會改變存檔時間
     
       * 如果該檔案不存在，則會創造該檔案
     
     * > Update the access and modification times of each FILE to the
       current time.
       >
       > A FILE argument that does not exist is created empty, unless -c
       or -h is supplied.
       >
       [touch(1) — Linux manual page](https://man7.org/linux/man-pages/man1/touch.1.html#SEE_ALSO)
       
       * **我猜不出同等在 PowerShell 的指令，原來我對 PowerShell 不熟！**

  2. Google 結果：

     * `ni .gitignore`

       * ni 意思是 New-Item
     
     * `ft > .gitignore`
     
       * ft 意思是 Format-Table
     
         * [Format-Table](https://docs.microsoft.com/zh-tw/powershell/module/microsoft.powershell.utility/format-table?view=powershell-7.2)
     
     * [Equivalent of Linux `touch` to create an empty file with PowerShell [duplicate]](https://superuser.com/questions/502374/equivalent-of-linux-touch-to-create-an-empty-file-with-powershell)
    
     * **兩者都可以達成 "可以用 Windows 或 VS Code 裡的 PowerShell 完成" 這個目標，但不太像是我曾經用過的語法**


## （第三輪）問題

問題不只是 "What is the touch command's equivalent in powershell?" 

更重要的是使用 **VS Code** 裡的 PowerShell。

## （第三輪）探索

* 重塑 Google 關鍵字：

  * touch equivalent **vscode** powershell

## （第三輪）結果 == 解法：可以解決問題且是我想要的

* 結果：
  * `code .gitignore`

    * code 是 VS Code 的指令

    * code + （不存在目錄的）檔名 的作用跟 Linux 的 touch + （不存在目錄的）檔名 一樣，都會建立新檔案

    * > Name of a file to open. If the file doesn't exist, it will be created and marked as edited. You can specify multiple files by separating each file name with a space.
      >
      [Command Line Interface (CLI)](https://code.visualstudio.com/docs/editor/command-line#_opening-files-and-folders)


* 附註 Google 頁面上所呈現的標題：
  * The Visual Studio Code command-line options

