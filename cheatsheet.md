# Cisco IOS

## General

General commands and configurations for Cisco IOS devices

### Common

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

`(config)# ntp master {stratum}` - sets device as NTP master with stratum level

`(config)# ntp server {ip-address}` - sets NTP server to sync time with

`config)# ntp update-calendar` - updates calendar on device with current time

`# terminal history size {number}` - increase or decrase the size of the buffer

`exit` - exits current mode/level

`end` - returns to exec mode

`# delete vlan.dat` - deletes the file containing all vlans

`# erase startup-config` - deletes contents from nvram

---

### Saving and managing configs

`# copy running-config startup-config` - copies running config to startup config (nvram)

`# copy running-config flash:` - copies running config to flash memory

`# copy flash: {filename} running-config` - copies config from flash to running config

`# copy running-config tftp:` - copies running config to tftp server

`# copy tftp: running-config` - copies config from tftp server to running config

---

### Upgrading IOS

`# copy tftp: flash:` - copies IOS image from tftp server to flash memory

`# boot system {filename}` - sets device to boot from specific IOS image in flash memory

---

### Housekeeping

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

### Interfaces

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

### VLAN

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

---

### DHCP

Usual commands for DHCP configuration

`(config)# ipv6 unicast-routing` - enables IPv6 routing

`(config)# no service dhcp` - disables DHCP services

`(config)# service dhcp` - enables DHCP services

`(config)# ip dhcp excluded-address {low-address} [high-address]` - exclude ip pool

`(config)# ip | ipv6 dhcp pool {pool-name}` - creates pool and puts router in config mode

`(dhcp-config)# network {network-number} [mask | /prefix-length]` - define address pool

`(dhcp-config)# default-router {address} [address2, addressx]` - define default router or gateway

`(dhcp-config)# dns-server {address} [address2, addressx]` - define dns server

`(dhcp-config)# domain-name {domain}` - define domain name

`(dhcp-config)# lease {days [hours [minutes]] | infinite}` - define duration of the DHCP release

`(dhcp-config)# netbios-name-server {address} [address2, addressx]` - define NetBIOS WINS server

`(config)# interface {type and number}` - dhcp interface

`(config-if)# ip address dhcp` - configures interface as a DHCP client

`(config-if)# ip helper-address {server-address}` - relays received DHCP broadcasts to the DHCPv4 server

`(config-if)# ipv6 enable` - creates link-local address without GUA

`(config-if)# ipv6 address autoconfig` - enables automatic configuration of IPv6 addressing usin SLAAC

`(config-if)# ipv6 nd other-config-flag` - reset the interface to default SLAAC only option (O flag = 0), thus forcefully enabling stateless DHCPv6

`(config-if)# ipv6 nd managed-config-flag` - enables stateful DHCPv6 on interface. Sets M flag to 1

`(config-if)# ipv6 nd prefix default no-autoconfig` - disables SLAAC by setting A flag to 0

---

### OSPF

Usual configuration commands for OSPF routing protocol

`# clear ip ospf process` - clears OSPF table

`(config)# interface Loopback {num}` - configure loopback interface

`(config)# ip address {ip-address} {subnet-mask}` - uses loopback ip as router ID

`(config)# router ospf {process-id}` - enables OSPF on router

`(config-router)# router-id {rid}` - sets router ID manually

`(config-router)# network {network-address} {wildcard-mask} area {area-id, 10 in ptp}` - enables interfaces that match to send and receive OSPF packets

`(config-router)# default-information originate` - propagate default route in OSPF. Distributes it to all OSPF routers. Same as `route 0.0.0.0 0.0.0.0 next-hop`

`(config-router)# passive-interface {type} {number}` - prevents routing updates to interfaces where they are not needed

`(config-router)# auto-cost reference-bandwidth {mbits}` - change reference cost

`(config)# interface {type/number}` - configure ospf interface

`(config-if)# ip ospf {process-id} area {area-id, 10 in ptp}` - configure OSPF directly on interface

`(config-if)# ip ospf network point-to-point` - changes to point to point network

`(config-if)# ip ospf priority {num}` - configures interface priority

`(config-if)# ip ospf cost {num}` - configures cost value of interface

`(config-if)# ip ospf hello-interval {sec}` - configures hello timer value (default 10)

`(config-if)# ip ospf dead-interval {sec}` - configures dead timer value (default 40)

---

### NAT

Usual configuration commands for NAT on routers

`(config)# ip nat inside source static {inside local address} {inside global address}` - Configure inside static NAT

`(config)# ip nat pool {pool name} {start-add} {end-add} netmask {mask}` - configure NAT pool

`(config)# access-list {aclnum} permit {to be translated add} {wildmask}` - permit only to be translated addresses

`(config)# ip nat inside source list {acl num | acl name} pool {nat pool name}` - bind ACL to pool

`(config)# interface {type/number}` - select the interfaces participatin in translation

`(config-if)# ip address {add} {mask}` - set ip address to interface

`(config-if)# ip nat {inside | outside}` - add nat to inside/outside interface

`(config)# ip nat inside source list {acl num | acl name} interface {type/number} overload` - configure dynamic NAT overload (PAT) to use interface ip as inside global address

`Config)# ip nat inside source list {acl num | acl name} pool {nat pool name} overload` - configure dynamic NAT overload (PAT) using pool addresses as inside global addresses

---

### Device Discovery

Usual configuration commands for CDP and LLDP to discover directly connected devices

`(config)# cdp run` - enables CDP globally

`(config)# no cdp run` - disables CDP globally

`(config)# interface {type/number}` - configure interface for CDP

`(config-if)# cdp enable` - enables CDP on interface

`(config-if)# cdp disable` - disables CDP on interface

`(config)# lldp run` - enables LLDP globally

`(config)# no lldp run` - disables LLDP globally

`(config)# interface {type/number}` - configure interface for LLDP

`(config-if)# lldp transmit` - enables LLDP transmission on interface

`(config-if)# lldp receive` - enables LLDP reception on interface

`(config-if)# no lldp transmit` - disables LLDP transmission on interface

`(config-if)# no lldp receive` - disables LLDP reception on interface

---

### NTP

Usual configuration commands for NTP to synchronize time on devices

`(config)# ntp master {stratum}` - sets device as NTP master with stratum level

`(config)# ntp server {ip-address}` - sets NTP server to sync time with

---

## SECURITY

Security commands

### SSH

Usual SSH configuration commands for secure remote access to devices

`(config)# ip domain-name {name.com}` - sets domain name

`(config)# cry key gen rsa general-keys mod 1024` - configs complexity of keys

`(config)# username {name} secret {password}` - sets a username and encrypted password

`(config)# ip ssh version 2` - sets SSH version to 2

`(config)# line vty 0 15 (0 4)` - configs which VTY lines to use

`(config-line)# login local` - sets login

`(config-line)# transport input ssh` - defines transport protocol to SSH

---

### PORT SECURITY

`(config)# interface {type and number}` - configure interface for port security

`(config-if)# switchport access` - change dynamic port to manually controlled

`(config-if)# switchport port-security` - enable port-security on interface

`(config-if)# switchport port-security maximum {value}` - set maximum number of MAC addresses allowed on a port

`(config-if)# switchport port-security mac-address {mac-address}` - allows set MAC address

`(config-if)# switchport port-security mac-address sticky` - enables dynamically learning MAC addresses and sticking them on NVRAM

`(config-if)# switchport port-security aging time {time}` - specify aging time for port. Range 0-1440

`(config-if)# switchport port-security aging type {absolute | inactivity}` - sets age out to exactly or after inactivity

`(config-if)# switchport port-security violation {protect | restrict | shutdown}` - sets how switch reacts to port violations. Shutdown disables port and port must be restarted manually

---

### DHCP SNOOPING

Usual configuration commands for DHCP snooping to prevent rogue DHCP servers on the network

`(config)# ip dhcp snooping` - enables DHCP snooping globally

`(config)# ip dhcp snooping vlan {vlan number}` - enables DHCP snooping on vlan

`(config)# interface {type/number}` - configure interface for DHCP snooping

`(config-if)# ip dhcp snooping trust` - configures interface as trusted for DHCP messages. Untrusted interfaces will drop DHCP messages that are not from a trusted source

---

### ACL

Usual configuration commands for ACLs to control traffic on the network

`(config)# access-list {acl-number} {deny | permit} {source} [wildcard-mask]` - creates ACL with number

`(config)# access-list {acl-number} remark {text}` - add remark to ACL. Documentation purposes.

`(config)# interface {type number}` - configure interface to apply ACL

`(config-if)# ip access-group {acl-number | acl-name} {in | out}` - apply ACL to interface

`(config)# ip access-list {type} {name}` - enter access list config mode with name

`(config-std-nacl)# remark {text}` - for documentation purposes

`(config-std-nacl)# permit host {ip-address}` - permits host ip

`(config-std-nacl)# permit {ip-address} {wildcard-mask}`  - permits all hosts on wildcard

`(config-std-nacl)# deny any` - track number of times denied

`(config)# line vty 0 15 (0 4)` - configure VTY lines to apply ACL

`(config-line)# access-class {acl-number | acl-name} {in | out}` - apply ACL to VTY lines

---

### Extended ACL

usual configuration commands for extended ACLs to control traffic on the network with more options

`(config)# access-list {acl-number (100-199, 2000-2699)} {deny | permit} {protocol (ip | tcp | udp | icmp} {source} {wildcard-mask} [lt | gt | eq | neq {port}]` - creates extended ACL with number

`(config)# ip access-list extended {name}` - enter access list config mode with name
