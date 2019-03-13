### COMPOSER (PHP)
скачать установщик composer и запустить, перенести исполняемый файл в локальный bin пользователя
```
# curl -sS https://getcomposer.org/installer | php
# mv composer.phar ~/.local/bin/composer
```

### LARAVEL
запустить фоновые выполнение консольных задач
```
# php /path-to-your-project/artisan schedule:run >> /dev/null 2>&1
```

создать таблицу миграции
```
# php artisan make:migration create_users_table --create=users
```

добавить дополнение к миграции
```
# php artisan make:migration add_votes_to_users_table --table=users
```
