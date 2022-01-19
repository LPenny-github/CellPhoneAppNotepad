# How to create one table 


## 目標


在全新的 ConsoleApp 中使用 EF Core，並開一個有 primary key 的資料表。

這個資料表會儲存目前學習到的英文單字，可以 儲存（Create） 和 印出已儲存的內容（Read）。


## 預備


1. 創建一個 ConsoleApp，能夠跑出 "Hello World!" 。
   * [教學課程：使用 Visual Studio Code 建立 .NET 主控台應用程式](https://docs.microsoft.com/zh-tw/dotnet/core/tutorials/with-visual-studio-code?pivots=dotnet-6-0)

1. `dotnet add package Microsoft.EntityFrameworkCore.Sqlite` ：安裝 SQLite 套件
   * 忘記的話可以複習教程： [開始使用 EF Core](https://docs.microsoft.com/zh-tw/ef/core/get-started/overview/first-app?tabs=netcore-cli#install-entity-framework-core)


## 執行


1. 在專案中加入新檔案 `Model.cs` 。
   * 把 [開始使用 EF Core] 裡建資料模型的方式複製過來，照自己的意思改。


```csharp
using System.ComponentModel.DataAnnotations;
using Microsoft.EntityFrameworkCore;

public class EnglishVocabularyNote
{
    // 只有一個 table 要加上 [key] 標示，不然 EF 會不知道哪一個是 primary key 或是 根本沒有 primary key 。
    // [key] 預設是自動產生，從 1 開始。
    [Key] 
    public int NoteId { get; set; }
    public string Word { get; set; }
    public string MeaningInChinese { get; set; }
}

public class NoteContext : DbContext
{
    public DbSet<EnglishVocabularyNote> EnglishVocabularyNotes { get; set; }

    public string DbPath { get; }

    public NoteContext()
    {
        var folder = Environment.SpecialFolder.LocalApplicationData;
        var path = Environment.GetFolderPath(folder);
        DbPath = System.IO.Path.Join(path, "EnglishVocabularyNotes.db");
    }

    // （教程的註解）
    // The following configures EF to create a Sqlite database file in the
    // special "local" folder for your platform.
    protected override void OnConfiguring(DbContextOptionsBuilder options)
        => options.UseSqlite($"Data Source={DbPath}");
}
```

2. 執行教程提供的建立資料模型命令。
   * 複製貼上就好，如果有不需要執行的命令（例如 工具已安裝）， PowerShell 會自動往下執行。

```powershell
dotnet tool install --global dotnet-ef
dotnet add package Microsoft.EntityFrameworkCore.Design
dotnet ef migrations add InitialCreate
```

3. 如果在建立資料庫之後，你對資料模型還有更動，記得使用 `dotnet ef database update` 。


## 驗證


* 更改 `Program.cs` 的內容。
  * 把 [開始使用 EF Core] 裡建資料模型的方式複製過來，照自己的意思改。
    * 目標是 新增（Create） 和 提取（Read）。

```csharp
using (var db = new NoteContext())
{
    // Create

    db.Add(new EnglishVocabularyNote { Word = "tweezers", MeaningInChinese = "鑷子" });
    db.Add(new EnglishVocabularyNote { Word = "clothespin", MeaningInChinese = "洗衣夾" });
    db.Add(new EnglishVocabularyNote { Word = "clothesline", MeaningInChinese = "曬衣繩" });

    db.SaveChanges();

    var words = db.EnglishVocabularyNotes.OrderBy(a => a.NoteId);

    foreach (var word in words)
    {
        Console.WriteLine(word.NoteId + "、" + word.Word + " : " + word.MeaningInChinese);
    }

    // Output:

    // 1、tweezers : 鑷子
    // 2、clothespin : 洗衣夾
    // 3、clothesline : 曬衣繩
}
```