# goit-rdb-hw-05
## 1. Nested query in SELECT operator

```
USE mydb;

SELECT
	*,
    (SELECT customer_id FROM orders WHERE orders.id= order_details.order_id) as customer_id
FROM mydb.order_details;
```
