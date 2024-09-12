---
title: "Physical Restore"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

1. **Physical Backup** in MySQL is a method of **backing up all physical files of the database**, including data files, log files, and configuration files, from the storage system.

2. **Physical Backup** directly saves the system files used by MySQL to store data. These files include InnoDB data files, MyISAM data files, log files, and related configuration files.

3. The data is copied in its entirety and can be immediately used upon restoration, without the need to re-execute SQL commands as in Logical Backup.
