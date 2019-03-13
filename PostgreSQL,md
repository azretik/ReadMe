### PostgreSQL
изменить значение поля в таблице
```
UPDATE 
  callcenter.blacklists
SET checked = true;
```

снять резервную копию _между паролем и командой pg_dump в винде нужно проставить &&_
```
# PGPASSWORD="password" pg_dump -h host -p port -U username database --scheme "schemeName" "DBname" > file.sql
```

```
# pg_dump --dbname=postgresql://username:password@host:port/database > file.sql
```

восстановление из резервной копии sql
```
# psql -U postgres database < file.sql
```

посчитать сколько весит база
```
SELECT pg_size_pretty( pg_database_size( 'sample_db' ) );
```

посчитать сколько весит таблица
```
SELECT pg_size_pretty( pg_total_relation_size( 'table' ) );
```

выгрузить таблицу в CSV файл
```
# psql -h diana-dtln.dd -U wapclickadm -d sms --no-align -c "SELECT * FROM subscriptions.operator_cidrs" > c:/tofile.csv
```
