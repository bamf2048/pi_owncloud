# Run Owncloud on a Raspberry Pi

## DIY selfhosted Dropbox

Use these instructions to install the Owncloud server (record all your accounts and passwords):

```
sudo apt-get update; sudo apt-get upgrade -y
sudo apt-get install apache2 php5 php5-fpm php5-gd php5-curl php5-mysql mysql-server -y
```

Set your mysql password when prompted. Customize `newuser`, `password` and `database_name`.

```
sudo service apache2 restart
cd /var/www/html; ls
sudo rm index.html
sudo chown -R www-data:www-data /var/www/
mysql -u root -p
CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';
CREATE DATABASE `database_name`;
GRANT ALL PRIVILEGES ON database_name.* TO 'newuser'@'localhost';
FLUSH PRIVILEGES;
```

Open in a browser by typing in it's ip address. Click the owncloud setup php file.

If php5 isn't running, `chmod 775 setup-owncloud.php` the owncloud php or run through installing php5 again: https://askubuntu.com/questions/451708/php-script-not-executing-on-apache-server

----

https://www.pi-supply.com/make/build-your-own-cloud-storage-file-server-with-a-raspberry-pi/
