## Cloud Data Center
RESTful application programming interfaces (API's) that enables you to access data globally service. 
After you register your app and get authentication tokens for a user or service, you can make requests to the Cloud Data Center API's.

#### Information of systems components
```
Hardware Report:

Host Name:                 9F079636H
OS Name:                   Microsoft Windows 10 Pro
OS Version:                10.0.19043 N/A Build 19043
OS Manufacturer:           Microsoft Corporation
OS Configuration:          Standalone Workstation
OS Build Type:             Multiprocessor Free
Registered Owner:          {{users}}
Registered Organization:
Product ID:                00330-50000-00000-AAOEM
Original Install Date:     11/1/2022, 8:20:54 PM
System Boot Time:          11/7/2022, 1:51:51 PM
System Manufacturer:       TOSHIBA
System Model:              PORTEGE Z30-B
System Type:               x64-based PC
Processor(s):              1 Processor(s) Installed.
                           [01]: Intel64 Family 6 Model 61 Stepping 4 GenuineIntel ~2300 Mhz
BIOS Version:              TOSHIBA Version 6.50  , 3/6/2018
Windows Directory:         C:\Windows
System Directory:          C:\Windows\system32
Boot Device:               \Device\HarddiskVolume1
System Locale:             en-us;English (United States)
Input Locale:              en-us;English (United States)
Time Zone:                 (UTC+07:00) Bangkok, Hanoi, Jakarta
Total Physical Memory:     16,279 MB
Available Physical Memory: 7,268 MB
Virtual Memory: Max Size:  19,223 MB
Virtual Memory: Available: 10,034 MB
Virtual Memory: In Use:    9,189 MB
Page File Location(s):     C:\pagefile.sys
Domain:                    WORKGROUP
Logon Server:              \\9F079636H
Hotfix(s):                 6 Hotfix(s) Installed.
                           [01]: KB5018329
                           [02]: KB5000736
                           [03]: KB5012170
                           [04]: KB5018482
                           [05]: KB5018506
                           [06]: KB5001405
Network Card(s):           3 NIC(s) Installed.
                           [01]: Intel(R) Ethernet Connection (3) I218-LM
                                 Connection Name: Ethernet
                                 Status:          Media disconnected
                           [02]: Intel(R) Dual Band Wireless-AC 7265
                                 Connection Name: Wi-Fi
                                 DHCP Enabled:    Yes
                                 DHCP Server:     192.168.43.1
                                 IP address(es)
                                 [01]: 192.168.43.227
                                 [02]: fe80::3ce6:38e2:89da:add4
                           [03]: Hyper-V Virtual Ethernet Adapter
                                 Connection Name: vEthernet (WSL)
                                 DHCP Enabled:    No
                                 IP address(es)
                                 [01]: 172.25.48.1
                                 [02]: fe80::da63:18e9:fd8f:5ffc
Hyper-V Requirements:      A hypervisor has been detected. Features required for Hyper-V will not be displayed.
```
```
Software Report:

Server version:	Apache/2.4.54 (Win64)
PHP Version:	8.0.25 (cli) (built: Oct 25 2022 10:49:29) ( ZTS Visual C++ 2019 x64 )
Mysql Version:	Ver 15.1 Distrib 10.4.25-MariaDB, for Win64 (AMD64)
Framework:	Laravel
Version:	8.x Release September 8th, 2020
Application:	Octane
Server:         swoole-http-server not roadrunner-http-server
```
```
Server Report

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.1 LTS
Release:        22.04
Codename:       jammy
```

#### Getting started for Windows 10
- Settings > Apps and Features > Program and Features. Kemudian Klik Turn Windows Features on or off. checklist under `Windows Subsystem for Linux` and `Virtual Machine Platform`
- Windows Powershell
```
PS wsl --install `optional poin one`
PS dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
PS dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
PS systeminfo | find "System Type"
```
- download and install according to systeminfo
[x64](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi) or [arm64](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_arm64.msi)
- open the Microsoft Store application, then find the Linux system you want to install.
- Windows Powershell
```
PS wsl --set-default-version 2
PS wsl --list --verbose
```
- open the Linux application that has been installed from the Microsoft Store application.

#### Setting server linux
```
# apt update
# apt upgrade
# apt install apache2
# systemctl is-enabled apache2.service or systemctl enable apache2.service
# service apache2 status|start|stop|restart
```
- config ports:	`# nano /etc/apache2/ports.conf`
- config file path:	`# nano /etc/apache2/sites-available/000-default.conf`
- shared folder windows to linux `# sudo ln -s "/mnt/<drive>/<folder>" /var/www/html/GraphGL`
- shared delete folder `# sudo rm -d v.0.0.5`
- IP Address:	`# hostname -I`
```
# apt-get install lsb-release ca-certificates apt-transport-https software-properties-common -y
# LC_ALL=C.UTF-8 add-apt-repository ppa:ondrej/php
# apt-get install php8.0
# apt install php8.0-amqp php8.0-common php8.0-gd php8.0-ldap php8.0-odbc php8.0-readline php8.0-sqlite3 php8.0-xsl php8.0-apcu php8.0-curl php8.0-gmp php8.0-mailparse php8.0-opcache php8.0-redis php8.0-sybase php8.0-ast php8.0-dba php8.0-igbinary php8.0-mbstring php8.0-pgsql php8.0-rrd php8.0-tidy php8.0-yaml php8.0-bcmath php8.0-dev php8.0-imagick php8.0-memcached php8.0-phpdbg php8.0-smbclient php8.0-uuid php8.0-zip php8.0-bz2 php8.0-ds php8.0-imap php8.0-msgpack php8.0-pspell php8.0-snmp php8.0-xdebug php8.0-zmq php8.0-cgi php8.0-enchant php8.0-interbase php8.0-mysql php8.0-psr php8.0-soap php8.0-xhprof php8.0-cli php8.0-intl php8.0-oauth php8.0-raphf php8.0-solr php8.0-xml php-pear php8.0-geoip php8.0-sockets php8.0-swoole php8.0-fpm libapache2-mod-php8.0
```
- switch version php multi:
```
# update-alternatives --config php
# update-alternatives --config phar
# update-alternatives --config phar.phar

# update-alternatives --set php /usr/bin/php8.0
# update-alternatives --set phar /usr/bin/phar8.0
# update-alternatives --set phar.phar /usr/bin/phar.phar8.0
```
- install composer:
```
# curl -s https://getcomposer.org/installer | /usr/bin/php
# mv composer.phar /usr/bin/composer
# export COMPOSER_ALLOW_SUPERUSER=1; composer show;
```
#### Laravel Octane
- install laravel:
```
# composer create-project --prefer-dist laravel/laravel="^8" .
# composer require laravel/octane
# php artisan octane:install
```
- config file `.env`
```
OCTANE_HTTPS=true
OCTANE_SERVER=swoole or roadrunner
```
- automatically file server update (optional):
```
# apt install npm
# npm config set fetch-retries 5
# npm config set fetch-retry-mintimeout 150000
# npm config set fetch-retry-maxtimeout 300000
# npm config set fetch-timeout 600000
# npm install --save-dev chokidar
```
#### Running
```
# php artisan octane:status|start|stop|reload
```
- command: 
```
--watch (required chokidar)
--server=swoole|roadrunner
--host=127.0.0.1
--port=8000
--workers=5
--task-workers=10
--max-requests=1000
```
#### Results
```
# wrk -t10 -c100 -d5s {{server_local}}
```
- swoole
```
Running 5s test @ http://127.0.0.1:8000
  10 threads and 100 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency     1.38s   197.90ms   1.97s    79.59%
    Req/Sec    11.28      9.05    30.00     62.79%
  139 requests in 5.02s, 2.48MB read
  Socket errors: connect 0, read 0, write 0, timeout 41
Requests/sec:     27.69
Transfer/sec:    505.27KB
```
- roadrunner
```
Running 5s test @ http://127.0.0.1:8000
  10 threads and 100 connections
  Thread Stats   Avg      Stdev     Max   +/- Stdev
    Latency     1.56s   571.06ms   1.98s    80.78%
    Req/Sec    12.91     12.03    50.00     84.46%
  255 requests in 5.03s, 4.54MB read
Requests/sec:     50.67
Transfer/sec:      0.90MB
```
