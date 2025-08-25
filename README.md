# goit-rdb-hw-05
## 1. Nested query in SELECT operator

```
USE mydb;

SELECT
	*,
    (SELECT customer_id FROM orders WHERE orders.id= order_details.order_id) as customer_id
FROM mydb.order_details;
```

## 2. Nested query in WHERE operator

```
USE mydb;

SELECT *
FROM order_details
WHERE 3 = (SELECT shipper_id from orders WHERE orders.id = order_details.order_id)
```

## 3. Nested query in FROM operator

```
USE mydb;

SELECT temp.order_id, AVG(temp.quantity) as average_quantity
FROM (SELECT * FROM order_details WHERE quantity > 10) as temp
GROUP BY order_id
```

## 4. Nested query in WITH operator

```
USE mydb;

WITH temp AS (
	SELECT * 
    FROM order_details
    WHERE quantity > 10
)
SELECT order_id, AVG(quantity) as average_quantity
FROM temp
GROUP BY order_id
```
