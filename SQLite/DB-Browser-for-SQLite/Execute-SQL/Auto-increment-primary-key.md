# Auto increment primary key


## 目的


上次作筆記 [How to create one table](https://github.com/LPenny-github/CellPhoneAppNotepad/blob/main/SQLite/DB-Browser-for-SQLite/Execute-SQL/Create-one-table.md) 時，我發現自己並沒有完全達成拷貝。

漏了 **自動生成 id** 這件事情。也就是下面這一段：

* [How to create one table](https://github.com/LPenny-github/CellPhoneAppNotepad/blob/main/Entity-Framework-Core/Sqlite/Model/Create-one-table.md)

    * 這個 table 的主要結構如下：

      ```csharp
      public class EnglishVocabularyNote
      {
    
        // 只有一個 table 要加上 [key] 標示，不然 EF 會不知道哪一個是 primary key 或是 根本沒有 primary key 。
        // [key] 預設是自動產生，從 1 開始。 <-- **這一行**
    
        [Key] 
        public int NoteId { get; set; }
        public string Word { get; set; }
        public string MeaningInChinese { get; set; }
      }
      ```


## 預備


* 網路問答

    * [Is there an auto increment in sqlite?](https://stackoverflow.com/questions/7905859/is-there-an-auto-increment-in-sqlite)

* 官方文件（還沒全部看完）

    * [SQLite Autoincrement](https://www.sqlite.org/autoinc.html)

        > On an INSERT, if the ROWID or INTEGER PRIMARY KEY column is not explicitly given a value, then it will be filled automatically with an unused integer, usually one more than the largest ROWID currently in use. This is true regardless of whether or not the AUTOINCREMENT keyword is used.

    * [Rowid Tables](https://www.sqlite.org/rowidtable.html)


## 執行


官方文件指出，只要是欄位是 INTEGER PRIMARY KEY 在增加資料時，當沒有給明確的值，預設會自動遞增數值。

那就來試試看：


```sql
INSERT INTO EnglishVocabularyNote (Word, MeaningInChinese)
VALUES ('flashlight', '手電筒')
```


## 驗證


原本資料表裡的內容為：


--|NoteId|Word|MeaningInChinese
--|------:|:-----------|:-------------
1 |1     |tweezers   |  鑷子
2 |2     |clothespin |	洗衣夾
3 |3     |clothesline|	曬衣繩


剛才多新增一筆資料 flashlight ，查看看它的 NoteId 。

預計會是： `4` 。


```sql
SELECT NoteId FROM EnglishVocabularyNote
WHERE Word = 'flashlight'
```

結果：


--|NoteId|
--|------:|
1 |4     |