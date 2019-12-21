### Установка OctoPrint (принт сервер для 3д принтеров) на ArmBian операционную систему для OrangePi

#### Установка Python и клонирование OctoPrint репозитория
```
sudo apt update
sudo apt install python python-pip virtualenv python-dev  
cd /opt  
git clone https://github.com/foosel/OctoPrint.git  
cd OctoPrint  
virtualenv venv  
./venv/bin/python setup.py install  
#Enter a username that is **NOT** a root user  
sudo chown -R [username]:[username] /opt/OctoPrint
```
#### Создание и запуск сервиса OctoPrint
Необходимо создать файл /etc/systemd/system/octoprint.service

#### Содержимое файла octoprint.service
```
[Unit]
Description=OctoPrint
After=network.target

[Service]
ExecStart=/opt/OctoPrint/venv/bin/octoprint serve
Restart=always
User=[username]
Group=[username]

[Install]
WantedBy=default.target
````

#### OctoPrint будет доступен на порту ip:5000
