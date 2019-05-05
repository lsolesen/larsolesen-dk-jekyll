---
title: "Fixing the database"
permalink: /content/fixing-database
language: en
tags:
  - boa
last_modified_at: 2013-08-31T09:21:54Z
---

This is how you can fix the database on Barracuda.

```
service cron stop

bash /var/xdrago/mysql\_repair.sh

service cron start

grep mysql /var/log/syslog

Mysql data directory

/var/lib/mysql
```
