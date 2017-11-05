# Programmable Wireless Raspberry Pi ppp scripts
Programmable Wireless is a set of developer-first tools to deploy and manage fleets of wireless devices, powering connectivity for the Internet of Things and enabling highly customized Communications use cases.

This repository includes a group of ppp scripts to connect a Raspberry Pi to the Internet using a USB cellular modem. You can learn more about Programmable Wireless from the [Programmable Wireless Documentation](https://www.twilio.com/docs/api/wireless) and how to connect a USB modem to a Raspberry Pi by following this [guide](https://www.twilio.com/docs/api/wireless/iot-guides/connect-using-raspberry-pi-and-cellular-usb-modem).
## Requirements
You will need to download and install software packages on your Raspberry Pi before you can use your unlocked cellular USB modem. Follow along with this repository's accompanying [guide](https://www.twilio.com/docs/api/wireless/iot-guides/connect-using-raspberry-pi-and-cellular-usb-modem) if you need additional help. The easiest option is to get a [Raspberry Pi WiFi dongle](https://www.amazon.com/Official-Raspberry-Pi-WiFi-dongle/dp/B014HTNO52/ref=sr_1_1?ie=UTF8&qid=1500054954&sr=8-1&keywords=Raspberry+Pi+Official+WiFi+Adapter) if your device does not have built in wifi.
## Step 1. Install packages on Raspberry Pi
Type the following in a terminal:
```
sudo apt-get update
sudo apt-get install ppp usb-modeswitch
```
## Step 2. Determine current mode of your USB modem
Follow along with this repository's accompanying [guide](https://www.twilio.com/docs/api/wireless/iot-guides/connect-using-raspberry-pi-and-cellular-usb-modem) to determine if your USB modem is in the correct mode.
## Step 3. Install ppp scripts
Type the following in a terminal:
```
wget https://github.com/twilio/wireless-ppp-scripts/archive/master.zip
unzip master.zip
cd wireless-ppp-scripts
sudo cp chatscripts/twilio /etc/chatscripts
sudo cp peers/twilio /etc/ppp/peers
```
Thats it for the scripts. You can remove master.zip and wireless-ppp-scripts by typing the following in a terminal:
```
rm -rf master.zip
rm -rf wireless-ppp-scripts
```
## Step 4. Shut down wifi if up
Type the following in a terminal:
```
sudo ifconfig wlan0 down
```
## Step 5. Connect to the cellular network
Type the following in a terminal:
```
sudo pon twilio
```
## Step 4. Confirm
Your USB modem should now be connected to the Internet! Try going to a web page or ping Twilio. Type the following in a terminal to ping www.twilio.com:
```
ping -c 3 www.twilio.com
```
## You’re connected!
You inserted a Twilio SIM card into your cellular USB modem and configured ppp to run at boot. Take a look at the other interesting things you can do with a Raspberry Pi such as [sending machine-to-machine Commands](https://www.twilio.com/docs/api/wireless/sending-machine-machine-commands) or creating a cellular connected [security camera](https://www.twilio.com/wireless/blueprints).
