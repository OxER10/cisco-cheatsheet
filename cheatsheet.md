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

---

# Interfaces

Usual interface commands

`(config)# int {type} {number}` - enter interface config mode

`(config)# int range {type} {number}` - enter multiple interface config mode

`(config-if-range)# channel-group {identifier} mode active` - inditifies group as LACP EtherChannel config

`(config)# interface port-channel {identifier}` - enters LACP interface config mode

`(config-if)# ip address {ip-address} {subnet-mask}` - sets ip address to interface

`(config-if)# ipv6 address {ip-address/subnet-prefix}` - sets ipv6 address to interface

`(config-if)# ipv6 address {ip-address} link-local` - sets ipv6 adress link local

`(config-if)# description {description}` - sets interface description

`(config-if)# shut | no shut` - disables | enables interface

`(config)# int {type/number} {number.subnumber}` - enter subint configure mode

`(config-subif)# encaplusation dot1q {vlan_id} [native]` - configure the subinterface to respond to 802.1Q encapsulated traffic from specified valn id

`(config-subif)# ip address {ip-address} {subnet-mask}` - configure ip of the subnet

`(config)# interface loopback {number}` - creates internal interface with set ip

`(config-if)# ip address {ip-address} {subnet-mask}` - sets ip-address to loopback interface

---

## VLAN

Usual commands that are needed for vlan configuration

`(conf)# vlan {number, number-number}` - creates vlans if not found

`(conf-vlan)# name {name}` - assigns name to vlan {num}

`(conf)# int {interface to vlan}` - configure vlan interface

`(conf)# int range {number-number}` - configure multiple vlan interfaces

`(conf-if)# switchport mode {access | dynamic {auto | desireable} | trunk}` - all switchport modes

`(conf-if)# switchport mode access` - set port to access mode

`(conf-if)# switchport access vlan {vlan number}` - assigns port to a vlan. Can chain with `,`

`(conf-if)# mls qos trust {cos | device cisco-phone | dscp | ip-precesence}` - all qos commands

`(conf-if)# switchport voice vlan {number}` - enables port to use voip

`(conf-if)# switchport mode trunk` - set the port to permanent trunking mode

`(conf-if)# switchport trunk native vlan {number}` - sets native VLAN to something other than VLAN 1

`(conf-if)# switchport nonegotiate` - stops DTP negotiation

`(conf-if)# switchport trunk allowed vlan {number, number-number, etc}` - specify the list of VLANs to be allowed on the trunk link

`(conf-if)# no switchport` - converts layer 2 port to layer 3 port in 3 layer switch

`(conf)# int vlan {number}` - enter vlan config mode

`(conf-if)#no ip address` - removes ip from vlan

`(conf-if)# ip address {ip-number} {subnet-mask}` - assigns ip number to vlan

`(conf-if)# no shut` - enables interface

