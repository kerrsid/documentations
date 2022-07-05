![KERRSID](https://www.girzsebastian.com/kerrsid/kerrsid_logo-long.png)
## CPU Virtualization check
First, you should check if your VPC (Virtual Processor Core) is enabled. You can check it by opening Performance Tab from Task Manager.

![Virtualization Check](https://i.stack.imgur.com/GkDPe.jpg)

If Virtualization is disabled you need to access the UEFI or BIOS(older hardware) and enable both of the options.
To enter the UEFI/BIOS you need to open Settings->Update&Security->Recovery->Advanced Startup. After the PC restarts select Troubleshoot->Advanced Options->Startup Settings->BIOS/UEFI.


# Installations
## Install Docker v4.4.4
**[Get Docker Desktop for Windows](https://desktop.docker.com/win/main/amd64/73704/Docker%20Desktop%20Installer.exe)**

When the installation finishes, Docker starts automatically. The whale ![whale](https://d1q6f0aelx0por.cloudfront.net/icons/whale-x-win.png) in the notification area indicates that Docker is running, and accessible from a terminal. Open Docker by double click on the whale from the notification area, go to Settings->General and make sure the box with ``` Use the WSL 2 based engine``` is checked, and Apply & Restart.
  - Additional links : 
    -  **[Install Docker Desktop on Windows](https://docs.docker.com/docker-for-windows/install/)** 
    -  **[Docker Desktop WSL 2 backend](https://docs.docker.com/docker-for-windows/wsl/)**
    -  **[How To Install and Use Docker on Ubuntu 20-04(Tutorial)](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04)**

*TBD, if wsl engine on distro is not wsl version 2

## Install Ubuntu
Get **Ubuntu 20.04 LTS** From Microsoft Store 

After Ubuntu subsystem has been installed on your local machine open it and you should see a new terminal that has access to your subsystem. Let it config itself.
By installing a subsystem on your current operating system you will integrate this subsystem with the WSL distro. Then go back to Docker Settings->Resources->WSL INTEGRATION and enable the additional distro ```Ubuntu-20.04```, and again Apply & Restart. In case you get an error about your current version of the WSL kernel,  download and install [wsl_update_x64](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi).

  - Additional links : 
    -  **[Download Windows Subsystem for Linux distro packages](https://docs.microsoft.com/en-us/windows/wsl/install-manual)** 

## Install VS Code
**[GET VS Code](https://code.visualstudio.com/sha/download?build=stable&os=win32-x64-user)**

After you have installed VS Code go to **[this link](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl)** and install Remote - WSL. Open again VS Code and press F1 and search ```Remote-WSL: New Window using Distro...``` and select ```Ubuntu-20.04```, it will open a new window that is connected to your subsystem Ubuntu.

## Install MySQL Workbanch
**[Get MySQL Workbanch](https://dev.mysql.com/get/Downloads/MySQLGUITools/mysql-workbench-community-8.0.23-winx64.msi)**.
In case you don't have it installed [Visual C++](https://aka.ms/vs/16/release/vc_redist.x64.exe)


## Install Apache, PHP, and MySQL into your subsystem
### Apache
To install Apache into your subsystem you need to open ```Ubuntu 20.04 LTS``` and run these commands in this sequence:
```sh
sudo apt update
sudo apt upgrade
sudo apt install apache2
sudo service apache2 start
sudo a2enmod headers
sudo a2enmod rewrite
```
To check if Apache is running you run this command:
```sh
sudo service apache2 status
```
To start Apache respective to stop Apache you run this commands:
```sh
sudo service apache2 start
sudo service apache2 stop
```
To check if your Apache Server is working insert the start command and type on into browser localhost and you should get a ```Apache2 Ubuntu Default Page```.

  - Additional links : 
    -  **[Install and Configure Apache](https://ubuntu.com/tutorials/install-and-configure-apache#1-overview)** 

### PHP
Install PHP 7.2 using the following commands:

```sh
sudo add-apt-repository -y ppa:ondrej/php
sudo apt-get update
sudo apt-get install php7.2 php7.2-cli php7.2-common
```
To install extensions:
```sh
sudo apt-get install php7.2-curl php7.2-gd php7.2-json php7.2-mbstring php7.2-intl php7.2-mysql php7.2-xml php7.2-zip php7.2-dev
```
Use the following command to check the PHP version installed on your server:
```sh
php -v
```
  - Additional links : 
    -  **[How to Install PHP 7.2 on Ubuntu 20.04](https://www.rosehosting.com/blog/how-to-install-php-7-2-on-ubuntu-16-04/)** 

### MySQL
Open VS Code with Ubuntu distro and open the folder ```home/```, create a new file call ```docker-compose.yml``` 
(!By default this file will be read-only. Use chmod command [$ sudo chmod -R 777 fileName] from VS Code terminal to make it writable) 
and insert:
```docker
version: "3.9"
services:
    mysql:
        image: mysql:5.7
        restart: always
        command: --default-authentication-plugin=mysql_native_password
        environment:
            - MYSQL_ROOT_PASSWORD=your_rootpassword
            - MYSQL_DATABASE=tehnomir
            - MYSQL_TCP_PORT=3307
        ports:
            - 3307:3307
        volumes:
            - mysqldata:/var/lib/mysql
    redis:
        image: redis
        container_name: redis_cache
        ports:
            - 6379:6379    
volumes:
    mysqldata:
```
Open a new terminal in VS Code, ``` Terminal->New Terminal or Ctrl+Shift+` ```, and run in terminal:
```sh
docker-compose up -d
```
To see all the images that are currently running insert:
```sh
docker ps
```
After both images finish to pull, you need to make a new MySQL connection with your MySQL Workbench and your container MySQL. Open the MySQL Workbench and click on the plus icon near MySQL Connections, it should open a new window called Setup New Connection. Insert into all the fields that should be required, from information that you have sees by using ```docker ps```.
