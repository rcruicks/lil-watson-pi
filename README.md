# lil-watson-pi
linuxing in london - raspberry pi edge connector to Watson with Node-RED

minimal node-red install for headless PiZw/Pi3

download raspbian [jessie full image](https://downloads.raspberrypi.org/raspbian_latest)

currently - this will be `2017-04-10-raspbian-jessie.img`

follow SD image creation [process](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) using the etcher flash utility from [etcher.io](https://etcher.io/)

touch *ssh* file in boot folder

+ macos `touch /Volumes/boot/ssh`
+ Windows `echo > x:\ssh`  (where X is the drive that the boot volume has been mounted to)

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

terminal - resolve raspberrypi.local (ping) - should resolve to a 169.254.x.x [APIPA](http://www.webopedia.com/TERM/A/APIPA.html) address. The name resolution protocol used for this to work properly is [mDNS](https://tools.ietf.org/html/rfc6762) - this is built into macOS, but other operating systems either have a different implementation, or lack native support.

+ Linux
if this does not work automatically, you may benefit from installing *avahi-autoipd*
`sudo apt-get install avahi-autoipd`
this will enable allow the ethernet port to try Automatic address discovery/assignment (dhcp), and if this fails (as would normally happen with a point-to-point ethernet connection, address assignment will fallback to APIPA/link-local.

+ Windows
if name-resolution for raspberrypi.local does not work, the simplest fix is to install Apple's [Bonjour Print Services for windows - currently V2.0.2](https://support.apple.com/kb/dl999?locale=en_US)

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

** extras worth trying **

`sudo apt-get install netatalk`

on *macos* this results in the Pi showing up as a device in the Finder view; something similar on linux?



