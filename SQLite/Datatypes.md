# Datatypes in SQLite


SQLite 使用的是 動態的、弱型別。

大體而言，你可以為欄位設定 **建議型別** ，但程式在執行時會依照你給予的資料內容本身與 **建議型別** ，作儲存型別的判定。

不過自版本 3.37.0 (2021-11-27) 起，SQLite 也提供強制型別的資料設定方式：

  * [STRICT Tables](https://www.sqlite.org/stricttables.html)


Storage Classes 比 Type Affinity 的定義內容更廣泛。


## Storage Classes


每個值儲存在 SQLite 資料庫裡的類別。

> Each value stored in an SQLite database (or manipulated by the database engine) has one of the following storage classes

1. NULL. The value is a NULL value.

1. INTEGER. The value is a signed integer, stored in 0, 1, 2, 3, 4, 6, or 8 bytes depending on the magnitude of the value.

1. REAL. The value is a floating point value, stored as an 8-byte IEEE floating point number.

1. TEXT. The value is a text string, stored using the database encoding (UTF-8, UTF-16BE or UTF-16LE).

1. BLOB. The value is a blob of data, stored exactly as it was input.


## Type Affinity


建立（CREATE TABLE） 給予每個欄位 建議的型別親和性 。

> The type affinity of a column is the recommended type for data stored in that column. The important idea here is that the type is recommended, not required. Any column can still store any type of data. It is just that some columns, given the choice, will prefer to use one storage class over another. The preferred storage class for a column is called its "affinity".


以下是型別親和性列表和舉例：


1. TEXT：字串

1. NUMERIC：

1. INTEGER：整數

1. REAL：浮點數

1. BLOB：一堆資料集合
 
   > (Historical note: The "BLOB" type affinity used to be called "NONE". But that term was easy to confuse with "no affinity" and so it was renamed.)


## 參考資料

* Datatypes In SQLite

  * https://www.sqlite.org/datatype3.html

* 資料類型

  * https://docs.microsoft.com/zh-tw/dotnet/standard/data/sqlite/types