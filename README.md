# Installation
## Prerequisite
```bash
sudo apt-get install python python-pip python-dev libffi-dev libssl-dev
sudo apt-get install python-virtualenv python-setuptools
sudo apt-get install libjpeg-dev zlib1g-dev swig
sudo apt-get install mongodb
sudo apt-get install postgresql libpq-dev
sudo apt-get install tcpdump apparmor-utils
sudo aa-disable /usr/sbin/tcpdump
```

## Virtual Box (Host Setup)
Download and install the Ubuntu distribution from here
https://www.virtualbox.org/wiki/Linux_Downloads

```bash
sudo iptables -t nat -A POSTROUTING -o eth0 -s 192.168.56.0/24 -j MASQUERADE
sudo iptables -P FORWARD DROP
sudo iptables -A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
sudo iptables -A FORWARD -s 192.168.56.0/24 -j ACCEPT
sudo iptables -A FORWARD -j LOG
sudo iptables -A FORWARD -s 192.168.56.0/24 -d 192.168.56.0/24 -j ACCEPT

VBoxManage hostonlyif create
VBoxManage hostonlyif ipconfig vboxnet0 --ip 192.168.56.1 --netmask 255.255.255.0
```
Select the vistual box name as cuckoo1
NOTE: If you change this name then make a corresponding change in the ~/.cuckoo/conf/virtualbox.conf

## Virtual Box (Guest Setup)

Select the following network setting
Network
    Attached to: Host-only Adapter
    Name: vboxnet0

Setup a static IP address



