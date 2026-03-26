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

---

## Housekeeping

Basic configs for each device

`(config)# hostname {name}` - set name of device

`(config)# service password-encryption` - encrypts all passwords

`(config)# enable secret {password}` - set encrypted password for priv exec mode

`(config)# banner motd #{banner}#` - creates message banner

`(config)# security passwords min-length {number}` - sets min password length

`(config)# login block-for {time} attempts {attempts} within {time}` - login failure wait time set

`(config-line)# password {password}` - sets password for console line

`(config-line)# login` - makes passwords active, use after EVERY password config

`(config-line)# exec-timeout {time}` - sets login timeout

`(config-if)# shutdown | no shutdown` - enables | disables interface

`(config-if)# description {description}` - sets description of interface

`(conf)# ip routing` - enables ipv4 routing on layer 3 switch

`(config) ipv6 unicast-routing` - enables ipv6 routing

`# cop run start` - copies running config to startup config (nvram)
