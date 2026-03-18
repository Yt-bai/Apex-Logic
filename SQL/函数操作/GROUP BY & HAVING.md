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

# HAVING() 
