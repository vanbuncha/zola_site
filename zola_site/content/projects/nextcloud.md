+++
title = "File service - Nextcloud"
date = 2023-03-09

[taxonomies]
categories = ["software"]

[extra]
+++

Self hosted file service

# Part one -- subdomain

As a web developer, I am always looking for new ways to improve my setup and make my web development projects more accessible to others. Recently, I decided to try and add a subdomain to my Raspberry Pi Apache server using Cloudflare Tunnel, but unfortunately, I did not have success. Here is my experience.

First, I set up my Raspberry Pi with Apache, following various tutorials on the web. I also configured my router to forward incoming requests to the Raspberry Pi’s IP address, so that the web server could be accessed from the internet. Next, I signed up for a Cloudflare account and set up a tunnel to my Raspberry Pi using the Cloudflare CLI. This was relatively easy, and I was able to connect to my web server using the tunnel URL provided by Cloudflare.

Now, I wanted to add a subdomain to my setup. I had already registered a domain name with a popular registrar and set up Cloudflare as my DNS provider. I added an A record pointing to my Raspberry Pi’s IP address, and set up a CNAME record pointing to the tunnel URL provided by Cloudflare. I also added a Page Rule to forward all traffic to my subdomain to the tunnel URL. However, when I tried to access my subdomain, I was greeted with a 502 Bad Gateway error.

I spent hours troubleshooting the issue, checking my Apache configuration files, and trying different combinations of DNS records and Page Rules. I also consulted various online forums and documentation, but I could not find a solution. Eventually, I realized that the issue might be with Cloudflare Tunnel itself, and not my setup.

I discovered that Cloudflare Tunnel does not support subdomains out of the box. While it is possible to use subdomains with Cloudflare Tunnel, it requires additional configuration and setup, which is beyond the scope of this blog post. I was disappointed that my initial attempt to add a subdomain to my Raspberry Pi Apache + Cloudflare Tunnel setup did not succeed, but I learned a valuable lesson about the limitations of certain tools and services.

p.s This could be all avoided with better router.

# Part two -- Installing Nextcloud and its usecases

Nextcloud is a free and open-source software platform for creating and hosting file hosting and communication services on your own servers. It offers features like file sharing, calendar, contact management, and more.

To install Nextcloud on a Raspberry Pi, I followed these steps:

Preparing the Raspberry Pi: First, I prepared my Raspberry Pi by installing the latest version of Raspberry Pi OS and enabling SSH access.
Installing Apache and PHP: I installed Apache web server and PHP on my Raspberry Pi using the following command in the terminal:
sudo apt-get install apache2 php libapache2-mod-php

Creating a Virtual Host: Next, I created a virtual host for Nextcloud by creating a new configuration file in the Apache sites-available directory using the following command:
sudo nano /etc/apache2/sites-available/nextcloud.conf

I added the following lines to the configuration file:

bash
```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/nextcloud/
        Servvanguyen.info
        <Directory /var/www/nextcloud/>
                Options +FollowSymlinks
                AllowOverride All
                Require all granted
                <IfModule mod_dav.c>
                        Dav off
                </IfModule>
                SetEnv HOME /var/www/nextcloud
                SetEnv HTTP_HOME /var/www/nextcloud
        </Directory>
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
I saved the configuration file and enabled the site using the following command:

sudo a2ensite nextcloud.conf

Downloading and Installing Nextcloud: I downloaded the latest version of Nextcloud from their website and copied the files to the web root directory /var/www/nextcloud/ on my Raspberry Pi using the following commands:
kotlin
Copy code
wget https://download.nextcloud.com/server/releases/nextcloud-22.3.0.zip
sudo unzip nextcloud-22.3.0.zip -d /var/www/
sudo chown -R www-data:www-data /var/www/nextcloud/
Setting Up a Database: Next, I set up a MySQL database for Nextcloud using the following commands:
csharp
Copy code
sudo apt-get install mariadb-server php-mysql
sudo mysql_secure_installation
sudo mysql -u root -p
I created a new database and user for Nextcloud, and granted the user permissions to the database:
```
CREATE DATABASE nextcloud;
CREATE USER 'nextclouduser'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON nextcloud.* TO 'nextclouduser'@'localhost';
FLUSH PRIVILEGES;
exit;
```
Completing the Installation: Finally, I accessed the Nextcloud installation wizard by visiting vanguyen.info/nextcloud in my web browser. I entered the database details and created an administrator account, and then completed the installation.
That's it! Now, I can access my Nextcloud instance by visiting vanguyen.info/nextcloud on my Raspberry Pi.

<a href="vanguyen.info/nextcloud">Link to Nextcloud</a>

# To-Do List

- [ ] Use external storage
- [ ] set up SMTP service


