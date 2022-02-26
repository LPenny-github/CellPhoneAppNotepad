# LIMIT


> The LIMIT clause is used to place an upper bound on the number of rows returned by the entire SELECT statement.

[The LIMIT clause](https://www.sqlite.org/lang_select.html#limitoffset)


## 簡述


1. LIMIT 之後的數字代表 SELECT 結果 row 的個數 的顯示上限。上限指 包括 / include。

1. 如果 LIMIT 之後的數字不能轉換成整數，會出現錯誤。

1. 如果 LIMIT 之後的數字是負數，那 LIMIT 等同虛設。

1. 如果 SELECT 結果 row 的個數 小於 LIMIT 之後的數字，則將回傳全部 SELECT 結果 row 的個數。


## 驗證


資料庫內容：


--|NoteId|Word|MeaningInChinese
--|------:|:-----------|:-------------
1 |1 |tweezers   |  鑷子
2 |2 |clothespin |	洗衣夾
3 |3 |clothesline|	曬衣繩
3 |4 |flashlight |	手電筒

---

### 實現： 1. LIMIT 之後的數字代表 SELECT 結果 row 的個數 的顯示上限。


```sql
SELECT * FROM EnglishVocabularyNote LIMIT 2;
```

--|NoteId|Word|MeaningInChinese
--|------:|:-----------|:-------------
1 |1 |tweezers   |  鑷子
2 |2 |clothespin |	洗衣夾

---

### 實現： 2. 如果 LIMIT 之後的數字不能轉換成整數，會出現錯誤。


```sql
SELECT * FROM EnglishVocabularyNote LIMIT $;
```

```txt
Execution finished with errors.
Result: unrecognized token: "$"
At line 1:
SELECT * FROM EnglishVocabularyNote LIMIT
```

---

### 實現： 3. 如果 LIMIT 之後的數字是負數，那 LIMIT 等同虛設。


```sql
SELECT * FROM EnglishVocabularyNote LIMIT -1;
```

--|NoteId|Word|MeaningInChinese
--|------:|:-----------|:-------------
1 |1 |tweezers   |  鑷子
2 |2 |clothespin |	洗衣夾
3 |3 |clothesline|	曬衣繩
3 |4 |flashlight |	手電筒

---

### 實現： 4. 如果 SELECT 結果 row 的個數 小於 LIMIT 之後的數字，則將回傳全部 SELECT 結果 row 的個數。


```sql
SELECT * FROM EnglishVocabularyNote LIMIT 1000;
```

--|NoteId|Word|MeaningInChinese
--|------:|:-----------|:-------------
1 |1 |tweezers   |  鑷子
2 |2 |clothespin |	洗衣夾
3 |3 |clothesline|	曬衣繩
3 |4 |flashlight |	手電筒