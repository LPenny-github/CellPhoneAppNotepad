# What and Why is `--no-https`


## 問題描述


[ 求解 ] `dotnet new blazorserver -o BlazorApp --no-https` 中的 `--no-https` 是什麼意思（What & Why）？

我看了 [Blazor Tutorial - Build your first Blazor app](https://dotnet.microsoft.com/en-us/learn/aspnet/blazor-tutorial/intro
) ，成功做出 Hello World。

但在寫筆記時，無法解釋 `--no-https` 是什麼意思（What & Why）。


## What


"--no-https" ：代表預設關閉 https （即 使用 http）


## Why


* http 
   * 優點：簡單、新人好上手
   * 缺點：不安全。無法知道資料是否來自目的方，沒有防禦竊聽與竄改。

* https
   * 優點：使用加密機制，以防禦竊聽與竄改。
   * 缺點：對新手而言相對複雜，需要具備加密的先備知識。


## Why not


不使用 "--no-https" 指令：使用 https 來顯示網頁，就不會彈跳出不安全的警告（因為 http 並不安全）


## 驗證


* 打開檔案 `launchSettings.json` 
   * 使用："--no-https" ：applicationUrl 只會有 http
   * 沒有使用："--no-https" ：applicationUrl 會有 https 與 http


* 實作兩種 BlazorServer （無論是否加上指令 "--no-https"），都可以正常跑出 Hello World。


## 參考資料

* [ 已解決 ] `dotnet new blazorserver -o BlazorApp --no-https` 中的 `--no-https` 是什麼意思（What & Why）？（Blazor 全端開發者社群）
  * https://www.facebook.com/groups/blazor/posts/1647199328820809

* Blazor Tutorial - Build your first Blazor app
  * https://dotnet.microsoft.com/en-us/learn/aspnet/blazor-tutorial/intro