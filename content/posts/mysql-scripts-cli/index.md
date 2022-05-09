---
title: "MySQL: Running SQL Scripts From the Command Line"
description: How to run .sql scripts from the command line. 
date: 2021-09-22T08:00:00+01:00
draft: false
toc: true
pinned: false
featuredImage: ''
tags: [MySQL, SQL]
categories: [MySQL]
---

MySQL can be accessed from the command line interface (CLI).  Here's how to run SQL scripts from the CLI. 

<!--more-->

When the server for MySQL is installed on a system, a client application program is also installed. On Windows this is mysql.exe. 

The client app, mysql.exe, is a terminal emulator, enabling interactive input of SQL statements [MySQL and Windows Terminal](https://upyesp.org/posts/mysql-windows-terminal/).

The same app also provides the ability for it to be called and execute a SQL script, straight from the command line or in a script. 

## Executing SQL Scripts from the Command Line

### PowerShell

Example of running an SQL script in MySQL from PowerShell:

```Powershell
Get-Content myScript.sql | & 'C:\Program Files\MySQL\MySQL Server 8.0\bin\mysql.exe' --verbose --force --table --port=3306 --host=127.0.0.1 --local_infile=1 --user=root -pdigimark > myScriptResults.txt
```

### CMD

Example of running an SQL script in MySQL from CMD:

```Batchfile
"C:\Program Files\MySQL\MySQL Server 8.0\bin\mysql.exe" --verbose --table --force --port=3306 --host=127.0.0.1 --local_infile=1 --user=root -pdigimark < myScript.sql > myScriptResults.txt
```

## Explanation of Command Line Parameters

When calling mysql.exe, several parameters are available, see [4.5.1.1 mysql Client Options](https://dev.mysql.com/doc/refman/8.0/en/mysql-command-options.html).  

### MySQL Password
In addition to the parameters discussed in [MySQL and Windows Terminal](https://upyesp.org/posts/mysql-windows-terminal/), consideration needs to be given to the password required for the MySQL service.  For an interactive MySQL terminal, the user can enter the password.  To enable a fully automated execution of a script, where the user may not be present, interactive input of the password may not be practical.  

It is possible to include password as a parameter, using '-p'. For example, if the password is digimark, the syntax would be '-pdigimark'. Clearly there are security implications with this method, you may want to consider if this is a suitable option in your use case.

### Redirecting the Results of the SQL Script To a Text File or Log File

Appending the '>' symbol along with a file name will direct the results of the SQL script to that file name, for example '> myScriptResults.txt'.  

### Including the SQL Script as a Parameter

This varies depending on if you are using PowerShell or CMD.  For CMD,  pipe the SQL script as input with '<' [How-to: Redirection](https://ss64.com/nt/syntax-redirection.html), along with the name of the script, such as, '< myScript.sql'. For PowerShell, use the [Get-Content](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-content?view=powershell-7.1) command, for example 'Get-Content myScript.sql |'.

### Other Parameters

These are some optional parameters I use:
 
| Parameter | Details                              |
|-----------|--------------------------------------|
| --local_infile=1 | Default=0 - Allow importing of data from the local client |
| --verbose | Verbose mode                         |
| --force   | Continue even if an SQL error occurs |
| --table   | Display output in tabular format     |


## Example SQL Script

Here's an example SQL script.  To create it:

1. Open VSCode, any IDE or text editor (such as Notepad).
1. Copy the code below and paste it into the editor.
1. Save the file, with a ".sql" extension, for example "myScript.sql"

```sql
#######################################################
#
# This SQL script prepares database exampleDB for use.
# The existing database is dropped, a new db is
# created, tables are then added and populated with
# data.
#
#######################################################

# Output the date and time the script was run.
select "Output from script, run at: " as 'Script Information',
    NOW() as 'Date and Time Executed';

# First, drop the database (if it exists).
DROP DATABASE exampleDB;

# Create a new, empty database.
CREATE DATABASE exampleDB;

# Use the new database.
USE exampleDB;

#######################################################
# Create table: itemType
#######################################################

CREATE TABLE itemType (
    id INT UNSIGNED NOT NULL AUTO_INCREMENT,
    description VARCHAR(100) NOT NULL,
    loanDuration INT NOT NULL,
    created TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    PRIMARY KEY (id)
    );

# Add some item types to table: itemType
INSERT INTO itemType(description, loanDuration)
    VALUES
    ('Raspberry Pi Kits', 28),
    ('Raspberry Pi Hats & Microcontrollers', 28),
    ('Raspberry Pi Books', 56)
    ;

SELECT * FROM itemType;
#######################################################
```
