### UBUNTU
Установка кодеков
```
# sudo apt install ubuntu-restricted-extras libavcodec-extra libdvd-pkg
```

Установка телеграма
```
# sudo add-apt-repository ppa:atareao/telegram
# sudo apt-get update
# sudo apt-get install telegram
```

Отключить Fn клавиши, чтобы работали только при зажатой (на маках)
```
# sudo mcedit /etc/rc.local
echo 2 > /sys/module/hid_apple/parameters/fnmode
```

Отключить и переназначить клавиши модификаторы
```
# xmodmap
# xmodmap -e 'claer shift'
# xmodmap -e 'add shift=Shift_L'
```

Смотреть информацию с датчиков температуры
```
# sudo apt install lm-sensors
# sudo sensors-detect
# sensors
```

```
# sudo apt install psensor
# psensor
```

### SAMBA
установить пакет samba (debian), создать самба пароль для пользователя root, редактировать файл конфигурации
```
# sudo apt-get install samba
# sudo smbpasswd -a root
# sudo mcedit /etc/samba/smb.conf
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

### LINUX
удалённый запуск приложения
```
# plink 192.168.1.130 -ssh -P 22 -l azretik -2 -4 -C -i "c:\Program Files\PuTTY\keys\mint-test\id_rsa" "DISPLAY=:0 nohup thunar"
```
