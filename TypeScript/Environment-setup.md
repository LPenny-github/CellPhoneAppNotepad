# Environment setup


## 目的


在 VS Code 上架設可操作 TypeScript 的環境。


## 步驟

1. （自選）在 VS Code 上安裝 TypeScript 應用：讓語法上色。
    
   * JavaScript and TypeScript Nightly

1. （自選）下載 node.js ：裡面有 npm ，待會下載 TypeScript 編譯器會很方便。

   * https://nodejs.org/en/

1. 打開 Powershell 下載 TypeScript 編譯器： `npm install -g typescript`

   * 確定 TypeScript 編譯器 裝載成功： `tsc`

     * 如果出現錯誤如下，請執行下一個自選步驟：

       ```
       tsc : File C:\Users\coldb\AppData\Roaming\npm\tsc.ps1 cannot be loaded because running scripts is disabled on this system. For more information, see about_Execution_Policies at https:/go.microsoft.com/fwlink/?LinkID=135170.
       ```

1. （自選）在 Powershell 執行，變更運行權限： `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`

    * 請見： [about_Execution_Policies](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_execution_policies?view=powershell-7.2#change-the-execution-policy)

    * 確定 TypeScript 編譯器 是否裝載成功： `tsc`

      * 如果裝載成功會出現 版本號 與 建議指令： 
        
        ```
        Version 4.6.2
        tsc: The TypeScript Compiler - Version 4.6.2
        TS 
        COMMON COMMANDS
        ...
        ```

1. 做一個 Hello World 試試看。