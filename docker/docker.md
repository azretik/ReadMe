#### Базовый функционал docker

вывести список запущеных контейнеров
```
# docker ps
```

подключиться к консоли контейнера
```
# docker exec -i -t 6ee6223a3ce3 bash
# docker exec -it {id/name} /bin/bash
# docker exec -it {id/name} /bin/sh
```

собрать образ из необходимой папки, с выбранным названием и без использования кеша
```
# docker build [dockerfile folder] -t azretik/name --no-cache
```

удалить образ
```
# docker image rm [id]
```

удалить контейнер
```
# docker rm [container name]
```

удалить все образы
```
# docker rmi $(sudo docker images -a -q)
```

показать адрес файла лога контейнера
```
# sudo docker inspect --format='{{.LogPath}}' <containertagname>
```

очистка лог файла контейнера
```
# echo "" > $(docker inspect --format='{{.LogPath}}' <container_name_or_id>)
```

очистить все логи контейнеров
```
#!/bin/bash -e

if [[ -z $1 ]]; then
    echo "No container specified"
    exit 1
fi

if [[ "$(docker ps -aq -f name=^/${1}$ 2> /dev/null)" == "" ]]; then
    echo "Container \"$1\" does not exist, exiting."
    exit 1
fi

log=$(docker inspect -f '{{.LogPath}}' $1 2> /dev/null)
truncate -s 0 $log
```
