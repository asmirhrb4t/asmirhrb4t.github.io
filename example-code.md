---
layout: default
title: WordPress Installation Example
nav_order: 4
---

# Installing WordPress on a Linux Server

A common way to create websites is by using a Content Management System (CMS).
One of the most widely used CMS platforms is WordPress.

WordPress is usually installed on a Linux server together with a web server,
a database system, and PHP. This example shows how WordPress can be installed
on a minimal Linux system without a graphical interface.

This installation example assumes a server running Debian 13 or a similar
Debian-based Linux distribution.

---

# Required Components

To run WordPress, the following software components are required:

- Apache – Web server that delivers the website
- MariaDB – Database server used to store website data
- PHP – Server-side scripting language used by WordPress

This combination is often referred to as a **LAMP stack**.

---

# Step 1 – Update the System

Before installing software, update the package lists and upgrade installed packages.

```bash
sudo apt update
sudo apt upgrade
```

---

# Step 2 – Install Apache Web Server

Install the Apache web server:

```bash
sudo apt install apache2
```

Check the service status:

```bash
sudo systemctl status apache2
```

---

# Step 3 – Install MariaDB Database Server

WordPress requires a database to store posts, pages, and user information.

Install MariaDB:

```bash
sudo apt install mariadb-server
```

Run the security configuration:

```bash
sudo mysql_secure_installation
```

---

# Step 4 – Install PHP

WordPress is written in PHP and requires several PHP modules.

Install PHP and the required database extension:

```bash
sudo apt install php php-mysql
```

Check the installed PHP version:

```bash
php -v
```

---

# Step 5 – Download WordPress

Download the latest WordPress release:

```bash
wget https://wordpress.org/latest.tar.gz
```

Extract the archive:

```bash
tar -xvzf latest.tar.gz
```

---

# Step 6 – Move WordPress to the Web Directory

Move WordPress to the Apache web root:

```bash
sudo mv wordpress /var/www/html/
```

Set correct permissions:

```bash
sudo chown -R www-data:www-data /var/www/html/wordpress
```

---

# Step 7 – Create a Database for WordPress

Open the MariaDB shell:

```bash
sudo mysql
```

Create a database and user:

```sql
CREATE DATABASE wordpress;
CREATE USER 'wpuser'@'localhost' IDENTIFIED BY 'securepassword';
GRANT ALL PRIVILEGES ON wordpress.* TO 'wpuser'@'localhost';
FLUSH PRIVILEGES;
EXIT;
```

---

# Step 8 – Complete the Installation

After configuring the server, open a browser and navigate to:

```
http://your-server-ip/wordpress
```

The WordPress setup wizard will guide you through the remaining configuration.

---

# Summary

WordPress can be installed on a minimal Linux server without a graphical interface
using only the command line. This demonstrates how dynamic websites created with
a CMS differ from static websites generated with tools like Jekyll.
