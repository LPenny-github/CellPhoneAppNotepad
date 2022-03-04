# DEFAULT


* 官方文件： [CREATE TABLE: 3.2. The DEFAULT clause](https://www.sqlite.org/lang_createtable.html)


## 簡述（建立資料表時 DEFAULT 關鍵字）


1. 當欄位建立時，沒有加上 DEFAULT 關鍵字，也不是設定 INTEGER PRIMARY KEY，使用 INSERT 語法卻沒有明確給值時，預設的值為 NULL 。

1. 使用 DEFAULT 關鍵字，可以更改 NULL 為指定值或是運算式（每次新增 row 卻沒有明確賦值時都會啟動運算）。

1. DEFAULT 關鍵字 後面也可以使用內建的特殊格式：CURRENT_TIME（格式為 "HH:MM:SS"）、CURRENT_DATE （"YYYY-MM-DD"） 、CURRENT_TIMESTAMP （"YYYY-MM-DD HH:MM:SS"）。

* **注意** ：以上簡述僅限於 CREATE TABLE ，當你想 ALTER TABLE 增加欄位時有其限制，例如：無法適用第 2、3 點，更多請參閱教程： [SQLite ALTER TABLE: Using SQLite ALTER TABLE to add a new column to a table](https://www.sqlitetutorial.net/sqlite-alter-table/)


## 驗證

### 實作： 1. 當欄位建立時，沒有加上 DEFAULT 關鍵字，也不是設定 INTEGER PRIMARY KEY，使用 INSERT 語法卻沒有明確給值時，預設的值為 NULL 。


（因為 DEFAULT 預設為 NULL ，在使用 Browse Data 上很容易察覺，所以下面實驗的是加入特定的預設值。）


原本資料庫內容：


--|NoteId|Word|MeaningInChinese
--|------:|:-----------|:-------------
1 |1 |tweezers   |  鑷子
2 |2 |clothespin |	洗衣夾
3 |3 |clothesline|	曬衣繩
3 |4 |flashlight |	手電筒
5 |5 |invoice    |	發票
6 |6 |spring     |	彈簧


```sql
ALTER TABLE EnglishVocabularyNote
ADD COLUMN ReviewCount INTEGER DEFAULT 0;
```

--|NoteId|Word|MeaningInChinese|ReviewCount
--|------:|:-----------|:----------|:----
1 |1 |tweezers   |  鑷子       |0
2 |2 |clothespin |	洗衣夾     |0
3 |3 |clothesline|	曬衣繩     |0
3 |4 |flashlight |	手電筒     |0
5 |5 |invoice    |	發票       |0
6 |6 |spring     |	彈簧       |0

---

### 實作： 3. DEFAULT 關鍵字 後面也可以使用內建的特殊格式：CURRENT_TIME（格式為 "HH:MM:SS"）、CURRENT_DATE （"YYYY-MM-DD"） 、CURRENT_TIMESTAMP （"YYYY-MM-DD HH:MM:SS"）。

（這邊實驗的是 CURRENT_DATE）

1. 建立新資料表。

   ```sql
   CREATE TABLE NoteReview (
	Id INTEGER PRIMARY KEY,
	Word TEXT,
	CreatedDate	TEXT DEFAULT CURRENT_DATE,
   );
   ```

2. 加入新的一筆資料。

   ```sql
   INSERT INTO NoteReview(Word)
   VALUES ('clothepin');
   ```

3. 輸出結果。

   ```sql
   SELECT * FROM NoteReview;
   ```

   --|Id|Word|CreatedDate
   --|------:|:-----------|:-------------
   1 |1 |clothepin   |  2022-03-04