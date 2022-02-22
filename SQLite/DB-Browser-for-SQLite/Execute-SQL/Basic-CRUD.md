# Basic CRUD


---|Create|Read|Update|Delete|
---|:---:|:---:|:---:|:---:|
table |✔ |✔   |     |     |
column|  |     |     |     |
row   |✔ |✔   |     |✔   |


---
---

## table

### C


```sql
  CREATE TABLE EnglishVocabularyNote(
	NoteId INTEGER,
	Word TEXT NOT NULL,
	MeaningInChinese TEXT NOT NULL,
	PRIMARY KEY(NoteId)
    )
```


### R


```sql
  SELECT * FROM EnglishVocabularyNote
```  


---

## row   

### C


```sql
  INSERT INTO EnglishVocabularyNote (NoteId, Word, MeaningInChinese)
  VALUES (4, 'keychain', '鑰匙圈')
```


### R


```sql
  SELECT * FROM EnglishVocabularyNote WHERE NoteId = 4
```


### D

```sql
  DELETE FROM EnglishVocabularyNote
  WHERE NoteId = 4
```
