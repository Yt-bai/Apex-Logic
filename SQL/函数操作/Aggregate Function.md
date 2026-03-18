<img width="785" height="340" alt="image" src="https://github.com/user-attachments/assets/aa2fc747-9aaa-4ed4-9df7-a4b9045c566e" /># AVG() 求列平均值
```text
SELECT AVG(column_name) FROM table_name;
```
*取count列的平均值*

```text
SELECT AVG(count) AS Countavg FROM Websites;
```
*取点击量高于平均值的site_id和点击量*

```text
SELECT site_id, count FROM Websites
WHERE count > (SELECT AVG(count) FROM Websites);
```
<img width="785" height="340" alt="image" src="https://github.com/user-attachments/assets/a7e8ea9f-c176-4cd6-882b-aac42b8be139" />

---

# COUNT() 求某列中满足指定条件的信息有几条
*计算 "access_log" 表中 "site_id"=3 的点击量数据有几条*
```text
SELECT COUNT(count) AS nums FROM access_log
WHERE site_id=3;
```
*计算 "access_log" 表中总记录数*
```text
SELECT COUNT(*) AS nums FROM access_log;
```
*计算 "access_log" 表中不同 site_id 的记录数*
```text
SELECT COUNT(DISTINCT site_id) AS nums FROM access_log;
```
**总结**：COUNT(column_name)返回column_name中非NULL的条数、COUNT(*)返回表中所有记录数包括NULL行、COUNT(DISTINCT column_name)返回非重复非NULL记录数。

---

# FIRST() 指定列中第一条记录的值
只有MS Access支持FIRST()。

*在My SQL中，选出Website表中成绩最好的学生姓名*
```text
SELECT stu AS BestStu FROM Websites
ORDER BY grades DESC
LIMIT 1;
```

---

# LAST() 指定列中最后一条记录的值
同样只有MS Access支持。

*在My SQL中，找最低点击量的site_id*
```text
SELECT site_id FROM Websites
ORDER BY count ASC
LIMIT 1;
```

---

# MAX() & MIN()
*从 "Websites" 表的 "alexa" 列获取最大值*
```text
SELECT MAX(alexa) AS Max_alexa FROM Websites;
```

---

# SUM() 计算总数
查找 "access_log" 表的 "count" 字段的总数。

```text
SELECT SUM(count) AS total FROM access_log;
```

---
