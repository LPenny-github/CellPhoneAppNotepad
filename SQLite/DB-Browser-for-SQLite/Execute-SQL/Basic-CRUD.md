# Basic CRUD


---|Create|Read|Update|Delete|
---|:---:|:---:|:---:|:---:|
table |✔ |✔   |     |     |
column|  |     |     |     |
row   |✔ |✔   |     |✔   |


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


### R


```sql
  SELECT * FROM EnglishVocabularyNote;
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


### D

```sql
  DELETE FROM EnglishVocabularyNote
  WHERE NoteId = 4;
```
