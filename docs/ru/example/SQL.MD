### 1. Опишите структуру как бы реализовали хранения оплаты заказ

```sql
CREATE TABLE orders
(
    id INT PRIMARY KEY AUTO_INCREMENT,
    product_id INT,
    quantity INT,
    customer_email VARCHAR(255),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

```sql
CREATE TABLE payments
(
    id INT PRIMARY KEY AUTO_INCREMENT,
    order_id INT,
    amount DECIMAL(10, 2),
    payment_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    payment_status VARCHAR(50),
);
```

### 2. Нужно описать модель библиотеки.

Задание:
Есть 3 сущности: "Автор", "Книга", "Читатель". У книги может быть несколько авторов, но только один читатель.

```sql
CREATE TABLE author
(
    id     INT PRIMARY KEY AUTO_INCREMENT,
    `name` VARCHAR(255)
);

CREATE TABLE reader
(
    id     INT PRIMARY KEY AUTO_INCREMENT,
    `name` VARCHAR(255)
);

CREATE TABLE book
(
    id        INT PRIMARY KEY AUTO_INCREMENT,
    `name`    VARCHAR(255),
    id_reader INT NOT NULL,
    FOREIGN KEY (id_reader) REFERENCES reader (id) ON DELETE CASCADE
);

CREATE TABLE author_book
(
    id_book   INT NOT NULL,
    id_author INT NOT NULL,
    FOREIGN KEY (id_book) REFERENCES book (id),
    FOREIGN KEY (id_author) REFERENCES author (id)
);
```

### 3. Вывести все книги, у которых более 3 авторов

```sql
SELECT book.id, book.name
FROM book
         JOIN author_book as ab on ab.id_book = book.id
GROUP by book.id
having count(ab.id_author) > 3
```

### 4. Вывести топ-3 авторов, чьи книги читают

```sql
SELECT *
FROM book
         JOIN author_book as ab on ab.id_book = book.id
WHERE id_reader is not NULL
group by ab.id_author
order by count(ab.id_book) desc LIMIT 3
```

### 5. Что будет при выполнения запроса

```sql
START TRANSACTION;
TRUNCATE TABLE table_name;
COMMIT;
select *
from table_name;
```

Данные из таблицы будут удалены
Важно отметить, что команда TRUNCATE TABLE является автоматически коммитируемой операцией, то есть она сразу применяется
и не может быть отменена или откатена в рамках транзакции.

### 6. Транзакции
```shell
docker run --name mysql -d \
    -p 3306:3306 \
    -e MYSQL_ROOT_PASSWORD=change-me \
    --restart unless-stopped \
    mysql:8

docker exec -it mysql mysql -p
```


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

### 7. Сервис знакомств

```sql
// Сервис знакомств, есть табличка с пользователями она денормализованна до безобразия 
// есть картинки, описание "о себе", все все все что можно было впихнуть про пользователя в 1 табличку, находится в этой табличке
// так же в ней есть дата рождения в хранящаяся в 3 полях day int, month int, year int
// количество пользователей 100 000 000 распределение по возрастам - будем считать что равномерное
// на сайте нужно отразить виджет "сегодня день рождения у..." в котором нужно отображить имена 3 пользователей у которых день рождения сегодня
// * для простоты работы с датами можно допустить что у нас есть 3 функции в mysql curr_day() curr_month() curr_year(), возвращают соответсвующие инты
// необходимо составить SQL запрос

SELECT *
FROM users 
WHERE day = curr_day() AND month = curr_month()
LIMIT 3
```
### 8. Оптимизировать выполнение следующего запроса

```sql
-- Есть таблица t с набором данных 10_000_000_000, где type_id - может принимать значения от 1 до 10, даты - в интервале 5 лет
-- Нужно максимально оптимизировать выполнение следующего запроса:

    select *
    from t
    where t.created_at between '2023-01-01' and '2023-01-31'
      and t.type_id = 10;
      
-- MySql      
-- id PRIMARY - IDX(created_at, type_id) vs IDX(type_id, created_at)
-- https://edu.postgrespro.ru/qpt-13/qpt_05_bitmapscan.html
-- реплика
-- чанки
```
[Назад](../../../README.md)