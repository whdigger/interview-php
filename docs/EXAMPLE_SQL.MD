docker run --name mysql -d \
    -p 3306:3306 \
    -e MYSQL_ROOT_PASSWORD=change-me \
    --restart unless-stopped \
    mysql:8

docker exec -it mysql mysql -p


```sql

CREATE DATABASE tr;
USE tr;
DROP TABLE IF EXISTS Table1;
CREATE TABLE Table1 (Id INT PRIMARY KEY AUTO_INCREMENT, Value INT);
INSERT INTO Table1 (Value) VALUES(1);
```

```sql
START TRANSACTION;
DECLARE @Value INT;
SELECT @Value = Value FROM Table1 WHERE Id = 1;
SELECT SLEEP(8);
UPDATE Table1 SET Value = @Value + 5 WHERE Id = 1;
COMMIT;

SELECT Value FROM Table1 WHERE Id = 1;
```

```sql
START TRANSACTION;

DECLARE @Value INT;
SELECT @Value = Value FROM Table1 WHERE Id = 1;
UPDATE Table1 SET Value = @Value + 7 WHERE Id = 1;

COMMIT;

SELECT Value FROM Table1 WHERE Id = 1;
```