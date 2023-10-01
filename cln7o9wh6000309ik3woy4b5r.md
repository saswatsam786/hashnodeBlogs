---
title: "🚀🌐 DevOps 2.3: Launch WordPress Template on Ubuntu 🖥️📝"
seoTitle: ""WordPress Deployment on Ubuntu""
seoDescription: "Master the art of deploying WordPress on Ubuntu with DevOps 2.3. Learn to create dynamic websites effortlessly."
datePublished: Sun Oct 01 2023 16:24:35 GMT+0000 (Coordinated Universal Time)
cuid: cln7o9wh6000309ik3woy4b5r
slug: devops-23-launch-wordpress-template-on-ubuntu
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696177296281/2fa74110-a2f5-44f9-b5cb-53026b7e0ed7.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1696177355300/13fe0468-ed34-46fd-84a5-92a284fa3e6e.png
tags: ubuntu, linux, wordpress, devops, apache

---

# Introduction

In "DevOps 2.3: Launch WordPress Template on Ubuntu," you'll learn how to deploy a WordPress website using Ubuntu, unlocking the power of dynamic content creation and management. Explore the step-by-step process and get ready to bring your online presence to life!

Follow the following commands and uncomment the private network, public network, and memory allocation line as shown in my [previous blog](https://saswatblogs.hashnode.dev/launch-your-website-on-linux).

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1693129880973/4d60517d-0d35-419a-ac5a-860e7067840e.png align="center")

Do `vagrant up` and `vagrant ssh` to start the VM.

Do `sudo -i` to switch to the root user.

Enter the following commands

```bash
sudo apt install apache2 \
                 ghostscript \
                 libapache2-mod-php \
                 mysql-server \
                 php \
                 php-bcmath \
                 php-curl \
                 php-imagick \
                 php-intl \
                 php-json \
                 php-mbstring \
                 php-mysql \
                 php-xml \
                 php-zip
```

```bash
sudo mkdir -p /srv/www
sudo chown www-data: /srv/www
curl https://wordpress.org/latest.tar.gz | sudo -u www-data tar zx -C /srv/www
```

The given commands perform the following tasks:

1. `sudo mkdir -p /srv/www`: Creates a directory named "www" inside the "/srv" directory. The `-p` flag ensures that parent directories are created if they don't exist.
    
2. `sudo chown www-data: /srv/www`: Changes the ownership of the "/srv/www" directory to the "www-data" user and group. This is typically done to allow the webserver to have proper access to the directory.
    
3. `curl` [`https://wordpress.org/latest.tar.gz`](https://wordpress.org/latest.tar.gz) `| sudo -u www-data tar zx -C /srv/www`: This command involves multiple steps:
    
    * `curl` [`https://wordpress.org/latest.tar.gz`](https://wordpress.org/latest.tar.gz): Uses the `curl` command to download the latest version of WordPress as a compressed tarball.
        
    * `|`: Pipes the downloaded tarball to the next command.
        
    * `sudo -u www-data tar zx -C /srv/www`: Extracts the downloaded tarball using the `tar` command and places the contents into the "/srv/www" directory. The `-C` flag specifies the target directory for extraction. The command is executed with the user context of "www-data" using `sudo`, which ensures that the extracted files are owned by the appropriate user and group.
        

In summary, these commands create a directory structure, set proper ownership, and download/extract the latest version of WordPress into the designated directory. This is a common process when setting up a web server to host a WordPress website.

`vim /etc/apache2/sites-available/wordpress.conf` - Paste the following command in the command line and press enter.

Paste the below content vim editor and paste the below content.

```bash
<VirtualHost *:80>
    DocumentRoot /srv/www/wordpress
    <Directory /srv/www/wordpress>
        Options FollowSymLinks
        AllowOverride Limit Options FileInfo
        DirectoryIndex index.php
        Require all granted
    </Directory>
    <Directory /srv/www/wordpress/wp-content>
        Options FollowSymLinks
        Require all granted
    </Directory>
</VirtualHost>
```

`sudo a2ensite wordpress` - Enter this command in the terminal, to enable the WordPress website.

`sudo a2enmod rewrite` - Enter the command to set up the redirect rule.

`sudo a2dissite 000-default` - To disable the default web page.

`sudo service apache2 reload` - Then reload the apache2 service.

### Configure Database:

`sudo mysql -u root` - Configures SQL.

`CREATE DATABASE wordpress;` - Create the database.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696172705216/bd16020b-8ee9-45a7-ba01-811d1d94dc9a.png align="center")

`CREATE USER` [`wordpress@localhost`](mailto:wordpress@localhost) `IDENTIFIED BY '<your-password>';` - This will create a user wordpress in local machine identified by a given password.

`GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,DROP,ALTER ON wordpress.* TO` [`wordpress@localhost`](mailto:wordpress@localhost)`;` - Grant the permission of the commands on wordpress database to the wordpress@localhost user.

And then `quit`.

### Configure WordPress to connect to the database -

`sudo -u www-data cp /srv/www/wordpress/wp-config-sample.php /srv/www/wordpress/wp-config.php` - Add the configuration file.

Next, set the database credentials in the configuration file (*do not* replace `database_name_here` or `username_here` in the commands below. *Do* replace `<your-password>` with your database password.):

```bash
sudo -u www-data sed -i 's/database_name_here/wordpress/' /srv/www/wordpress/wp-config.php
sudo -u www-data sed -i 's/username_here/wordpress/' /srv/www/wordpress/wp-config.php
sudo -u www-data sed -i 's/password_here/<your-password>/' /srv/www/wordpress/wp-config.php
```

`vim /srv/www/wordpress/wp-config.php` - To check if db\_name, username, and password are correct. If not then change it.

`sudo -u www-data nano /srv/www/wordpress/wp-config.php` - Find the below and delete it.

```bash
define( 'AUTH_KEY',         'put your unique phrase here' );
define( 'SECURE_AUTH_KEY',  'put your unique phrase here' );
define( 'LOGGED_IN_KEY',    'put your unique phrase here' );
define( 'NONCE_KEY',        'put your unique phrase here' );
define( 'AUTH_SALT',        'put your unique phrase here' );
define( 'SECURE_AUTH_SALT', 'put your unique phrase here' );
define( 'LOGGED_IN_SALT',   'put your unique phrase here' );
define( 'NONCE_SALT',       'put your unique phrase here' );
```

And insert below.

```bash
define('AUTH_KEY',         'Rd;4A-9a.T@0`j0|/-e!Bg|W?HS,.`++&ii_g Mi-+r#YII9B]kg23H=7#~~K+ C');
define('SECURE_AUTH_KEY',  '6YY:s&ETLH<C+H6x5 !v{qfy:HL,cxzK-36CZ!|/n~IX@z{&;N]Pv@uP)OkRD:p:');
define('LOGGED_IN_KEY',    'oby>Z;$;8G01-OfVS+n_%_E6e>%/lH*DXMd?C@+%b&xTV-uKM3/mG|1H22CbZ^j8');
define('NONCE_KEY',        'A9;ekXiKwo+xMv+NlyMgYSR-l,4>QFC@+;}]<{Ama0)pD:~]889bI~jCH=/o5-_7');
define('AUTH_SALT',        'J`n.}FoqL`Vu-M@@8:LS%t /Ktwd`i/mnGok@e+VHnoBPTa{N@ g%AC$B+M|+w;z');
define('SECURE_AUTH_SALT', '.1WDTUYeG(].>tMfX{GS >+gv*_sMmE+mmJzzyLcnS54c1D~yZ-QyF9LLq>/xMM_');
define('LOGGED_IN_SALT',   'OZhGqrp!)(Q+iIRq1]-@hR-:z_R%g-bhgnx*Ko_;#Q{@O@0=0u5{jEmm%C]-a6Dy');
define('NONCE_SALT',       'ac!x^<f|_;k-P<FmZ0Lx,1wdcsrZtn?RlgDP5b0F`GZ+O_{fliOZ]NcCf-%Po Rg');
```

### Configure WordPress:

`ip addr show` - To get the ip address

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696176668425/62631a43-12a1-4d17-a0e8-3f100a3f836d.png align="center")

Copy the address and paste it in your browser.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696176720139/ad6746d6-b8de-420c-93da-999ced2f2c77.png align="center")

For any other issues check this link out for reference - [https://ubuntu.com/tutorials/install-and-configure-wordpress#1-overview](https://ubuntu.com/tutorials/install-and-configure-wordpress#1-overview)

# Conclusion:

In conclusion, mastering the art of launching a WordPress template on Ubuntu is a crucial step for any DevOps enthusiast or web developer. This process empowers you to efficiently deploy and manage dynamic websites with ease. By understanding the intricacies of this deployment, you gain valuable skills that can be applied to various web projects, enhancing your capabilities in the ever-evolving world of DevOps and web development.