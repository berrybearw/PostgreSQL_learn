查看 table 欄位 型態

https://database.guide/3-ways-to-check-a-columns-data-type-in-postgresql/

```
SELECT column_name, data_type,

character_maximum_length AS max_length,

character_octet_length AS octet_length

FROM ==information_schema.columns==

WHERE table_schema = 'public' AND table_name = 'actor'

AND column_name = 'first_name';
```

查看 有哪些 table

```
select * from ==information_schema.tables==
```

查看有哪些 user

https://www.postgresqltutorial.com/postgresql-administration/postgresql-list-users/

查看 暫存表

https://www.dbrnd.com/2017/06/postgresql-find-a-list-of-active-temp-tables-with-size-and-user-information-idle-connection/

```
select nspname , relname

FROM ==pg_catalog.pg_class== c

LEFT JOIN ==pg_catalog.pg_namespace== n

ON n.oid = c.relnamespace

where nspname like 'pg_temp%'

```
