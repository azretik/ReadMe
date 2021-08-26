### Docker hub - полезные образы
* nginx:latest - свежий nginx
* php:7-fpm - php-fpm без модулей
* exozet/php-fpm:7.1.10 - php-fpm с дополнениями (в том числе с композером) [официальный git](https://github.com/exozet/docker-php-fpm)

### Сборка и запуск образов
##### mongo-db
```
# docker run -p 27017:27017 --name mongo mongo &
```
Логин без пароля. 
