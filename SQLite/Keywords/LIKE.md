# LIKE


* 官方文件： [The LIKE, GLOB, REGEXP, MATCH, and extract operators](https://www.sqlite.org/lang_expr.html?fbclid=IwAR1LQSNUDnQGVPVpT4m8CvxVAJWcn-2aV0er1DLWUe8B7grUXbYToChlLQk#like)

* （含範例的）教程： [SQLite LIKE](https://www.sqlitetutorial.net/sqlite-like)


## 簡述


1. 協助篩選搜尋結果，不分英文大小寫。

   * 欲區分大小寫：[PRAGMA case_sensitive_like = boolean;](https://www.sqlite.org/pragma.html#pragma_case_sensitive_like)

   * 「不分英文大小寫」僅限於 ASCII 

      * > Important Note: SQLite only understands upper/lower case for ASCII characters by default. The LIKE operator is case sensitive by default for unicode characters that are beyond the ASCII range. For example, the expression **'a' LIKE 'A'** is TRUE but **'æ' LIKE 'Æ'** is FALSE. The ICU extension to SQLite includes an enhanced version of the LIKE operator that does case folding across all unicode characters.

1. `%` ：0 ~ many 字串。

1. `_` ：1 個字元。

1. `%` 和 `_` 可以搭配使用。

1. 如果想用 LIKE 搜尋的字串中包含 `%` 、 `_` 參見： [SQLite LIKE with ESCAPE clause](https://www.sqlitetutorial.net/sqlite-like)


## 驗證


資料庫內容：


--|NoteId|Word|MeaningInChinese
--|------:|:-----------|:-------------
1 |1 |tweezers   |  鑷子
2 |2 |clothespin |	洗衣夾
3 |3 |clothesline|	曬衣繩
3 |4 |flashlight |	手電筒
5 |5 |invoice    |	發票
6 |6 |spring     |	彈簧

---

### 實作： 1. 協助篩選搜尋結果，不分英文大小寫。


下面兩個 SQLite 句法結果相等：

```sql
SELECT * FROM EnglishVocabularyNote
WHERE Word like '%in';
```

```sql
SELECT * FROM EnglishVocabularyNote
WHERE Word like '%IN';
```

--|NoteId|Word|MeaningInChinese
--|------:|:-----------|:-------------
1 |2 |clothespin |	洗衣夾

---

### 實作： 2. `%` ：0 ~ many 字串。


```sql
SELECT * FROM EnglishVocabularyNote
WHERE Word like 'in%';
```

--|NoteId|Word|MeaningInChinese
--|------:|:-----------|:-------------
1 |5 |invoice    |	發票


```sql
SELECT * FROM EnglishVocabularyNote
WHERE Word like '%in%';
```

--|NoteId|Word|MeaningInChinese
--|------:|:-----------|:-------------
1 |2 |clothespin |	洗衣夾
2 |3 |clothesline|	曬衣繩
3 |5 |invoice    |	發票
4 |6 |spring     |	彈簧

---

### 實現： 3. `_` ：1 個字元。

5 個 `_` ，下面兩個句法結果相等：

```sql
SELECT * FROM EnglishVocabularyNote
WHERE Word like 'in_____'; 
```

```sql
SELECT * FROM EnglishVocabularyNote
WHERE Word like 'IN_____';
```

--|NoteId|Word|MeaningInChinese
--|------:|:-----------|:-------------
1 |5 |invoice    |	發票

---

### 實現： 4. `%` 和 `_` 可以搭配使用。

1 個 `%` 和 1 個 `_` 搭配：

```sql
SELECT * FROM EnglishVocabularyNote
WHERE Word like '%in_';
```

--|NoteId|Word|MeaningInChinese
--|------:|:-----------|:-------------
1 |3 |clothesline|	曬衣繩
2 |6 |spring     |	彈簧