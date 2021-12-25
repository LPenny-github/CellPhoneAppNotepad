# How to build "Hello World" (your first Blazor)


## 預備
 

.Net SDK


## 製作


1. 打開 PowerShell 或 CLI

1. `dotnet new blazorserver -o BlazorApp --no-https` 

   * `-o BlazorApp` ：變更專案名稱為 BlazorApp 。
     * 專案名稱預設與資料夾名稱相同。

   * `--no-https` ： **我看不懂，相關資料先列在下面**

     ```txt
       --no-https                 Whether to turn off HTTPS. This option only applies if Individual, IndividualB2C, SingleOrg, or MultiOrg aren't used for --auth.

                                  bool - Optional

                                  Default: false
        
       -au|--auth                 The type of authentication to use

                                      None             - No authentication

                                      Individual       - Individual authentication

                                      IndividualB2C    - Individual authentication with Azure AD B2C

                                      SingleOrg        - Organizational authentication for a single tenant

                                      MultiOrg         - Organizational authentication for multiple tenants

                                      Windows          - Windows authentication

                                  Default: None
     ```

    * 有任何看不懂的指令，都可以用 `dotnet new BlazorServer -h` 查詢。

1. `cd .\BlazorApp\` ：指向檔案 `BlazorApp`

1. `dotnet watch` 
   * 結束記得按 `ctrl` + `C`


## 參考資料

* Blazor Tutorial - Build your first Blazor app
  * https://dotnet.microsoft.com/en-us/learn/aspnet/blazor-tutorial/intro