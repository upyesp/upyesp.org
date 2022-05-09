---
title: "MySQL: Import CSV Files"
description: How to import CSV data into a MySQL database table. 
date: 2021-11-02T08:00:00
draft: false
toc: true
pinned: false
featuredImage: ''
tags: [MySQL, SQL, CSV]
categories: [MySQL]
---

A single SQL statement can import a CSV file into a MySQL database table. 

<!--more-->

It is possible to import a CSV file into a MySQL table, using the [LOAD DATA](https://dev.mysql.com/doc/refman/5.6/en/load-data.html) SQL statement, like this:

```sql
LOAD DATA local INFILE 'C:/example.csv'
    INTO TABLE example_table
    FIELDS TERMINATED BY ' '
    ENCLOSED BY '"'
    LINES TERMINATED BY '\n'
    IGNORE 1 ROWS;
```

> There are important security considerations when using the above statement, especially if the content of the CSV file is unknown or not from a trusted source. See [Security Considerations for LOAD DATA LOCAL](https://dev.mysql.com/doc/mysql-security-excerpt/8.0/en/load-data-local-security.html) for more information.

A sequence of preparatory steps to enable the import of a CSV could be:

1. If you haven't already, get a copy of the CSV file you want to import.  This example will use CSV file ```nasa_aug95.csv``` from data.world, [https://data.world/shad/nasa-website-data/workspace/file?filename=nasa_aug95.csv](https://data.world/shad/nasa-website-data/workspace/file?filename=nasa_aug95.csv).
1. Move or copy your CSV file to the root folder of your 'C' drive, here ```C:\```.  This is just temporary, move or delete it later - or if you store it in a different location, adapt the SQL statement below.
1. Open a MySQL terminal, so you can enter SQL commands.  Do that by... open a command prompt, then copy & paste this command into it:  ```"C:\Program Files\MySQL\MySQL Server 8.0\bin\mysql.exe" --port=3306 --host=127.0.0.1 --local_infile=1 --user=root -p``` (you'll need to enter the password you saved in MySQL).  For more information on using the MySQL terminal, see [MySQL and Windows Terminal](https://upyesp.org/posts/mysql-windows-terminal/).
1. The prompt should now look like this... ```mysql>```

## SQl Statements

Example statements for the MySQL terminal:

```sql
SHOW DATABASES;
```

To create a new database:

```sql
CREATE DATABASE nasa;
```

To use a database:

```sql
USE nasa;
```

List tables in a database:

```sql
SHOW TABLES;
```

Before the CSV file can be loaded into a table, a table needs to exist for the CSV to be loaded into.  So, create a table.  The columns should be the same format as the CSV:

```sql
CREATE TABLE nasa_aug95 (
    requesting_host VARCHAR(2000),
    datetime DATETIME,
    request VARCHAR(2000),
    status INT,
    response_size INT
    );
```

Load ```nasa_aug95.csv``` into the table. Note the location of ```C:/nasa_aug95.csv``` - in the root of C: also note, use '/' in the path, not '\\' - including on Windows devices. If you have stored your CSV file in a different location, adapt the SQL statement below.

```sql
LOAD DATA local INFILE 'C:/nasa_aug95.csv'
    INTO TABLE nasa_aug95
    FIELDS TERMINATED BY ' '
    ENCLOSED BY '"'
    LINES TERMINATED BY '\n'
    IGNORE 1 ROWS;
```

The above statement might result in this error:

```text
ERROR 3948 (42000): Loading local data is disabled; this must be enabled on both the client and server sides
```

This is an important security measure. If you are satisfied that the CSV file you are importing is completely safe, the following statement will enable the data to be imported:

```sql
SET GLOBAL local_infile=true;
```

Once your CSV file has been imported into a table, typical SQL statements can be performed on it.