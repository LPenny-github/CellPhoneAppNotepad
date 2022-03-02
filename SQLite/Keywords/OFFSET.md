# OFFSET


[The LIMIT clause](https://www.sqlite.org/lang_select.html#limitoffset)


## 簡述


1. OFFSET 意指 忽略前 M 項 row （exclude）。

   * 在做分頁結果，每頁只呈現 N 筆資料時很好用。

1. M 的規則如同先前提到 LIMIT N 的 N 。除了 N 是 include 但 M 是 exclude 。

   * [LIMIT](https://github.com/LPenny-github/CellPhoneAppNotepad/blob/main/SQLite/Keywords/LIMIT.md#%E7%B0%A1%E8%BF%B0)

   * 如果 M > 所有的搜尋結果 row 就不會有資料結果。

1. OFFSET 應於 LIMIT 語法之後。

1. LIMIT N OFFSET M 執行結果等同於 LIMIT M,N ，為避免（人眼）混淆仍建議前者語法。


## 驗證


資料庫內容：


--|NoteId|Word|MeaningInChinese
--|------:|:-----------|:-------------
1 |1 |tweezers   |  鑷子
2 |2 |clothespin |	洗衣夾
3 |3 |clothesline|	曬衣繩
4 |4 |flashlight |	手電筒

---

### 實現： 1. OFFSET 意指 忽略前 M 項 row （exclude）。


```sql
SELECT * FROM EnglishVocabularyNote
LIMIT 2 OFFSET 1
```

--|NoteId|Word|MeaningInChinese
--|------:|:-----------|:-------------
1 |2 |clothespin |	洗衣夾
2 |3 |clothesline|	曬衣繩

---

### 實現： 2. 如果 M > 所有的搜尋結果 row 就不會有資料結果。

（這個資料庫只有四筆資料）


``` sql
SELECT * FROM EnglishVocabularyNote
WHERE NoteId > 0
LIMIT 3 OFFSET 4
```


```

```

---

### 實現： 3. OFFSET 應於 LIMIT 語法之後。


1. OFFSET 置於 LIMIT 之後。

```sql
SELECT * FROM EnglishVocabularyNote
WHERE NoteId > 0
LIMIT 3 OFFSET 0
```


--|NoteId|Word|MeaningInChinese
--|------:|:-----------|:-------------
1 |1 |tweezers   |  鑷子
2 |2 |clothespin |	洗衣夾
3 |3 |clothesline|	曬衣繩


2. OFFSET 置於 LIMIT 之前的話......

```sql
SELECT * FROM EnglishVocabularyNote
WHERE NoteId > 0
OFFSET 0 LIMIT 3
```


```
Execution finished with errors.
Result: near "OFFSET": syntax error
At line 1:
SELECT * FROM EnglishVocabularyNote
WHERE NoteId > 0
OFFSET
```


3. 單獨只有 OFFSET 而沒有 LIMIT 的話......

```sql
SELECT * FROM EnglishVocabularyNote
WHERE NoteId > 0
OFFSET 0
```


```
Execution finished with errors.
Result: near "OFFSET": syntax error
At line 1:
SELECT * FROM EnglishVocabularyNote
WHERE NoteId > 0
OFFSET
```

---

## 實現： 4. LIMIT N OFFSET M 執行結果等同於 LIMIT M,N ，為避免（人眼）混淆仍建議前者語法。


前項語法：

```sql
SELECT * FROM EnglishVocabularyNote
WHERE NoteId > 0
LIMIT 3 OFFSET 0
```

結果等價：

```sql
SELECT * FROM EnglishVocabularyNote
WHERE NoteId > 0
LIMIT 0,3
```


--|NoteId|Word|MeaningInChinese
--|------:|:-----------|:-------------
1 |1 |tweezers   |  鑷子
2 |2 |clothespin |	洗衣夾
3 |3 |clothesline|	曬衣繩
