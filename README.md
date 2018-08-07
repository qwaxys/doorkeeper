# doorkeeper

Add the following to config.txt

```
#############################
# Doorkeeper extra settings #
#############################  

#  Bluetooth on the software serial and the PGIO pins to the dedicated Serial
#  (optional)
dtoverlay=pi3-miniuart-bt

# Enable serial pins
enable_uart=1

# Set relay board pins to output and to high (1)
gpio=20,21,26=op,dl

# Set the GSM board power pin to output and to low (0)
# To be togled on for one second later after boot 
gpio=4=op,dl

```


Install the daemon:


```
sudo apt-get install smstools
```

Edit the config file at /etc/smsd.conf

```
[GSM1]
device = /dev/serial0 
incoming = yes
baudrate = 19200
eventhandler = /home/pi/log.sh
```


Install the parser for the sms messages:


```
sudo apt-get install formail
```


log.sh
```
#!/bin/sh
# This is an example how to use an eventhandler with smsd.

#run this script only when a message was received.
if [ "$1" != "RECEIVED" ]; then exit; fi;

#Extract data from the SMS file
SENDER=`formail -zx From: < $2`
TEXT=`formail -I "" <$2 | sed -e"1d"`

echo "from: $SENDER"  >> /home/pi/log.txt
echo "sms: $TEXT"  >> /home/pi/log.txt
```


First off, update everything, you'll need to be running this in bash or over SSH:
```
sudo apt-get update -y && sudo apt-get dist-upgrade -y && sudo apt-get autoclean && sudo apt-get autoremove
```
next up install LAMP:
```
sudo apt-get install apache2 php7.0 mariadb-server-10.1
```
Then PHPmyAdmin:
```
sudo apt-get install phpmyadmin
```
