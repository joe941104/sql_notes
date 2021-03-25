## 创建database

1. database is just a brunch of tables. 

2. ```sql
   CREATE TABLE tablename
   ( column_name data_type,
     column_name data_type
   );
   ```

   ​       创建表格

   例子：

   ```sql
   CREATE TABLE cats( name VARCHAR(100)，
                      age   INT );
   ```

   想看创建的表格

   ```sql
   SHOW TABLES;
   ```

   看表格里面的内容

   ```sql
   show columns from cats;
   ```

   OR

   ```sql
   DESC cats;
   ```

   删除表格

   ```sql
   DROP TABLE <table name>
   ```

   插入数据

   ```sql
   INSERT INTO cats(name,  age)
   VALUES ('Jetson',7);
   ```

   插入多个数据

   ```sql
   INSERT INTO cats(name, age)
   VALUES ('lalal',10),
   			('bababa',9),
   			('hahaha',10d
   ```

   SQL WARNING

   想看warning, 怎么办

   ``` sql
   SHOW WARNINGS;
   ```

   如果创建的时候不想要NULL

   ```sql
   CREATE TABLE cat2(
   								name VARCHAR(100) NOT NULL，
   								age  INT NOT NULL);
   ```

   关于DEFAULT VAULE

   ```sql
   CREATE TABLE cats3(
   									name VARCHAR(30) DEFAULT 'unnamed',
   									age  INT DEFAULT 99);
   ```

   关于select 

   ```mysql
   select * from cats where age=4;
   ```

   Distinct 

   ```mysql
   select distinct * from ...
   ```

   Order by

   ```mysql
   select author_lname from books order by author_lname
   ```

   limit

   ```mysql
   select author_lname from books order by author_lname desc limit 5;
   ```

   或者

   ```mysql
   select author_lname from books order by author_lname desc limit 0,5;
   其中0是staring point, 5是end point
   ```

   Like 

   ```mysql
   select * from books where author_fname LIKE '%da%'
   ```

   

   ## Primary Key and foreign key

   ### Primary Key

   1. PK is unique identifier

   2. 关于PK

      ```sql
   CREATE TABLE unique_cats(cat_id INT NOT NULL, name VARCHAR(100), age INT, primary KEY(cat_id));
      ```

   3. 如果想让ID 自动增加怎么办 (AUTO_INCREMENT)
   
      ```sql
   CREATE TABLE unique_cats(cat_id INT NOT NULL AUTO_INCREMENT, name VARCHAR(100), age INT, primary KEY(cat_id));
      ```

## Update Database

```sql
UPDATE cats SET breed = 'Shorthair' WHERE breed = 'Tabby';
```

## delete database

```sql
DELETE FROM cats WHERE name = 'egg';
```

### Delete 所有的东西

```sql
DELETE FROM cats;
```

## String Function

### conact(连接在一起)

``` sql
CONCAT(column, another column);

SELECT CONCAT(Column, another Column) from books;
```

### CONACT_WS (conact with separator)

```sql
SELECT CONACT_WS ('-',title, author_fname, author_lname) from books;
```

### SUBSTRING (work with part of string)

```sql
SELECT SUBSTRING('Hello World', 1,4)


=====> Hell

SELECT SUBSTRING('Hello World', 4 )

====> lo World


SELECT SUBSTRING('Hello World',-3);

====> rld
```

### Replace(Replace part of string)

```sql
SELECT REPLACE('Hello World','Hell', 'AAAA')

====> AAAAo World

SELECT REPLACE('cheese bread coffee milk,' ', 'and')
```

### REVERSE(换位置)

```sql
SELECT REVERSE('Hello World');

=====> dlroW olleH
```

## Char Length(count the string)

```sql
select CHAR_LENGTH('Hellow World');

====>  11
```

### Upper() and Lower() (Upper case and Lower Case)

```sql
SELECT UPPER('Hello World');

====> HELLO WORLD
```

### Selection 

### DISTINCT（Give all unique value）

```sql

```

### order by(sort)

```sql
SELECT author_lname FROM books ORDER BY author_lname;

SELECT author_lname FROM books ORDER BY author_lname DESC;

```

### limit

### like(beter searching)

```sql
SELECT author_fname WHERE author_fname LIKE '%da%';
```

%代表省略

```sql
SELECT stock_quantity where stock_quantity = '_____'
```

'_ _ _ _' 代表几位数

```sql
SELECT title where title LIKE '%/%%'
```

/% 代表 万一搜索的包含 %

## Aggregate Functions(Combin Data)

### COUNT 

```sql
SELECT COUNT(*) from books;
```

### DISTINCT

```sql
SELECT COUNT(DISTINCT(author_fname)) from books;
```

### group by 

```sql
SELECT title, author_lname from books GROUP BY author_lname; 

SELECT author_lname, COUNT(*) FROM books GROUP BY author_lname;
```

### MIN and MAX

```sql
SELECT MIN(released_year) FROM books;


SELECT MAX(released_year) FROM books;
```

### AVG 

```sql
average data 

```

## Data Types

### VARCHAR 和 CHAR

CHAR has **fixed length** , CHAR is **FASTER** for fixed length text.

 <img src="/Users/jiachenliu/Library/Application Support/typora-user-images/截屏2021-01-13 上午9.35.07.jpg" alt="截屏2021-01-13 上午9.35.07" style="zoom: 33%;" />

### INT ,  DECIMAL,

```sql
DECIMAL(5,2) 

====>5: total number of digits , 2: digits after decimal
```

### FLOAT and DOUBLE

store large number using less space 

```sql

```

<img src="/Users/jiachenliu/Library/Application Support/typora-user-images/截屏2021-01-13 上午9.55.21.jpg" alt="截屏2021-01-13 上午9.55.21" style="zoom:33%;" />

### DATE and TIMES

DATE: values with a date but no time. Format: YYYY-MM-DD

TIME: values with a TIME but no DATE. Format: HH:MM:SS

DATETIME: values with a DATE and TIME. Format: YYYY-MM-DD HH:MM:SS



### CURDATE, CURTIME, NOW 

CURDATE(): current date 

CURTIME(): current time 

NOW(): current daytime

DAY(): extract the day 

DAYNAME():  

```mysql
 select DAYNAME(birthday) from people;
 "Friday"
```



DAYOFWEEK():

DAYOFYEAR(): tell exact day of that year 

### Datemath

DATEDIFF(): the day between different date 

```mysql
select datediff(now(),'1994-11-04');

--->9573
```

DATEADD(): 

```mysql
select date_add(now(),interval 1 day );

---> 2021-01-20 16:26:35
```

### TIMESTAMP

## Logical Operator

### !=

```sql
select * from books where released_year != 2017;
```

### Not Like

```mysql
select title from books where title not like '%w%'; 

select all title that not contain w
```

### >, < 

```sql
select  * from books where released_year > 2013;

select  * from books where released_year >= 2013;
```

### AND and OR

```sql
select  title, author_lname, released_year from books where author_lname = "Eggers" AND released_year < 2013;

select  title, author_lname, released_year from books where author_lname = "Eggers" AND released_year < 2013;

OR:只要有一个true 就是true 
```

### BETWEEN 和 NOT BETWEEN

```sql
select * from books where released_year between  2004 and 2015;

select * from books where released_year not between  2004 and 2015;
```

### CAST() 把一个数据类型变成另外一个数据类型

```sql
select cast('2017-05-02' as datetime); 

select name, birthdate from people where birthdate between CAST('1980-01-01' as datetime )  and CAST('2020-01-01' as datetime);
```

### IN and NOT IN 

```sql
select title, author_lname from books where author_lname IN ('Carver','Lahiri','Smith');

select title, author_lname from books where author_lname NOT IN ('Carver','Lahiri','Smith');

select title, author_lname from books where released_year >= 2000 and released_year % 2 != 0;
```

### CASE

```mysql
select title , released_year,
       CASE
            WHEN released_year >= 2000 THEN 'Modern Lit'
            ELSE '20th Century Lit'
        END AS genre
from books;



select title,stock_quantity,
CASE
when stock_quantity between 0 and 50 then "*"
when stock_quantity between 51 and 100 then '**'
else '***'
end as 'stock'
from books;


select title, author_lname  from books where SUBSTRING(author_lname,1,1) in ('C', 'S');
```

## JOIN

### One to Many

#### Primary Key

```mysql
create table customers(
    id int auto_increment primary key,
    first_name varchar(100),
    last_name  varchar(100),
    email varchar(100)
);

```

#### Forigen Key

```mysql
create table orders(
    id int auto_increment primary key,
    order_date date,
    amount decimal(8,2),
    customer_id int,
    foreign key (customer_id) references customers(id)
);
```

#### CROSS JOIN

1. order table:

   <img src="/Users/jiachenliu/Library/Application Support/typora-user-images/截屏2021-01-22 下午4.48.04.jpg" alt="截屏2021-01-22 下午4.48.04" style="zoom:50%;" />

2. Customer table: 

   <img src="/Users/jiachenliu/Library/Application Support/typora-user-images/截屏2021-01-22 下午4.48.27.jpg" alt="截屏2021-01-22 下午4.48.27" style="zoom: 50%;" />

3. Cross join 

   ```mysql
   select * from customers,orders;
   ```

   <img src="/Users/jiachenliu/Library/Application Support/typora-user-images/截屏2021-01-22 下午4.50.05.jpg" alt="截屏2021-01-22 下午4.50.05" style="zoom: 33%;" />

####  Inner Join

<img src="/Users/jiachenliu/Library/Application Support/typora-user-images/截屏2021-01-22 下午4.57.42.jpg" alt="截屏2021-01-22 下午4.57.42" style="zoom: 25%;" />

```mysql
select first_name, last_name, order_date, amount 
from customers 
join orders
		 on customer.id = orders.customer_id;
		 
		 
A是 customer ， B 是 orders
```

<img src="/Users/jiachenliu/Library/Application Support/typora-user-images/截屏2021-01-22 下午5.03.05.jpg" alt="截屏2021-01-22 下午5.03.05" style="zoom: 50%;" />

#### Left Join



<img src="/Users/jiachenliu/Library/Application Support/typora-user-images/截屏2021-01-22 下午5.20.44.jpg" alt="截屏2021-01-22 下午5.20.44" style="zoom: 25%;" />

```mysql
select * from customers
left join orders
on customers.id = orders.customer_id;
```

<img src="/Users/jiachenliu/Library/Application Support/typora-user-images/截屏2021-01-22 下午5.23.23.jpg" alt="截屏2021-01-22 下午5.23.23" style="zoom:50%;" />

**take everything from A: customers to B: orders;**

#### IFNULL

IFNULL(exp1, exp2): 

```mysql
select first_name,
       last_name,
       ifnull(sum(amount), 0) as total_spent
from customers
left join orders o on customers.id = o.customer_id
group by customers.id;
```

<img src="/Users/jiachenliu/Library/Application Support/typora-user-images/截屏2021-01-22 下午6.05.34.jpg" alt="截屏2021-01-22 下午6.05.34" style="zoom: 67%;" />

#### Right Join

<img src="/Users/jiachenliu/Library/Application Support/typora-user-images/截屏2021-01-22 下午6.06.31.jpg" alt="截屏2021-01-22 下午6.06.31" style="zoom: 25%;" />

**take every thing from orders that matching customers**

```mysql
select * from customers
right join orders
on customers.id = orders.customer_id;
```



## CTE

## 修改表名(在不删除数据的情况下修改表名)

```mysql
ALTER  TABLE table_name RENAME TO new_table_name

例如 ALTER  TABLE admin_user RENAME TO a_user
```

##  Triger

SQL statements that are automatically run when a specific table is changed. 

<img src="/Users/jiachenliu/Library/Application Support/typora-user-images/截屏2021-01-29 上午10.22.09.jpg" alt="截屏2021-01-29 上午10.22.09" style="zoom:33%;" />



<img src="/Users/jiachenliu/Library/Application Support/typora-user-images/截屏2021-01-29 上午10.22.35.jpg" alt="截屏2021-01-29 上午10.22.35" style="zoom:33%;" />



```mysql
delimiter $$

create trigger must_be_adult
    before insert on users for each row
    begin
        if NEW.age < 18
            then signal sqlstate '45000'
            set message_text = 'must be an adult!';
        end if;
    end;
$$

delimiter ;
```



