# GROUP BY() 做分组统计
通常和聚合函数一起用。

*使用结构:**先按照列1做分组(GROUP BY),再按照聚合函数对列2做统计计算，最终显示的是列1和新字段列名组成的表，列1的具体值对应通过聚合函数对列2做计算后的具体值。***
```text
SELECT 列1, 聚合函数(列2) AS 新字段列名
FROM 表名
WHERE 条件
GROUP BY 列1;
```
*统计 access_log 各个 site_id 的访问量*
```text
SELECT site_id, SUM(count) AS total_count
FROM access_log
GROUP BY site_id;
```
*注：如果access_log表是Web数据库中的一张表，那么要写access_log.count*

---

# HAVING() 筛选分组后的数据
由于WHERE不能和聚合函数一起使用，**即，WHERE SUM() > 100 这种写法是错误的！** 

因此，需要一个能够和聚合函数一起使用的HAVING语法。

WHERE和HAVING在功能上的最主要区别是，WHERE是分组前作为分组条件的筛选，HAVING是分组后，对已经筛选出的各组数据进行进一步筛选。

*简单使用方式。**最终显示的结果集是列1和新字段列名中满足HAVING 条件的那些记录。***
```text
SELECT 列1, 聚合函数(列2) AS 新字段列名
FROM 表名
GROUP BY 列1
HAVING 条件;
```
- 列1：要检索的列。
- 聚合函数(列2)：一个聚合函数，例如SUM、COUNT、AVG等，应用于column2的值。
- 表名：要从中检索数据的表。
- GROUP BY 列1：根据column1列的值对数据进行分组。
- HAVING 条件：一个条件，用于筛选分组的结果。只有满足条件的分组会包含在结果集中。

---

# 总结
```text
SELECT ...
FROM ...
WHERE ...
GROUP BY ...
HAVING ...
ORDER BY ...
```
**先从表中筛选取列，然后分组，然后筛选组，最后排序。**

- **WHERE：过滤原始行**
- **HAVING：过滤分组后的结果**

---

执行顺序：
**FROM -> WHERE -> GROUP BY -> HAVING -> SELECT -> ORDER BY**
**取表 -> 筛选原始行 -> 分组 -> 筛选组 -> 选择 -> 排序**


