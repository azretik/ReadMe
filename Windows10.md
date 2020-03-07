#### Установка WSL и Ubuntu пакета - запускать из под PowerShell
Включение WSL

```Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux```

Скачивание образа Ubuntu

```Invoke-WebRequest -Uri https://aka.ms/wsl-ubuntu-1604 -OutFile Ubuntu.appx -UseBasicParsing```

Установка образа Ubuntu

```Add-AppxPackage .\Ubuntu.appx```
