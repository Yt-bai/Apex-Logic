# SQL JOIN

<img width="729" height="579" alt="Image" src="https://github.com/user-attachments/assets/f6e13f79-8788-4f81-bad4-3a1db170cd98" />

| 类型 | 描述 |
|------|------|
| INNER JOIN | 返回两个表中满足连接条件的记录（交集）。 |
| LEFT JOIN | 返回左表中的所有记录，即使右表中没有匹配的记录（保留左表）。 |
| RIGHT JOIN | 返回右表中的所有记录，即使左表中没有匹配的记录（保留右表）。 |
| FULL OUTER JOIN | 返回两个表的并集，包含匹配和不匹配的记录。 |
| CROSS JOIN | 返回两个表的笛卡尔积，每条左表记录与每条右表记录进行组合。 |
| SELF JOIN | 将一个表与自身连接。 |
| NATURAL JOIN | 基于同名字段自动匹配连接的表。 |

*比如：*

### *表1：Customers*

| CustomerID | Name |
|------------|------|
| 1 | Alice |
| 2 | Bob |
| 3 | Charlie |

### *表2：Orders*

| OrderID | CustomerID | Product |
|---------|------------|---------|
| 101 | 1 | Laptop |
| 102 | 2 | Phone |
| 103 | 4 | Tablet |

### *结果对比*

| JOIN 类型 | 结果 |
|-----------|------|
| INNER JOIN | 返回两个表中匹配的记录。在给定的例子中，只有 CustomerID 为 1 和 2 的记录在两个表中都有匹配，所以只会返回这些记录。 |
| LEFT JOIN | 返回左表（Customers）中的所有记录，即使右表（Orders）中没有匹配记录。对于左表中没有匹配的右表记录，结果中的右表字段为 `NULL`。在例子中，CustomerID 为 3 的记录在右表中没有匹配，所以其对应的 Product 将为 `NULL`。 |
| RIGHT JOIN | 返回右表（Orders）中的所有记录，即使左表（Customers）中没有匹配记录。对于右表中没有匹配的左表记录，结果中的左表字段为 `NULL`。在例子中，OrderID 为 103 的记录在左表中没有匹配，所以其对应的 Name 将为 `NULL`。 |
| FULL OUTER JOIN | 返回两个表中的所有记录，无论它们是否匹配。如果某个表中没有匹配的记录，那么该表的字段将为 `NULL`。在例子中，CustomerID 为 3 和 OrderID 为 103 的记录将分别在对方的表中显示为 `NULL`。 |
| CROSS JOIN | 返回两个表的笛卡尔积，即左表中的每一行与右表中的每一行组合。在例子中，每个顾客都将与每个订单组合，产生多个结果。 |
| SELF JOIN | 表与其自身进行连接。这通常用于查询表中相互关联的记录，比如员工与其经理之间的关系。 |

---

# UNION()
联接两个SELECT查询返回的结果，合并为一个结果集。

*去重合并：*
```text
SELECT 列1,列2,列3
FROM 表1
UNION
SELECT 列1,列2,列3
FROM 表2;
```
*不去重合并：*
```text
SELECT 列1,列2,列3
FROM 表1
UNION ALL
SELECT 列1,列2,列3
FROM 表2;
```
