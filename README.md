#!/bin/bash 

# Sao luu card mang
mv /etc/network/interfaces /etc/network/interfaces.bka

# Khai bao IP 
cat << EOF > /etc/network/interfaces
### Khai bao cho interface

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
###
# EM1
auto em1
iface em1 inet manual

# BR1
auto br1
iface br1 inet static
address 172.16.69.4
netmask 255.255.255.0
gateway 172.16.69.1
dns-nameservers 8.8.8.8
bridge_ports em1
bridge_stp off   

# EM2
auto em2
iface em2 inet manual

# BR2
auto br2
iface br2 inet static
address 123.30.178.194
netmask 255.255.255.224
bridge_ports em2
bridge_stp off  
EOF

sleep 3
echo " KHOI DON"
init 6
