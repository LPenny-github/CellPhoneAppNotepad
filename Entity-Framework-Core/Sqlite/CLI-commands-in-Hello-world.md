# CLI commands in Hello world


## 問題
 

考察 "Hello world" 這個專案用到的命令列指令：
（盡我所能地查，仍然有模糊的地方）


1. `dotnet add package Microsoft.EntityFrameworkCore.Sqlite`

1. `dotnet tool install --global dotnet-ef`

1. `dotnet add package Microsoft.EntityFrameworkCore.Design`

1. `dotnet ef migrations add InitialCreate`

1. `dotnet ef database update`


## 探索


1. `dotnet add package Microsoft.EntityFrameworkCore.Sqlite` ：在該專案中加入 "Microsoft.EntityFrameworkCore.Sqlite" 這個套件參考。
   
   * `dotnet add [<PROJECT>] package <PACKAGE_NAME>` ：將套件參考新增至專案檔。
     
     * 如果沒有給 <PROJECT> ，預設從該目錄底下找專案檔。
   
       * [dotnet add package](https://docs.microsoft.com/zh-tw/dotnet/core/tools/dotnet-add-package#synopsis)

   * Microsoft.EntityFrameworkCore.Sqlite 是一個什麼樣的工具（what）？

     * > SQLite database provider for Entity Framework Core.

       [Microsoft.EntityFrameworkCore.Sqlite](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore.Sqlite/)

   * 驗證是否成功安裝 Microsoft.EntityFrameworkCore.Sqlite
     * 到 .csproj 看看有沒有這行：

       ```cs
       <PackageReference Include="Microsoft.EntityFrameworkCore.Sqlite" Version="6.0.1" />
       ```
     
---  
取得 Entity Framework Core CLI 工具 [安裝 Entity Framework Core](https://docs.microsoft.com/zh-tw/ef/core/get-started/overview/install#get-the-entity-framework-core-tools)


2. `dotnet tool install --global dotnet-ef` ：安裝 .NET Core CLI 工具（指 dotnet-ef）。

   * `dotnet tool install <PACKAGE_NAME> -g|--global` ：在電腦上安裝指定的 .net 工具。

     * `-g|--global` ：在 Windows 中預設裝在 `%USERPROFILE%\.dotnet\tools` 。

       * [dotnet tool install](https://docs.microsoft.com/zh-tw/dotnet/core/tools/dotnet-tool-install#description)


3. `dotnet add package Microsoft.EntityFrameworkCore.Design` ：在該專案中加入 "Microsoft.EntityFrameworkCore.Design" 這個套件參考。

   * Microsoft.EntityFrameworkCore.Design 是一個什麼樣的工具（what）？

     * > Shared design-time components for Entity Framework Core tools.

       [Microsoft.EntityFrameworkCore.Design ](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore.Design/)

   * 驗證是否成功安裝 Microsoft.EntityFrameworkCore.Design

     * 到 .csproj 看看有沒有這幾行：

       ```cs
       <PackageReference Include="Microsoft.EntityFrameworkCore.Design" Version="6.0.1">
          <IncludeAssets>runtime; build; native; contentfiles; analyzers; buildtransitive</IncludeAssets>
          <PrivateAssets>all</PrivateAssets>
       </PackageReference>
       ```


* 驗證是否已正確安裝 EF Core CLI 工具：

  * `dotnet ef`
    
    * 安裝成功的結果

      ```
       _/\__
               ---==/    \\
         ___  ___   |.    \|\
        | __|| __|  |  )   \\\
        | _| | _|   \_/ |  //|\\
        |___||_|       /   \\\/\\

      Entity Framework Core .NET Command-line Tools 2.1.3-rtm-32065

      <Usage documentation follows, not shown.>
      ```

      [Entity Framework Core 工具參考-.NET Core CLI](https://docs.microsoft.com/zh-tw/ef/core/cli/dotnet#verify-installation)
---

4. `dotnet ef migrations add InitialCreate` ：加入新的遷移，遷移的名稱是 InitialCreate（自訂）。

   * `dotnet ef migrations add` ：加入新的遷移。
     
     * [Entity Framework Core 工具參考-.NET Core CLI](https://docs.microsoft.com/zh-tw/ef/core/cli/dotnet#dotnet-ef-migrations-add)

   * `migrations` （遷移 / 移轉）是什麼？
   
     * > 建立移轉的 Scaffolding，以針對模型建立一組初始資料表。

       [開始使用 EF Core](https://docs.microsoft.com/zh-tw/ef/core/get-started/overview/first-app?tabs=netcore-cli#create-the-database)


5. `dotnet ef database update` 
  
   * `database update` ：建立資料庫，並對資料庫套用新的 移轉 / 遷移。


## 結果

雖然查了很多資料（也不知道該不該查），仍然對一些 "概念"（？）不是很懂。

不了解是什麼（what），例如 design-time components 和 Scaffolding ；說不清楚到底為什麼（why），像是 package 。