# Getting Started

## Drone Install
On drone install:

TODO: Instruction on how to install drone software on SD card

Log into drone using SSH, and install controller software.

From fatcnt directory download software https://github.com/Ryder-Robots/fatcnt/releases/tag/0.0.3


# Install Required Libraries

```
sudo apt-get install libusb-dev isc-dhcp-server -y
```

TODO: Add pre-deploy steps including how to install dlib


fatcnt_0.0.3_arm64.deb



## Setup Wifi Hotspot

```
vi /etc/dhcpcd.conf

"
interface wlan0
static ip_address=192.168.1.35/24
static routers=192.168.1.35
static domain_name_servers=192.168.1.35
"

vi /etc/init.d/isc-dhcp-server
INTERFACESv4="wlan0"

sudo nmcli device wifi hotspot ssid skuld002-0001 password dizzycheese310 ifname wlan0

```


