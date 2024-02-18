# AndroidPHP

## Note
**This method has been tested on Android 9-13 by myself**

This php binary is for 64bit ONLY.

This php binary can still connect to the Internet.
To connect to the Internet on Android, you need to prepare resolv.conf and cacert.pem, which can be found in the below.
To run the server on Android, you need to prepare PocketMine-MP by yourself.

## Required Applications
In this section, we will use "Termux" as a terminal emulator.

You can get it [here](https://github.com/termux/termux-app?)

## Installation
### Download php
The PHP can be downloaded from the [release page](https://github.com/JankleDev/AndroidPHP/releases).

![img1](https://user-images.githubusercontent.com/17798680/73345192-f9324300-42c6-11ea-9036-c162bf03c5bd.png)

#### Move php to your server's folder
Now launch "Termux".
To execute the following command:
 - Long press the screen until you see text selection appear and then select "Paste".

```
cd $HOME
mkdir pmmp
```

This will create a folder named 'pmmp'

#### Make php executable

Long press the screen until you see text selection appear and then select "Paste".

```
cp /storage/emulated/0/Download/php /data/data/com.termux/files/home/pmmp/php
chmod 777 $HOME/pmmp/php
```
This will copy paste the php binary you downloaded to your server's folder. (if you have a downloaded php some where else you might have to edit the command)

#### Download various files to connect to the Internet
Please Download the following files (resolv.conf, cacert.pem, php.ini) from the following download links.

##### Direct downloads
- [cacert.pem](https://curl.haxx.se/ca/cacert.pem)
- [resolv.conf](https://www.dropbox.com/s/xwta1aobds1557e/resolv.conf?dl=1)
- [php.ini](https://github.com/JankleDev/AndroidPHP/releases/latest/download/php.ini)

#### Placing the various files

Please execute the following command.
```
cd $HOME/pmmp/
mkdir config
cd /storage/emulated/0/Download/
mv php.ini $HOME/pmmp/config/
mv resolve.conf $HOME/pmmp/config/
mv cacert.pem $HOME/pmmp/config/
```

#### Install PocketMine-MP
Please download "PocketMine-MP.phar" from the following link.
https://github.com/pmmp/PocketMine-MP/releases/latest/download/PocketMine-MP.phar

After downloading the file please execute the following command.
```
cd /storage/emulated/0/Download/
mv PocketMine-MP.phar $HOME/pmmp/
```

#### Launch PocketMine-MP
If your running it for first time then execute the following command.
```
cd $HOME/pmmp/
env LESMI_RESOLV_CONF_DIR=$HOME/pmmp/config/resolv.conf SSL_CERT_FILE=$HOME/pmmp/config/cacert.pem $HOME/pmmp/php -c $HOME/pmmp/config/php.ini $HOME/pmmp/PocketMine-MP.phar
```

If you have already ran it one time the use the following command.
```
$HOME/PocketMine/bin/php -c $HOME/PocketMine/config/php.ini $HOME/PocketMine/PocketMine-MP.phar
```

The LESMI_RESOLV_CONF_DIR environment variable is created by the modified musl (gcc).

<hr />