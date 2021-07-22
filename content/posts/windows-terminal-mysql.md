---
title: "MySQL and Windows Terminal"
description: Some notes on configuring Windows Terminal to work with MySQL. 
date: 2021-07-22T06:00:00+01:00
draft: false
toc: true
tags:
  - MySQL
  - PowerShell
  - SQL
categories:
  - Windows
series:
  - Windows Terminal
---

MySQL has it's own terminal emulator, providing a command-line interface (CLI) for the direct input and execution of SQL commands and scripts. 

<!--more-->

The MySQL terminal can be called from PowerShell, CMD or added to the Windows Terminal.

![screenshot of Windows Terminal running a MySQL terminal, with some SQL commands](/images/MySQL-Terminal-In-Windows-Terminal.png "MySQL in Windows Terminal")

## Starting A MySQL Terminal Session From Inside an Active PowerShell or CMD Session

### PowerShell

```PowerShell
& 'C:\Program Files\MySQL\MySQL Server 8.0\bin\mysql.exe' --port=3306 --host=127.0.0.1 --user=root -p
```

### CMD

```Batchfile
"C:\Program Files\MySQL\MySQL Server 8.0\bin\mysql.exe" --port=3306 --host=127.0.0.1 --user=root -p
```

### Some Useful SQL Commands

```SQL
show databases;
use employeeschema;
show tables;
describe employee;
select * from employee;
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