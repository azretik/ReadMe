### Docker-compose
запуск конфигурации docker-compose - поднять и потушить
```
# sudo docker-compose up
# sudo docker-compose down
```

простая сборка nginx + php-fpm

_docker-compose.yml_
```
web:
    image: nginx:latest
    ports:
        - "8080:80"
    volumes:
        - ./code:/code
        - ./site.conf:/etc/nginx/conf.d/site.conf
    links:
        - php
php:
    image: php:7-fpm
    volumes:
        - ./code:/code
```

_site.conf_
```
server {
    index index.php index.html;
    server_name php-docker.local;
    error_log  /var/log/nginx/error.log;
    access_log /var/log/nginx/access.log;
    root /code;

    location ~ \.php$ {
        try_files $uri =404;
        fastcgi_split_path_info ^(.+\.php)(/.+)$;
        fastcgi_pass php:9000;
        fastcgi_index index.php;
        include fastcgi_params;
        fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;
        fastcgi_param PATH_INFO $fastcgi_path_info;
    }
}
```
