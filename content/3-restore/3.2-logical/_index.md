---
title: "Logical Restore"
date: "`r Sys.Date()`"
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

1. **Logical Backup** stores the data and structure of the database in the form of SQL commands, such as **CREATE TABLE, INSERT INTO, etc.** This method primarily backs up the content of the database (including tables, data, triggers, stored procedures, etc.) without involving the physical files of the database.

2. The most common tool for creating Logical Backup in MySQL is **mysqldump**.

3. Backup a Table

   1. **Backup only the structure of the table**
      - Command:
      
      ```bash
      mysqldump.exe -uroot -p <database_name> -d <table_name> > <folder_path>\<table_name>_ddl.sql
      ```
      
   2. **Backup only the data of the table**
      - Command:
      
      ```bash
      mysqldump.exe -uroot -p <database_name> -t <table_name> > <folder_path>\<table_name>_data.sql
      ```
      
   3. **Backup both the structure and data of the table**
      - Command:
      
      ```bash
      mysqldump.exe -uroot -p <database_name> <table_name> > <folder_path>\<table_name>_table.sql
      ```
      

4. Backup One or More Databases

   1. **Backup one database:**
      - Command:
      
      ```bash
      mysqldump.exe -uroot -p <database_name> > <folder_path>\<database_name>db.sql
      ```
      
   2. **Backup all databases:**
      - Command:
      
      ```bash
      mysqldump.exe -uroot -p --all-databases > <folder_path>\alldb.sql
      ```
