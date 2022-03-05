# RENAME


* 官方文件： [2. ALTER TABLE RENAME](https://www.sqlite.org/lang_altertable.html)

* 教程： [SQLite ALTER TABLE](https://www.sqlitetutorial.net/sqlite-alter-table)


## 簡述


1. RENAME 關鍵字用在改名，可以用來改資料表的名稱或是欄位名稱。


## 驗證


### 實作： 1. RENAME 關鍵字用在改名，可以用來改資料表的名稱或是欄位名稱。


1. 製作一個新的資料表。


    ```sql
    CREATE TABLE Students(
    Id INTEGER PRIMARY KEY,
    Name TEXT
    );
    ```


1. 資料表改名。


    ```sql
    ALTER TABLE Students RENAME TO Teachers;
    ```


1. 欄位改名。


    ```sql
    ALTER TABLE Teachers 
    RENAME COLUMN Id TO TeacherId;
    ```


實作的結果可以用 Browse Data 驗證，不加任何資料也可以改名。