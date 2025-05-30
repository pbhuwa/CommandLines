#### **Redis Setup**
Before using Redis with Laravel, you will need to install the predis/predis package via Composer:
```
composer require predis/predis
```

Alternatively, you may install the PhpRedis PHP extension via PECL. The extension is more complex to install but may yield better performance for applications that make heavy use of Redis.

Open PowerShell as Administrator and run this command to enable Windows Subsystem for Linux (WSL):
    - Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux

Launch Microsoft Windows Store:
    install ubuntu

```
sudo apt-add-repository ppa:redislabs/redis
```
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo apt-get install redis-server
```
```
sudo service redis-server start
```
```
sudo service redis-server stop
```
```
sudo service redis-server restart
```
