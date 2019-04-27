---
title: "Fixing the database"
permalink: /content/fixing-database
language: und
tags:
last_modified_at: 2013-08-31T09:21:54Z
---

service cron stop

bash /var/xdrago/mysql\_repair.sh

service cron start

grep mysql /var/log/syslog

Mysql data directory

/var/lib/mysql
