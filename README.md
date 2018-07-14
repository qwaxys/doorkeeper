# doorkeeper

Add the following to config.txt

```
#############################
# Doorkeeper extra settings #
#############################  

#  Bluetooth on the software serial and the PGIO pins to the dedicated Serial
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

