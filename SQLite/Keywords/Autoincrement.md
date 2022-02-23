# Autoincrement


[SQLite Autoincrement](https://www.sqlite.org/autoinc.html)


## 簡述


1. 耗效能。

1. INTEGER PRIMARY KEY 可能做到 ROWID 效果（屏除設定為 WITHOUT ROWID），內容型態為 64-bit signed integer 。

1. 在 INTEGER PRIMARY KEY 設計下， INSERT 沒有給定 ID 的話，預設為 ROWID +1 （無論是否有加上關鍵字 AUTOINCREMENT ）。

    * 如果你有指定 ID 的值，系統會照你給的資料寫入。


1. 在 INTEGER PRIMARY KEY AUTOINCREMENT 設計下， INSERT 沒有給定 ID 的話，預設會跳過使用過（但是後來刪掉）的 ID。


## 驗證


實現： 4. 在 INTEGER PRIMARY KEY AUTOINCREMENT 設計下， INSERT 沒有給定 ID 的話，預設會跳過使用過（但是後來刪掉）的 ID。


1. 建一個新的資料模型，而且在主鍵使用關鍵字 AUTOINCREMENT 。

    ```sql
    CREATE TABLE EnglishVocabularyNote(
	NoteId INTEGER PRIMARY KEY AUTOINCREMENT,
	Word TEXT NOT NULL,
	MeaningInChinese TEXT NOT NULL
    );
    ```


1. 加入三筆資料。

    ```sql
    INSERT INTO EnglishVocabularyNote(Word, MeaningInChinese)
    VALUES('tweezers', '鑷子'),
    ('clothespin','洗衣夾'),
    ('clothesline', '曬衣繩');
    ```


1. 確認上述是否加入成功（可略）。

    ```sql
    SELECT * FROM EnglishVocabularyNote;
    ```


1. 刪除最後一筆資料。

    ```sql
    DELETE FROM EnglishVocabularyNote
    WHERE NoteId = 3;
    ```


1. 加入一筆新資料。

    ```sql
    INSERT INTO EnglishVocabularyNote (Word, MeaningInChinese)
    VALUES ('keychain', '鑰匙圈');
    ```


1. 查詢方才資料的 ID （預計是 4） 或 查看所有資料。

    ```sql
    SELECT * FROM EnglishVocabularyNote WHERE Word = 'keychain';
    ```

    --|NoteId|Word|MeaningInChinese
    --|------:|:-----------|:-------------
    1 |4     |keychain|	鑰匙圈


    ```sql
    SELECT * FROM EnglishVocabularyNote;
    ```

    --|NoteId|Word|MeaningInChinese
    --|------:|:-----------|:-------------
    1 |1     |tweezers   |  鑷子
    2 |2     |clothespin |	洗衣夾
    3 |4     |keychain|	鑰匙圈

---

實現： 3. 在 INTEGER PRIMARY KEY 設計下， INSERT 沒有給定 ID 的話，預設為 ROWID +1 （無論是否有加上關鍵字 AUTOINCREMENT ）。

1. 在上述操作後，再加一筆資料。

    ```sql
    INSERT INTO EnglishVocabularyNote(Word, MeaningInChinese)
    VALUES('clothesline', '曬衣繩');
    ```

1. 查看資料，預計 ID = 5。

    ```sql
    SELECT * FROM EnglishVocabularyNote;
    ```

    --|NoteId|Word|MeaningInChinese
    --|------:|:-----------|:-------------
    1 |1     |tweezers   |  鑷子
    2 |2     |clothespin |	洗衣夾
    3 |4     |keychain|	鑰匙圈
    3 |5	 |clothesline|	曬衣繩
