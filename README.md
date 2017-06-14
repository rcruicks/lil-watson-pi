# lil-watson-pi
linuxing in london - raspberry pi edge connector to Watson with Node-RED

minimal node-red install for headless PiZw/Pi3

download raspbian [jessie full image](https://downloads.raspberrypi.org/raspbian_latest)

currently - this will be `2017-04-10-raspbian-jessie.img`

follow SD image creation [process](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) using the etcher flash utility from [etcher.io](https://etcher.io/)

touch *ssh* file in boot folder

+ macos `touch /Volumes/boot`
+ Windows `echo > x:\ssh`

```
for PiZw, there is no onboard ethernet, so exploit recent support for ethernet gadget
```
[Pi ethernet over USB](http://www.circuitbasics.com/raspberry-pi-zero-ethernet-gadget/)
```
- update config.txt
- update cmdline.txt
```

+ plug in PiZw - via USB port **NOT** power port
+ plug in Pi3 - via ethernet

terminal - resolve raspberrypi.local (ping) - should resolve to a 169.254.x.x [APIPA](http://www.webopedia.com/TERM/A/APIPA.html) address

terminal remote - `ssh pi@raspberrypi.local`

create an entry for local WiFi network
`sudo wpa_passphrase CodeNode welovecode | sudo tee -a /etc/wpa_supplicant/wpa_supplicant.conf`

`sudo raspi-config` 

![raspi-config](/images/raspi-config-menu.png)

- Interfaces - enable ssh
- Hostname - pick your name -- *this will override the name raspberrypi*
- Password - set new password for `pi`
- Advanced - Audio - set to 3.5mm
Select *Finish*

`sudo reboot`

reconnect with ssh (using new *hostname* - should resolve to wifi connection)

**work in progress**

`sudo systemctl enable nodered.service`

`sudo systemctl start nodered.service`

check via *hostname:1880*

install python, and pip

install [base requirement for python](https://www.raspberrypi.org/documentation/linux/software/python.md) to enable support for [sense hat](https://www.raspberrypi.org/products/sense-hat/)  in Node-RED

![sense hat](https://www.raspberrypi.org/app/uploads/2016/02/Sense-HAT-web.jpg)

sudo apt-get install sense-hat
sudo pip-3.2 install pillow




