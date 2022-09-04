## LEMP STACK IMPLEMENTATION
 ## Installation of NGINX
`sudo apt update`
sudo apt install nginx``
`sudo systemctl status nginx`
	![Installation of NGINX](./images/NGINX-Confirmation.png)
    	![Website](./images/NGINX-WEBSITE.png)
## Installation of MYSQL
	`sudo apt install mysql-server`
    	`sudo mysql`
        	`ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';`
            	`sudo mysql_secure_installation`
               	`sudo mysql -p`
   ![MYSQL](./images/MYSQL-INSTALLATION.png)   
      ## Installation of PHP
      `sudo apt install php-fpm php-mysql`
           `sudo mkdir /var/www/projectLEMP`
             `sudo chown -R $USER:$USER /var/www/projectLEMP`
              `sudo nano /etc/nginx/sites-available/projectLEMP`
              `#/etc/nginx/sites-available/projectLEMP

server {
    listen 80;
    server_name projectLEMP www.projectLEMP;
    root /var/www/projectLEMP;

    index index.html index.htm index.php;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php8.1-fpm.sock;
     }

    location ~ /\.ht {
        deny all;
    }

}
``sudo ln -s /etc/nginx/sites-available/projectLEMP /etc/nginx/sites-enabled/`
`sudo nginx -t`
`nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful`
`sudo unlink /etc/nginx/sites-enabled/default`
`sudo systemctl reload nginx`
`sudo echo 'Hello LEMP from hostname' $(curl -s http://169.254.169.254/latest/meta-data/public-hostname) 'with public IP' $(curl -s http://169.254.169.254/latest/meta-data/public-ipv4) > /var/www/projectLEMP/index.html`
![PHP](./images/PHP-INSTALLATION.png)
## Testing PHP with NGINX
	`sudo nano /var/www/projectLEMP/info.php`
    	`<?php
phpinfo();
`![Testing](./images/FINAL-PHP.png)