# How to define a one-to-many relationship


## 目標


製作兩個 資料表（table），帶有 一對多（one-to-many） 的關係。


## 預備


* 複習之前開一個資料表的經驗：

  * [How to create one table](https://github.com/LPenny-github/CellPhoneAppNotepad/blob/main/Entity-Framework-Core/Sqlite/Model/Create-one-table.md)


## 執行


1. 在專案中加入新檔案 `Model.cs` 。
   * 把 [How to create one table] 裡建資料模型的方式複製過來，照自己的意思改。

```csharp
using Microsoft.EntityFrameworkCore;

// 只要明確告知對映的方式，EF Core 會自動將 table 中 id 命名者設為 primary key。 

public class HomeRoom // Home Room 類似台灣 "班級" 的概念
{
    public int HomeRoomId{get; set;} // primary key
    public string HomeRoomName{get; set;}

    // 一間 home room 有很多學生
    public List<Student> students {get;} = new();
}

public class Student
{
    public int StudentId{get; set;} // primary key
    public string StudentName{get; set;}

    // 一位學生只有一間 home room
    public int HomeRoomId{get; set;} // foreign Key
    public HomeRoom homeRoom{get; set;}
}

public class Context : DbContext
{
    public DbSet<HomeRoom> HomeRooms { get; set; }
    public DbSet<Student> Students { get; set; }

    public string DbPath { get; private set; }

    public Context()
    {
        var folder = Environment.SpecialFolder.LocalApplicationData;
        var path = Environment.GetFolderPath(folder);
        DbPath = $"{path}{System.IO.Path.DirectorySeparatorChar}school.db";
    }

    // The following configures EF to create a Sqlite database file in the
    // special "local" folder for your platform.
    protected override void OnConfiguring(DbContextOptionsBuilder options)
        => options.UseSqlite($"Data Source={DbPath}");
}

```


## 驗證


* 打開專案裡的 `Migrations` 裡其中 `{你執行migration的日期}_{你對此次migration的命名}.Designer.cs` ，觀察裡面的結構，是否與你的藍圖相同。例如其中一段：

    ```csharp
    modelBuilder.Entity("Student", b =>
        {
            b.HasOne("HomeRoom", "homeRoom")       
                .WithMany("students")              
                .HasForeignKey("HomeRoomId")       
                .OnDelete(DeleteBehavior.Cascade)
                .IsRequired();

            b.Navigation("homeRoom");
        });

    modelBuilder.Entity("HomeRoom", b =>
        {
            b.Navigation("students");
        });
    ```

* 更改 `Program.cs` 的內容。
  * 把 [How to create one table] 裡建資料模型的方式複製過來，照自己的意思改。
    * 目標是 新增（Create） 和 提取（Read）。

  ```csharp
  internal class Program
  {
    private static void Main()
    {
        using (var db = new Context())
        {
            // Create
            HomeRoom homeRoom1 = new HomeRoom { HomeRoomId = 100, HomeRoomName = "草食" };
            HomeRoom homeRoom2 = new HomeRoom { HomeRoomId = 200, HomeRoomName = "肉食" };

            db.Add(new Student { StudentId = 1, StudentName = "雷格西" , HomeRoomId = 200});
            db.Add(new Student { StudentId = 2, StudentName = "哈魯" , HomeRoomId = 100 });
            db.Add(new Student { StudentId = 3, StudentName = "路易"  , HomeRoomId = 100});
            db.Add(new Student { StudentId = 4, StudentName = "茱諾" , HomeRoomId = 200});
            db.Add(new Student { StudentId = 5, StudentName = "雅夫亞" , HomeRoomId = 200});

            db.SaveChanges();

            // Read

            // 印出所有學生
            var studentList = db.Students;
            foreach (var student in studentList)
            {
                Console.WriteLine(student.StudentId + " : " + student.StudentName);

            }

            // 印出每間 home room，以及其學生
            var homeRoomList = db.HomeRooms.OrderBy(b => b.HomeRoomId);

            foreach (var item in homeRoomList)
            {
                Console.WriteLine(item.HomeRoomId + " : " + item.HomeRoomName);
                foreach (var student in item.students)
                {
                    Console.WriteLine(student.StudentId + " : " + student.StudentName);
                }
            }

            // Output:
            //
            // 1 : 雷格西
            // 2 : 哈魯
            // 3 : 路易
            // 4 : 茱諾
            // 5 : 雅夫亞
            // 100 : 草食
            // 2 : 哈魯
            // 3 : 路易
            // 200 : 肉食
            // 1 : 雷格西
            // 4 : 茱諾
            // 5 : 雅夫亞
        }
      }
  }
```