---
title: configure to zip jenkins log daily
date: 2017-01-20 11:03:37
tags:
---
env:
docker image os: CentOS 6.6
1. install logrotate
```
yum -y install logrotate
```
2. install crontab
```
yum -y install vixie-cron
```
3. update /etc/crontab
```
01 01 * * * root run-parts /etc/cron.daily
```
