вывести список запущеных контейнеров
```
# docker ps
```

подключиться к консоли контейнера
```
# docker exec -i -t 6ee6223a3ce3 bash
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
