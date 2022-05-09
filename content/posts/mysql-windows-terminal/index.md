---
title: "MySQL and Windows Terminal"
description: Some notes on configuring Windows Terminal to work with MySQL. 
date: 2021-09-20T14:00:00+01:00
draft: false
toc: true
pinned: false
featuredImage: ''
tags: [MySQL, PowerShell, SQL]
categories: [Windows, MySQL]
series: [Windows Terminal]
---

MySQL has it's own terminal emulator, providing a command-line interface (CLI) for the direct input and execution of SQL commands and scripts. 

<!--more-->

The MySQL terminal emulator can be called from PowerShell, CMD or added to the Windows Terminal.

![screenshot of Windows Terminal running a MySQL terminal, with some SQL commands](/images/MySQL-Terminal-In-Windows-Terminal.png "MySQL in Windows Terminal")

## Starting A MySQL Terminal Session From Inside an Active PowerShell or CMD Session

The MySQL terminal is launched by calling program 'mysql.exe'.  A number of parameters can be passed, the full list is available at [4.5.1.1 mysql Client Options](https://dev.mysql.com/doc/refman/8.0/en/mysql-command-options.html).  

The parameters I typically use are detailed below: 

| Parameter | Details                                                       |
|-----------|---------------------------------------------------------------|
| --port    | Default=3306 - TCP/IP port number for connection.             |
| --host    | Default=127.0.0.1 - Host on which MySQL server is located     |
| --local_infile=1 | Default=0 - Allow importing of data from the local client |
| --user    | Default=root - MySQL user name when connecting to the server. |
| -p        | Password to use when connecting to the server.                |

Here are examples of calling mysql.exe with these parameters:

### PowerShell

```powershell
& 'C:\Program Files\MySQL\MySQL Server 8.0\bin\mysql.exe' --port=3306 --host=127.0.0.1 --local_infile=1 --user=root -p
```

### CMD

```Batchfile
"C:\Program Files\MySQL\MySQL Server 8.0\bin\mysql.exe" --port=3306 --host=127.0.0.1 --local_infile=1 --user=root -p
```

### Example SQL Commands

```sql
SHOW databases;
USE employeeschema;
SHOW TABLES;
CREATE TABLE itemType (
    id INT UNSIGNED NOT NULL AUTO_INCREMENT,
    description VARCHAR(100) NOT NULL,
    loanDuration INT NOT NULL,
    created TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY (id)
    );
INSERT INTO itemType(description, loanDuration)
    VALUES
    ('Raspberry Pi Kits', 28),
    ('Raspberry Pi Hats & Microcontrollers', 28),
    ('Raspberry Pi Books', 56)
    ;
SELECT * FROM itemType;
```

## Windows Terminal - Adding A Dedicated MySQL Terminal

1. Start Windows Terminal
1. Open Settings <kbd>Ctrl</kbd> + <kbd>,</kbd>
1. Click `+ Add new` (bottom left corner)
1. Enter the values for your installation, for example:
    
    - Name: `MySQL`
    - Command Line: `C:\Program Files\MySQL\MySQL Server 8.0\bin\mysql.exe -h localhost -u root -p` (yours might be different)
    - Starting directory: I've left this empty
        - I've ticked "Use parent process directory"
    - Icon:  I just used an emoji (press <kbd>Windows</kbd> + <kbd>.</kbd>).  I'm using this one... 🐬
    - Tab Title: `MySQL`

    Done.