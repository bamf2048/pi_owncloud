# Run Owncloud on a Raspberry Pi

## DIY selfhosted Dropbox

Use these instructions to install the Owncloud server (record all your accounts and passwords). Set your mysql password when prompted. Customize `newuser`, `password` and `database_name`.

```
sudo apt-get update; sudo apt-get upgrade -y
sudo apt-get install apache2 php5 php5-fpm php5-gd php5-curl php5-mysql mysql-server -y
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

```
sudo apt-get install apache2 php5 libapache2-mod-php5
a2query -m php5
sudo a2enmod php5
sudo service apache2 restart
```

Try opening the script in browser again.

----

https://www.pi-supply.com/make/build-your-own-cloud-storage-file-server-with-a-raspberry-pi/

Verified running on Pi 1 model B.
