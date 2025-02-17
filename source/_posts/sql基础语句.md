---
title: SqlCrud语句
date: 2025-02-10 21:59:51
tags: sql学习
toc: true
---

[toc]

### 基础语句

#### create/alter table

Create table:

```sqlite
CREATE TABLE departments (
    id INTEGER PRIMARY KEY,
    department_name TEXT NOT NULL
);

CREATE TABLE employees (
    id INTEGER PRIMARY KEY,
    name TEXT NOT NULL,
    department_id INTEGER,
    CONSTRAINT fk_departments
    FOREIGN KEY (department_id)
    REFERENCES departments(id)
);
```

alter table:

```sql
/* rename */
ALTER TABLE employees
RENAME TO contractors;

ALTER TABLE contractors
RENAME COLUMN salary TO invoice;

/*add and drop*/

ALTER TABLE contractors
ADD COLUMN job_title TEXT;

ALTER TABLE contractors
DROP COLUMN is_manager;
```

#### insert

```sql
INSERT INTO employees(id, name, title)
VALUES (1, 'Allan', 'Engineer');
```

#### delete

```sql
DELETE FROM employees
    WHERE id = 251;
```

#### update

```sql
UPDATE employees
SET job_title = 'Backend Engineer', salary = 150000
WHERE id = 251;
```

### Queries语句

#### where条件

where语句后可以跟随条件

```sql
SELECT name FROM users WHERE power_level >= 9000;
SELECT name FROM users WHERE first_name IS NULL;
```

#### AS

```sql
SELECT employee_id AS id, employee_name AS name
FROM employees;
```

#### IIF

```sql
SELECT quantity,
    IIF(quantity < 10, 'Order more', 'In Stock') AS directive
    FROM products;
 /* quantitiy<10 = true,则新建的directive column为Order more,否则为 In Stock */
```

#### between

```sql
SELECT employee_name, salary
FROM employees
WHERE salary BETWEEN 30000 and 60000;

SELECT product_name, quantity
FROM products
WHERE quantity NOT BETWEEN 20 and 100;
```

#### distinct

查找非重复的值

```sql
SELECT DISTINCT previous_company
    FROM employees;
```

#### and

```sql
SELECT product_name, quantity, shipment_status
    FROM products
    WHERE shipment_status = 'pending'
    AND quantity BETWEEN 0 and 10;
```

#### or

```sql
SELECT product_name, quantity, shipment_status
    FROM products
    WHERE shipment_status = 'out of stock'
    OR quantity BETWEEN 10 and 100;
```

#### in

```sql
SELECT product_name, shipment_status
    FROM products
    WHERE shipment_status IN ('shipped', 'preparing', 'out of stock');
    
 /* 其实等于执行了以下语句*/
 SELECT product_name, shipment_status
    FROM products
    WHERE shipment_status = 'shipped'
        OR shipment_status = 'preparing'
        OR shipment_status = 'out of stock';
```

#### like

```sql
/* starts with banana */
SELECT * FROM products
WHERE product_name LIKE 'banana%';

/* ends with banana*/
SELECT * FROM products
WHERE product_name LIKE '%banana';

/* contains banana */

SELECT * FROM products
WHERE product_name LIKE '%banana%';

/*占位，有几个下划线就表示有几个待匹配字符，如下则表示4个字符且结尾为oot*/
SELECT * FROM products
    WHERE product_name LIKE '_oot';
    
 
```

