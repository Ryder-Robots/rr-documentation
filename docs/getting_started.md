# Getting Started

## Drone Install
On drone install:

TODO: Instruction on how to install drone software on SD card

Log into drone using SSH, and install controller software.

From fatcnt directory download software https://github.com/Ryder-Robots/fatcnt/releases/tag/0.0.3


### Install Required Libraries

```
sudo apt-get install libusb-dev -y
```

TODO: Add pre-deploy steps including how to install dlib


fatcnt_0.0.3_arm64.deb

### Setup Wifi Hotspot (on drone)

WIFI servers are used to communicate with the drone, as of yet the configuration for the developer server does
not allow for LAN communication with the drone do dnsmaq and hostapd will need to be shutdown, in order to update the
drone.

However you can use LAN to communicate with the drone to execute these commands.

```
sudo systemctl stop dnsmasq
sudo systemctl stop hostapd
```

On drone perform the following, after logging via Ethernet to LAN
```
sudo apt install dnsmasq hostapd -y
sudo systemctl stop dnsmasq
sudo systemctl stop hostapd
```


```
no-resolv
no-poll
interface=eth0
no-hosts
dhcp-range=192.168.0.50,192.168.0.150,255.255.255.0,12h
```

### DHCP Server
```
sudo service isc-dhcp-server stop
sudo apt install dnsmasq iptables iptables-persistent
```

Update configuration file with the following:

```
interface=eth0
bind-dynamic
domain-needed
bogus-priv
dhcp-range=192.168.1.100,192.168.1.200,255.255.255.0,12h
```


## Configuring Development Server

Development server us used to allow updates on the drone, which will not allow connections other than the UI
once it has been configured.

in /etc/dhcp/dhcpd.conf edit options at top of file to be: 
```
option domain-name "rrobot.org"
option domain-name-servers 192.168.1.1
subnet 192.168.0.0 netmask 255.255.255.0 {
   range 192.168.0.2 192.168.0.254;
   option routers 192.168.0.1;
}
```

### Ethernet Port

On set development Pi setup the following

- Create file "/etc/network/interfaces.d/eth0"
- add the following text

```
allow-hotplug eth0
iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0
gateway 192.168.1.1
```

assuming that 192.168.1.1 is the WiFi router address.

### DHCP Server
```
sudo service isc-dhcp-server stop
sudo apt install dnsmasq iptables iptables-persistent
```

Update configuration file with the following:

```
interface=eth0
bind-dynamic
domain-needed
bogus-priv
dhcp-range=192.168.1.100,192.168.1.200,255.255.255.0,12h
```

Allow routing from eth0 to wlan0 so that ipv4 messages will be forwarded

```
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -o wlan0 -j MASQUERADE
iptables -A FORWARD -i eth0 -o wlan0 -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -i wlan0 -o eth0 -j ACCEPT
netfilter-persistent save
```

verify connection

```
systemctl status dnsmasq
cat /var/lib/misc/dnsmasq.leases
```

should get something back that states the IP address of the drone for local connection.


