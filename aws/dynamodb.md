---
description: NoSQL database service
---

# DynamoDB

## 觀念

### Tables, Items, and Attributes <a id="HowItWorks.CoreComponents.TablesItemsAttributes"></a>

* Table: 存放資料
* Item: 具有唯一性識別的一群 attributes
  * 需有 unique identifier 或 primary key，可識別出不同的 item
  * 上限 400 KB
* attributes: 欄位
  * nested attributes: 最多 32 level

### Primary Key

* **partition key**: _simple primary key_: ，使用 1 個 attribute
  * _hash attribute_
  * 僅能為純量，string, number, or binary
* **partition key + sort key**: _composite primary key_: ，使用兩個 attribute
  * partition key 可相同，sort key 需不同
  * _range attribute_

partition key 經由 hash function 後的 output 會決定資料存放的實體位置，具有相同 partition key 的 item 會被存在一起，並依照 sort key 排序

### Secondary Indexes

* primary key 不夠用時，可建立一或多個 secondary indexes，用來 query 資料
* global secondary index: 定義不同的 primary key
  * 每個 table 最多 20 個
* local secondary index: ordering 
  * 每個 table 最多 5 個
* 每個 index 都屬於一個 table
* index 由 DynamoDB 維護
* 可指定哪些 attribute 要加入 index，key attribute 一定會被加到 index 中

### DynamoDB Streams <a id="HowItWorks.CoreComponents.Streams"></a>

可選用的功能，例如搭配 Lambda 作 trigger

1. 新增 item attributes
2. 修改前及修改後 item attributes
3. 刪除前 item attributes

## Naming Rules and Data Types <a id="HowItWorks.NamingRulesDataTypes"></a>

### Data Types <a id="HowItWorks.DataTypes"></a>

* **Scalar Types** number, string, binary, Boolean, and null
* **Document Types** 可為 nested attributes，最多 32 層
  * **List**
    * 有序
    * data type 可不同
  * **Map**
    * 無序
    * data type 可不同
* **Set Types** string set, number set, and binary set.
  * data type 需相同

## Reference

* [DynamoDB, explained](https://www.dynamodbguide.com/what-is-dynamo-db)

