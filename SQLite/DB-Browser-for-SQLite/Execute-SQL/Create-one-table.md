# How to create one table


## 目標


用 DB Browser 的 `execute SQL` 功能，做出如同在 EF Core 建立的 table 。

  * [How to create one table](https://github.com/LPenny-github/CellPhoneAppNotepad/blob/main/Entity-Framework-Core/Sqlite/Model/Create-one-table.md)

    * 這個 table 的主要結構如下：

      ```csharp
      public class EnglishVocabularyNote
      {
    
        // 只有一個 table 要加上 [key] 標示，不然 EF 會不知道哪一個是 primary key 或是 根本沒有 primary key 。
        // [key] 預設是自動產生，從 1 開始。
    
        [Key] 
        public int NoteId { get; set; }
        public string Word { get; set; }
        public string MeaningInChinese { get; set; }
      }
      ```
    * 填入的資料為：

      ```csharp
      // 1、tweezers : 鑷子
      // 2、clothespin : 洗衣夾
      // 3、clothesline : 曬衣繩
      ```


## 預備


準備 SQL 語法（非必要）

  * 可以使用 GUI 介面建立 table ，然後觀察 DB Browser 的 log 是怎麼寫的 😆

    **注意** ： DB Browser 的 log 會把 資料表名稱、欄位名稱......加上 `""` ， SQL 語法不需要加上 `""` ，但 `execute SQL`無論是否有 `""` 都可以被接受。


## 執行


1. New Database > 命名檔案 > 儲存 。（快捷鍵： `ctrl` + `N`）

   * 或是建造一個 In-Memory 的檔案，關閉檔案後資料即消失。  

1. 點擊頁籤 `execute SQL` 。

1. 建立資料表，打完後按圖示 `▶` 或是 快捷鍵：`ctrl` + `R` ，之後的步驟都是如此。

   ```sql
    CREATE TABLE EnglishVocabularyNote(
	NoteId INTEGER,
	Word TEXT NOT NULL,
	MeaningInChinese TEXT NOT NULL,
	PRIMARY KEY(NoteId)
    )
   ```

1. 填入資料：

   ```sql
    INSERT INTO EnglishVocabularyNote
    VALUES(1, 'tweezers', '鑷子'),
    (2, 'clothespin','洗衣夾'),
    (3, 'clothesline', '曬衣繩')
   ```



## 驗證


1. 把 table 裡的資料調出來：

   ```sql
    SELECT * FROM EnglishVocabularyNote
   ```


1. 呈現結果：

    --|NoteId|Word|MeaningInChinese
    --|------:|:-----------|:-------------
    1 |1     |tweezers   |  鑷子
    2 |2     |clothespin |	洗衣夾
    3 |3     |clothesline|	曬衣繩