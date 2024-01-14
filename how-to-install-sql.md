## How to install SQL on Arch

NOTE: On Arch Linux, MariaDB is what you want to use.
MySQL is a deprecated package (no longer available on pacman, the Arch packge manager)
As a matter of fact, if you try to run any commmands here with mysql,
you will be redirected to mariadb.

https://www.geeksforgeeks.org/how-to-install-and-configure-mysql-on-arch-based-linux-distributionsmanjaro/

`sudo pacman -S mariadb`

Next verify the install:
`mariadb --version`

Next initialize the MariaDB Directory, and create the system tables needed for the functioning of the MariaDB server. 
`sudo mariadb-install-db --user=mysql --basedir=/usr --datadir=/var/lib/mysql`

Next start the server:
`sudo systemctl start mariadb.service`

Log into MariaDB 
`sudo mariadb -u root`
You will be logged into a command prompt that looks like this:
`MariaDB [(none)]>`

NOTE: The proper syntax woul look like this
`mariadb -u name-of-user -h the-remote-server-you want to connect to -p the-port -p the password`

## SQL Commands
When logged into the SQL prompt, Every command in SQL must end with a semicolon.
If 

`show databases` = Show databases

`CREATE DATABASE nc_coffee;`
NOTE: In SQL keywords are not sensitive, 
so `create database nc_coffee;` is valid.

## Selecting a database
`use nc_coffee;` = Access the database called nc_coffee.
Your prompt will now look like this MariaDB [nc_coffee]>

`show tables` = Show the tables of a database.

---

## Creating a table 

### How to create columns
Enter the following one line at a time:
`create table coffee_table (`
`id int,` = id is the column name, int means integer (the type of data that will be stored in that collumn)
`name varchar(255),` = varchar(255), means 255 characters
`region varchar(255),`
`roast varchar(255)`
`);` = This will create the database.

### How to create rows
`insert into coffee_table values (1, "default route", "japan", "light");`

---

## How to view the details of this table
`show tables;`
`describe coffe_table;`

## How to view the actual data
`select * from coffe_table;` = select everything.

You can also select a specific field:
`select region from coffee_table`

You can also filter the data based on a condition from a field:
`SELECT * FROM coffee_table WHERE region = "japan";`
`SELECT * FROM coffee_table WHERE NOT region = "japan";`

## How to delete an entire row from your table
`DELETE FROM coffee_table WHERE NOT region = "japan";`

## How to update a region
`UPDATE coffee_table set region = "china" where roast = "medium";`

# How to view the data in a specific order:
`select * from avengers order by age asc;` = Ascending order.
`select * from avengers order by age desc;` = Descending order.

## How to add more collumns to a table after it has been created
`ALTER TABLE coffee_table ADD on_sale BOOLEAN;`

NOTE: In an SQL table, 1 is true, and 0 is false
NOTE: You can select multiple fields with a , E.g.
`SELECT customerid, city, country FROM customers;`

## Using LIKE %
`WHERE region LIKE "East%"` will return all records where the the region starts with East.

---

## Some useful patterns

Pattern Results that could be returned

'a%'        apple123, art, a

'a_'        as, an, a7

'a__'       ant, add, a1c

'%a'        pizza, Z6ra, a

'_a'        ma, 1a, Ha

'%a%'       Again, back, a

'_a_'       Car, ban, ea7

---
+1 (780) 428-9482

Terminology: Schema
This is refers to how the database is arranged and organized.
