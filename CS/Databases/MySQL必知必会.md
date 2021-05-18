# MySQL 必知必会

《MySQL 必知必会》是一本入门书籍

<!--ts-->
* [MySQL 必知必会](#mysql-必知必会)
   * [1. 了解 SQL](#1-了解-sql)
      * [1.1 数据库基础](#11-数据库基础)
      * [1.2 SQL](#12-sql)
   * [2. MySQL 简介](#2-mysql-简介)
      * [2.1 什么是 MySQL](#21-什么是-mysql)
   * [3. 使用 MySQL](#3-使用-mysql)
      * [3.1 连接](#31-连接)
      * [3.2 选择数据库](#32-选择数据库)
      * [3.3 了解数据库和表](#33-了解数据库和表)
   * [4 检索数据](#4-检索数据)
      * [4.1 SELECT 语句](#41-select-语句)
      * [4.2 检索单个列](#42-检索单个列)
      * [4.3 检索多个列](#43-检索多个列)
      * [4.4 检索所有列](#44-检索所有列)
      * [4.5 检索不同的行](#45-检索不同的行)
      * [4.6 限制结果](#46-限制结果)
      * [4.7 使用完全限定的表名/列名](#47-使用完全限定的表名列名)
   * [5 排序检索数据](#排序检索数据)
      * [5.1 排序数据](#51-排序数据)
      * [5.2 按多个列排序](#52-按多个列排序)
      * [5.3 指定排序方向](#53-指定排序方向)
   * [6. 过滤数据](#6-过滤数据)
      * [6.1 使用 WHERE 子句](#61-使用-where-子句)
      * [6.2 WHERE 子句操作符](#62-where-子句操作符)
   * [7 数据过滤](#7-数据过滤)
      * [7.1 组合 WHERE 子句](#71-组合-where-子句)
      * [7.2 IN 操作符](#72-in-操作符)
      * [7.3 NOT 操作符](#73-not-操作符)
   * [8 用通配符进行过滤](#8-用通配符进行过滤)
      * [8.1 LIKE 操作符](#81-like-操作符)
      * [8.2 使用通配符技巧](#82-使用通配符技巧)
   * [9 正则表达式](#9-正则表达式)
   * [10 创建计算字段](#10-创建计算字段)
      * [10.1 计算字段](#101-计算字段)
      * [10.2 拼接字段](#102-拼接字段)
      * [10.3 执行算术运算](#103-执行算术运算)
   * [11 使用数据处理函数](#11-使用数据处理函数)
      * [11.1 函数](#111-函数)
      * [11.2 使用函数](#112-使用函数)
      * [12 汇总数据](#12-汇总数据)
      * [12.1 聚集函数](#121-聚集函数)
      * [12.2 聚合不同值](#122-聚合不同值)
      * [12.3 组合聚合函数](#123-组合聚合函数)

<!-- Added by: tx-deepocean, at: 2021年 05月 18日 星期二 18:48:42 CST -->

<!--te-->
## 1. 了解 SQL

### 1.1 数据库基础

**数据库(database)** 是保存有组织的数据的容器（通常是一个文件或一组文件）

**表(table)** 是某种特定类型数据的结构化清单

**主键(primary key)** 一列， 其值能够唯一区分表中的每一行。

### 1.2 SQL

**SQL(Structured Query Language)** 结构化查询语言

- 数据库无关
- 简单易学， 官架子不多
- 支持非常复杂和高级的数据库操作

## 2. MySQL 简介

### 2.1 什么是 MySQL

MySQL 是一种 DBMS(数据库管理系统), 有以下特点:

- 开源
- 高性能
- 可信赖
- 简单

MySQL 各版本介绍

- 4 InnoDB引擎， 事务， 并， 改进全文本走索等
- 4.1 增加函数库， 子查询， 集成帮助等
- 5 存储过程， 触发器， 游标， 视图等
- 8 TODO

## 3. 使用 MySQL

### 3.1 连接

连接4要素：

- 主机名(ip/计算机名)
- 端口
- 用户名
- 密码(口令)

### 3.2 选择数据库

`USE <database>;`

### 3.3 了解数据库和表

- `SHOW DATABASES;` // 返回可用数据库的列表
- `SHOW TABLES;` // 选中数据库的表的列表
- `SHOW COLUMNS FROM user;` == `DESCRIBE user;` == `DESC user;` // 表结构， 每个字段的名称， 数据类型， 约束等
- `SHOW STATUS；` // 显示服务器状态信息
- `SHOW CREATE DATABASE;` 和 `SHOW CREATE TABLE;` // 分别用来显示创
建特定数据库或表的MySQL语句
- `SHOW GRANTS`  // 用来显示授予用户(所有用户或特定用户)的安
全权限
- `SHOW ERRORS` 和 `SHOW WARNINGS` // 用来显示服务器错误或警告消息

## 4 检索数据

### 4.1 SELECT 语句

- SQL语句 不区分大小写， 但是一般将 SQL 关键字大写， 对所有列名和表名使用小写。

### 4.2 检索单个列

`SELECT name FROM user;`

### 4.3 检索多个列

用逗号(,)分隔， 注意最后一个列名后不能加逗号

`SELECT name, age FROM user;`

### 4.4 检索所有列

使用星号(*)通配符匹配

`SELECT * FROM user;`

### 4.5 检索不同的行

使用 DISTINCT 关键字修饰某一列名来返回唯一的值

`SELECT DISTINCT age FROM user;`

### 4.6 限制结果

使用 LIMIT 子句, LIMIT 3, 4 表示从行3开始的4行， 注意第一行为0， 若行数不够时， 则只返回能返回的那么多行。

### 4.7 使用完全限定的表名/列名

`SELECT user.name FROM test.user;`  // 在 test 数据库中的 user 表查找 user 的姓名

## 5 排序检索数据

### 5.1 排序数据

使用 **ORDER BY** 关键字

`SELECT name FROM user ORDER BY age;`  // ORDER BY 子句可以使用非检索的列进行排序

### 5.2 按多个列排序

`SELECT id, name FROM user ORDER BY id, name;` // 指定列名，列名之间用逗号分隔

### 5.3 指定排序方向

默认是**ASC(升序)**， **DESC**为降序

`SELECT id, name FROM user ORDER BY id DESC, name;`  // DESC 只用来修饰前面的列名

## 6. 过滤数据

### 6.1 使用 WHERE 子句

`SELECT name FROM user WHERE name = 'Alice';`  // WHERE 子句在表名之后给出

`SELECT name FROM user WHERE name = 'Bob' ORDER BY id;` // 同时使用 WHERE 和 ORDER BY 时， ORDER BY 位于 WHERE 之后

### 6.2 WHERE 子句操作符

| 操作符 | 说明 |
| --- | --- |
| = | 等于 |
| <> | 不等于 |
| != | 不等于 |
| < | 小于 |
| <= | 小于等于 |
| > | 大于 |
| >= | 大于等于 |
| BETWEEN a and b | 指定a和b之间 |

空值(NULL)检查时， 使用 `IS`

## 7 数据过滤

### 7.1 组合 WHERE 子句

使用 `AND` 和 `OR` 操作符， `AND` 优先级较高， 组合使用时建议使用圆括号指明顺序， 消除歧义

### 7.2 IN 操作符

`SELECT prod_name, prod_price FROM products WHERE vend_id IN (1002, 1003) ORDER BY prod_name;`

`IN` 和 `OR` 的功能相同， 但有以下优点:

- 更长的筛选时， `IN` 更直观
- `IN` 更快
- `IN` 可以包含其他　`SELECT` 语句

### 7.3 NOT 操作符

`NOT` 的操作符在复杂语句中很有用

## 8 用通配符进行过滤

### 8.1 LIKE 操作符

通配符 | 说明 | 注意
--- | --- | ---
% | 任意字符出现任意次数 | 区分大小写
_ | 单个任意字符 |

### 8.2 使用通配符技巧

- 不要过度使用通配符。 如果其他操作符能达到相同的目的,应该
使用其他操作符。
- 在确实需要使用通配符时,除非绝对有必要,否则不要把它们用
在搜索模式的开始处。把通配符置于搜索模式的开始处,搜索起
来是最慢的。
- 仔细注意通配符的位置。如果放错地方,可能不会返回想要的数据。

## 9 正则表达式

使用 `REGEXP` 关键字

字符 | 说明 | 示例
--- | --- | ---
. | 匹配任意一个字符 | `SELECT prod_name FROM products WHERE prod_name REGEXP '.000' ORDER BY prod_name;`
\| | or | `SELECT prod_name FROM products WHERE prod_name REGEXP '1000|2000' ORDER BY prod_name;`
[] | 匹配几个字符之一 | `SELECT prod_name FROM products WHERE prod_name REGEXP '[123] Ton' ORDER BY prod_name;`
- | 范围匹配 | [0-9] [a-z]
* | 0个或多个匹配 |
+ | 1个或多个匹配(等于{1,}) |
? | 0个或1个匹配(等于{0,1}) |
{n} | 指定树木的匹配 |
{n,} | 不少于指定数目的匹配 |
{n,m} | 匹配数目的范围(m不超过255) |
^ | 文本的开始 |
$ | 文本的结尾 |
[[:<:]] | 词的开始 |
[[:>:]] | 词的结尾 |

## 10 创建计算字段

### 10.1 计算字段

**字段(field)** 基本与列(column)的意思相同， 不过数据库列一般称为列， 而字段通常用于在计算字段的连接上。

### 10.2 拼接字段

vendors 表包含供应商名和位置信息。假如要生成一个供应商报表,
需要在供应商的名字中按照 name(location) 这样的格式列出供应商的位
置。

```
// MySQL 中使用 Concat() 函数实现拼接, 并使用`AS`关键字赋予别名
SELECT Concat(vend_name, '(', vend_country, ')') AS vend_title FROM vendors ORDER BY vend_name;`
```

### 10.3 执行算术运算

```
SELECT prod_id quantity, item_price, quantity*item_price AS expanded_price
FROM orderitems
WHERE order_num = 20005;
```

## 11 使用数据处理函数

### 11.1 函数

SQL 支持使用函数处理数据。 但是函数没有SQL语句的可移植性强。

### 11.2 使用函数

- [文本处理函数](https://dev.mysql.com/doc/refman/8.0/en/string-functions.html)
- [日期和时间处理函数](https://dev.mysql.com/doc/refman/8.0/en/date-and-time-functions.html)
- [数值处理函数](https://dev.mysql.com/doc/refman/8.0/en/numeric-functions.html)
- [其他参考](https://dev.mysql.com/doc/refman/8.0/en/functions.html)

### 12 汇总数据

### 12.1 聚集函数

函数 | 说明 | 注意
--- | --- | ---
AVG() | 平均值 | AVG()只用于单列， 并忽略 值为NULL的行
COUNT() | 行数 | COUNT(*)不忽略 NULL, COUNT(column)忽略 NULL
MAX() | 最大值 | MAX() 不仅可以用于数值和日期， 也可用于文本列中的最大值, 并忽略 NULL
MIN() | 最小值 | 同MAX()
SUM() | 列之和 | 

### 12.2 聚合不同值

以上5个聚合函数都可以如下使用:

- 对所有的行执行计算,指定 ALL 参数或不给参数(因为 ALL 是默认
行为);
- 只包含不同的值,指定 DISTINCT 参数。

### 12.3 组合聚合函数

```SQL
SELECT COUNT(*) AS num_items,
       MIN(prod_price) AS price_min,
       MAX(prod_price) AS price_max,
       AVG(prod_price) AS price_avg
FROM products;
```
