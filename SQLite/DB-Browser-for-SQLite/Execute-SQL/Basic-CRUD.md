# Basic CRUD


---|Create|Read|Update|Delete|
---|:---:|:---:|:---:|:---:|
table |✔ |✔   |     |✔    |
column|✔ |✔   |✔   |✔   |
row   |✔ |✔   |✔   |✔   |


---

* **注意**

  * 每一句結束應該加上 `;` ，但在 DB Browser 的 Execute SQL 介面中，操作一行指令時可以省略 `;` 。

  * 在 DB Browser 的 Execute SQL 介面中，操作兩行指令，至少前面那句結尾要有 `;` ，否則將出現錯誤。

---

## table

### C


```sql
  CREATE TABLE EnglishVocabularyNote(
	NoteId INTEGER,
	Word TEXT NOT NULL,
	MeaningInChinese TEXT NOT NULL,
	PRIMARY KEY(NoteId)
  );
```

或者

```sql
  CREATE TABLE EnglishVocabularyNote(
	NoteId INTEGER PRIMARY KEY,
	Word TEXT NOT NULL,
	MeaningInChinese TEXT NOT NULL
  );
```


### R


```sql
  SELECT * FROM EnglishVocabularyNote;
```  


### D


```sql
  DROP TABLE EnglishVocabularyNote;
```


---

## column

### C


**注意** ：在 DB Browser 的 Execute SQL 介面中，下面兩個句法的結果相同（差別於有沒有加上 `COLUMN` ，在 DROP COLUMN 時也會有同樣的狀況。由於官方文件的語法上有加上 `COLUMN` ，建議還是要有 `COLUMN` 。


```sql
  ALTER TABLE EnglishVocabularyNote
  ADD COLUMN ReviewCount INTEGER;
```

或：

```sql
  ALTER TABLE EnglishVocabularyNote
  ADD ReviewCount INTEGER;
```


### R


```sql
  SELECT Word FROM EnglishVocabularyNote;
```


### U


```sql
  UPDATE EnglishVocabularyNote
  SET MeaningInChinese = '';
```


### D


```sql
  ALTER TABLE EnglishVocabularyNote
  DROP COLUMN ReviewCount;
```


---

## row   

### C


```sql
  INSERT INTO EnglishVocabularyNote (NoteId, Word, MeaningInChinese)
  VALUES (4, 'keychain', '鑰匙圈');
```


### R


```sql
  SELECT * FROM EnglishVocabularyNote WHERE NoteId = 4;
```


### U


```sql
  UPDATE EnglishVocabularyNote
  SET Word = 'mouse', MeaningInChinese = '滑鼠'
  WHERE NoteId = 3;
```


### D


```sql
  DELETE FROM EnglishVocabularyNote
  WHERE NoteId = 4;
```
