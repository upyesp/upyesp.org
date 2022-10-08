---
title: "MySQL: Starting & Stopping the Server"
description: For Windows installations, how to manage the MySQL server.
date: 2022-03-08T08:00:00+01:00
draft: false
toc: true
pinned: false
featuredImage: ''
tags: [MySQL, SQL]
categories: [MySQL]
---

The MySQL server runs as a background service. Be default, it is set to start automatically when Windows starts. You can manage this service from the Windows Services applet and from the command line.

<!--more-->

The MySQL server program is [mysqld](https://dev.mysql.com/doc/refman/8.0/en/mysqld.html).  This must first be active and running for MySQL to provide any services.

The MySQL server can be run as a service, or started manually from the command line.  To start, stop or restart the MySQL server as a service, use the Windows Services app, `services.msc`. This can be run with <kbd>Windows</kbd> + <kbd>r</kbd> and typing `services.msc` into the Run dialog box.

To start MySQL from the command line, use the following:

PowerShell:

```Powershell
& 'C:\Program Files\MySQL\MySQL Server 8.0\bin\mysqld'
```

CMD:

```batchfile
"C:\Program Files\MySQL\MySQL Server 8.0\bin\mysqld"
```

The MySQL server can be stopped with:

PowerShell:

```Powershell
& 'C:\Program Files\MySQL\MySQL Server 8.0\bin\mysqladmin' -u root -p shutdown
```

CMD:

```batchfile
"C:\Program Files\MySQL\MySQL Server 8.0\bin\mysqladmin" -u root -p shutdown
```
