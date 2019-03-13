# ReadMe
Что делать если? Простой список команд, решений и подходов к работе с железом и программным обеспечением.

### GIT
инициализировать гит
```
git init
```

```
git remote add [git_url_alias] [GIT_URL]
```

вытащить изменения из репозитория
```
git pull [alias]
```

```
git fetch [alias]
```

переключить ветку
```
git checkout [нужная ветка]
```

убрать изменения
```
git stash
```

смержить текущий код с нужной веткой
```
git merge ogirin/master
```


### COMPOSER (PHP)
скачать установщик composer и запустить, перенести исполняемый файл в локальный bin пользователя
```
curl -sS https://getcomposer.org/installer | php
mv composer.phar ~/.local/bin/composer
```


### SAMBA (LINUX)
установить пакет samba (debian), создать самба пароль для пользователя root, редактировать файл конфигурации
```
sudo apt-get install samba
sudo smbpasswd -a root
sudo mcedit /etc/samba/smb.conf
```
содержимое файла конфигурации самба
```
[folder]
path = /path
create mask = 0777
directory mask = 0777
valid users = "root"
write list = "root"
```

### DOCKER
подключиться к консоли контейнера
```
docker-compose exec workspace bash
```

собрать образ из необходимой папки, с выбранным названием и без использования кеша
```
docker build [dockerfile folder] -t azretik/name --no-cache
```

удалить образ
```
docker image rm [id]
```

удалить контейнер
```
docker rm [container name]
```

удалить все образы
```
docker rmi $(sudo docker images -a -q)
```

### FFMPEG
вырезать из ролика часть
```
ffmpeg -ss <начало> -t <продолжительность> -i in1.avi -vcodec copy -acodec copy out1.avi
```

### LARAVEL
запустить фоновые выполнение консольных задач
```
php /path-to-your-project/artisan schedule:run >> /dev/null 2>&1
```

создать таблицу миграции
```
php artisan make:migration create_users_table --create=users
```

добавить дополнение к миграции
```
php artisan make:migration add_votes_to_users_table --table=users
```

### PostgreSQL
изменить значение поля в таблице
```
UPDATE 
  callcenter.blacklists
SET checked = true;
```

снять резервную копию _между паролем и командой pg_dump в винде нужно проставить &&_
```
PGPASSWORD="password" pg_dump -h host -p port -U username database --scheme "schemeName" "DBname" > file.sql
```

```
pg_dump --dbname=postgresql://username:password@host:port/database > file.sql
```

восстановление из резервной копии sql
```
psql -U postgres database < file.sql
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
psql -h diana-dtln.dd -U wapclickadm -d sms --no-align -c "SELECT * FROM subscriptions.operator_cidrs" > c:/tofile.csv
```

### LINUX
удалённый запуск приложения
```
plink 192.168.1.130 -ssh -P 22 -l azretik -2 -4 -C -i "c:\Program Files\PuTTY\keys\mint-test\id_rsa" "DISPLAY=:0 nohup thunar"
```
