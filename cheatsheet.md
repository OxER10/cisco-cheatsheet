# Cisco IOS

## General:

General commands that are used a lot

`> en` - enter privileged exec mode

`# conf t` - enter global config mode

`(config)# int {type} {number}` - enter interface config mode 

`(config)# vlan {number}` - enter VLAN config mode

`(config)# line con 0` - enter console line config mode

`(config)# line vty 0 15` - enter vty line config mode

`(config)# no ip domain look` - stops router domain lookup

`(config)# ip default-gateway {ip-address}` - sets default gateway to switch

`(config) ipv6 unicast-routing` - enables ipv6 routing

`(config)# undebug all` - stops all debugs

`# clock set {time} {date}` - sets manual time/date

`# terminal history size {number}` - increase or decrase the size of the buffer

`exit` - exits current mode/level

`end` - returns to exec mode

`# delete vlan.dat` - deletes the file containing all vlans

`# erase startup-config` - deletes contents from nvram
