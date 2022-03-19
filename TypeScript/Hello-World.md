# Hello World


## 目的


在 VS Code 裡，運行第一個 TypeScript 檔案，印出 "Hello World" 。


## 預備


1. 設定運行環境： [Environment setup](https://github.com/LPenny-github/CellPhoneAppNotepad/blob/main/TypeScript/Environment-setup.md)

1. 閱讀 VS Code 對 TypeScript 的說明： [TypeScript tutorial in Visual Studio Code](https://code.visualstudio.com/docs/typescript/typescript-tutorial)


## 執行


1. 開新的/設定 （專案）資料夾。

1. 新增檔案： `helloworld.ts` ，檔案內容如下：

   ```typescript
   console.log("Hello World"); 
   ```


## 驗證


1. 打開 VS Code 的 CLI（預設為 Powershell）

1. 鍵入指令，編譯 TypeScript 檔案 為 Javascript 檔案： `tsc helloworld.ts` 。

   * 編譯成功的話，專案資料夾會出現 `tsc helloworld.js` ，你也可以點開來看。在這個例子中因為語法相似，所以內容是一樣的。

1. 鍵入指令，編譯 Javascript 檔案：`node helloworld.js` 。

   * 編譯成功的話，在 TERMINAL 可以看到印出字串 Hello World 。