# Домашнее задание к занятию «Работа с данными (DDL/DML)»

### Задание 1
1.1. Поднимите чистый инстанс MySQL версии 8.0+. Можно использовать локальный сервер или контейнер Docker.

1.2. Создайте учётную запись sys_temp. 

1.3. Выполните запрос на получение списка пользователей в базе данных. (скриншот)

1.4. Дайте все права для пользователя sys_temp. 

1.5. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)

1.6. Переподключитесь к базе данных от имени sys_temp.

Для смены типа аутентификации с sha2 используйте запрос: 
```sql
ALTER USER 'sys_temp'@'localhost' IDENTIFIED WITH mysql_native_password BY 'secret';
```
1.7. По ссылке https://downloads.mysql.com/docs/sakila-db.zip скачайте дамп базы данных.

1.8. Восстановите дамп в базу данных.

1.9 При работе в IDE сформируйте ER-диаграмму получившейся базы данных. При работе в командной строке используйте команду для получения всех таблиц базы данных. (скриншот)

*Результатом работы должны быть скриншоты обозначенных заданий, а также простыня со всеми запросами.*

---
### Ответ 1

### 1.3. Выполните запрос на получение списка пользователей в базе данных. (скриншот)
![image](https://github.com/Dk054/studies/assets/139000762/e0c1e52b-a7bb-4cdd-b0b2-8629f0f591cc)
### 1.5. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)
![image](https://github.com/Dk054/studies/assets/139000762/b67b9218-d773-4c3f-a971-9ae73105ea66)
![image](https://github.com/Dk054/studies/assets/139000762/1d4546ab-2efa-4acf-adef-9d16f9224710)
### 1.6. Переподключитесь к базе данных от имени sys_temp.
![image](https://github.com/Dk054/studies/assets/139000762/da64cf88-ac0f-44ff-b318-eec4f1a4f077)
![image](https://github.com/Dk054/studies/assets/139000762/e21daff1-7ada-43f7-ac22-629ce6c0293d)
### 1.9 При работе в IDE сформируйте ER-диаграмму получившейся базы данных. При работе в командной строке используйте команду для получения всех таблиц базы данных. (скриншот)
![image](https://github.com/Dk054/studies/assets/139000762/6fabd8d9-1021-42ed-a207-dadd89b85ec8)




---
### Задание 2
Составьте таблицу, используя любой текстовый редактор или Excel, в которой должно быть два столбца: в первом должны быть названия таблиц восстановленной базы, во втором названия первичных ключей этих таблиц. Пример: (скриншот/текст)
```
Название таблицы | Название первичного ключа
customer         | customer_id
```
### Задание 2
```
Название таблицы             | Название первичного ключа
actor                        | actor_id
actor_info                   | 
address                      | address_id
category                     | category_id
city                         | city_id
country                      | country_id
customer                     | customer_id
customer_list                | 
film                         | film_id
film_actor                   | actor_id, film_id
film_category                | film_id, category_id
film_list                    | 
film_text                    | film_id
inventory                    | inventory_id
language                     | language_id
nicer_but_slower_film_list   | 
payment                      | payment_id
rental                       | rental_id
sales_by_film_category       | 
sales_by_store               | 
staff                        | staff_id
staff_list                   | 
store                        | store_id
```

### Задание 3*
3.1. Уберите у пользователя sys_temp права на внесение, изменение и удаление данных из базы sakila.

3.2. Выполните запрос на получение списка прав для пользователя sys_temp. (скриншот)

### Ответ 3

![image](https://github.com/Dk054/studies/assets/139000762/62245e32-bb82-4c91-be9c-827f71423406)


```
mysql> REVOKE ALL PRIVILEGES, GRANT OPTION FROM 'sys_temp'@'localhost';
mysql> show grants for 'sys_temp'@'localhost';
mysql> GRANT INSERT, UPDATE, DELETE ON `sakila`.* TO 'sys_temp'@'localhost';
mysql> show grants for 'sys_temp'@'localhost';
mysql> REVOKE INSERT, UPDATE, DELETE ON `sakila`.* FROM 'sys_temp'@'localhost';
mysql> show grants for 'sys_temp'@'localhost';
```


*Результатом работы должны быть скриншоты обозначенных заданий, а также простыня со всеми запросами.*
