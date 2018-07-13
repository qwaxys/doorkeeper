# doorkeeper

Add the following to config.txt

```
#############################
# Doorkeeper extra settings #
#############################  

# Disable Bluetooth and hence using better hardware for Serial
dtoverlay=pi3-disable-bt

# Enable serial pins
enable_uart=1

# Set relay board pins to output and to low (0)
gpio=20,21,26=op,dl

# Set the GSM board power pin to output and to low (0)
# To be togled on for one second later after boot 

gpio=4=op,dl

```
