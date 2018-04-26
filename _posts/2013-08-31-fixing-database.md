---
title: Fixing the database
redirect_from: /content/fixing-database
tags:
modified: 2013-08-31T09:21:54Z
---

service cron stop

bash /var/xdrago/mysql\_repair.sh

service cron start

grep mysql /var/log/syslog

Mysql data directory

/var/lib/mysql
