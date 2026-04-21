# Linux Commands (Detailed Explanations)

This page explains Linux commands in a way that a complete beginner can understand.
Each command includes:
- What it does
- When to use it
- Why it fixes problems
- How to type it correctly
- Common mistakes
- Real examples from my lab work

- ## ip a

### What it does
Shows all network interfaces and their IP addresses.

### When to use it
Use this when:
- You need to check your Linux VM’s IP address
- You’re troubleshooting network issues
- You’re configuring netplan/YAML

### Why it fixes things
It tells you exactly what IP the system has, which is required for:
- SSH
- Apache
- osTicket
- DNS
- Routing

### How to type it
ip a

### Common mistakes
- Typing ifconfig (not installed by default)
- Forgetting to run it after changing YAML/netplan

- ## sudo apt update

### What it does
Refreshes the list of available software packages.

### When to use it
Use this before installing ANYTHING:
- Apache
- PHP
- MariaDB
- Python packages

### Why it fixes things
If the package list is old, installs will fail or install outdated versions.

### How to type it
sudo apt update

## sudo apt upgrade -y

### What it does
Installs all available updates for the system.

### When to use it
Use this after:
- A fresh install
- Long periods without updates
- Before installing major software

### Why it fixes things
Keeps the system secure and prevents dependency issues.

### How to type it
sudo apt upgrade -y

## sudo apt install <package>

### What it does
Installs software from Ubuntu’s repositories.

### When to use it
Use this to install:
- apache2
- php
- mariadb-server
- nano
- htop

### Why it fixes things
If a service or tool is missing, this installs it.

### How to type it
sudo apt install apache2
sudo apt install php php-mysql php-xml php-mbstring
sudo apt install mariadb-server

### Common mistakes
- Forgetting sudo
- Misspelling package names

- ## systemctl status <service>

### What it does
Shows whether a service is running, stopped, or failed.

### When to use it
Use this when:
- Apache won’t load
- MariaDB won’t start
- osTicket shows errors
- You edited config files

### Why it fixes things
It tells you:
- If the service is running
- If it crashed
- If there are errors

### How to type it
systemctl status apache2
systemctl status mariadb

## systemctl restart <service>

### What it does
Restarts a service.

### When to use it
Use this after:
- Editing config files
- Installing PHP modules
- Changing Apache settings
- Fixing MariaDB permissions

### Why it fixes things
Services don’t reload changes automatically.

### How to type it
sudo systemctl restart apache2
sudo systemctl restart mariadb

## nano <file>

### What it does
Opens a text editor inside the terminal.

### When to use it
Use this to edit:
- YAML/netplan files
- PHP config files
- osTicket config
- Python scripts

### Why it fixes things
Linux config files must be edited manually.

### How to type it
sudo nano /etc/netplan/00-installer-config.yaml
sudo nano /var/www/html/osticket/include/ost-config.php

## netplan apply

### What it does
Applies network configuration changes.

### When to use it
Use this after editing:
- Static IP settings
- DNS settings
- Network interface names

### Why it fixes things
Linux does not apply YAML changes automatically.

### How to type it
sudo netplan apply

### Common mistakes
- YAML indentation errors
- Wrong interface name (ens33, eth0, etc.)

- ## MariaDB Commands

### What they do
Manage databases, users, and permissions.

### Commands used in my lab:
sudo mysql -u root -p
CREATE DATABASE osticket;
CREATE USER 'ostuser'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON osticket.* TO 'ostuser'@'localhost';
FLUSH PRIVILEGES;
EXIT;

### When to use them
During osTicket setup or any database-backed application.

### Why they fix things
osTicket cannot run without:
- A database
- A database user
- Correct permissions

- ## File Navigation Commands

### ls
Lists files in the current directory.

### cd <folder>
Moves into a directory.

### pwd
Shows your current location.

### mkdir <folder>
Creates a new folder.

### rm <file>
Deletes a file.

### Why they matter
You used these during:
- Python project
- osTicket file setup
- Moving upload folder into Apache

- ## mv <source> <destination>

### What it does
Moves or renames files and folders.

### When to use it
Used during osTicket setup:
sudo mv upload /var/www/html/osticket

### Why it fixes things
Apache needs the osTicket files in the web directory.

