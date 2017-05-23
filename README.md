# lil-watson-pi
linuxing in london - raspberry pi edge connector to Watson with Node-RED

minimal node-red install for headless PiZ

raspbian jessie lite
etcher flash utility

[Pi ethernet over USB](http://www.circuitbasics.com/raspberry-pi-zero-ethernet-gadget/)

1 update config.txt
1 update cmdline.txt

touch *ssh* file in boot folder

enable ICS on host

plug in Pi - via USB port NOT power port

terminal - resolve raspberrypi.local (ping)

terminal remote - `ssh pi@raspberrypi.local`

raspi-config 
- Interfaces - enable ssh
- expand file system

`reboot`

reconnect with ssh 

install python, and pip

install [base requirement for python](https://www.raspberrypi.org/documentation/linux/software/python.md) to enable support for [sense hat](https://www.raspberrypi.org/products/sense-hat/)  in Node-RED

![sense hat](https://www.raspberrypi.org/app/uploads/2016/02/Sense-HAT-web.jpg)

sudo apt-get install sense-hat
sudo pip-3.2 install pillow




