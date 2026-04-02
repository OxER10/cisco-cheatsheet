# Troubleshooting

Guide for troubleshooting common issues on Cisco devices.

## Issues and commands to troubleshoot them

### Interface status is down

`# sh int {interface-id}` - check if interface is administratively down or if there is a physical issue with the interface

`# sh log` - check for any error messages related to the interface

`# sh int {interface-id} status` - check the status of the interface and if it is connected to a device

## Usual show commands

Usual show commands to display information about the device and its configuration.

`# sh run` - displays running configs

`# sh int` - display information for all interfaces on device

`# sh vlan [b, brief | id {vlan-id} | name {vlan-name} | summary]`  - display information about vlans on the device

`# sh ip int (b, brief)` - display summary of all ipv4 interfaces and operational statuses

`# sh ipv6 int (b, brief)` - display summary of all ipv6 interfaces and operational statuses

`# sh run int {interface-id}` - display commands applied to specific interface

`# sh ip ro, route` - display contents of the ipv4 routing table

`# sh ipv6 ro, route` - display contents of the ipv6 routing table

`# sh history` - display command history

`# sh file systems` - lists available file systems

`# sh version` - displays switch version

`# sh ip ssh` - displays if switch supports SSH

`# sh interface port-channel {identifier}` - displays general status of port channel interface

`# sh etherchannel summary` - display one line of information per port channel

`# sh enterchannel port-channel` - display information about specific port channel

`# sh interfaces {interface} etherchannel` - display information about the role of the interface in EtherChannel

`# sh run | section dhcp` - shows dhcp section in running-config

`# sh ip | ipv6 dhcp pool` - displays names of DHCPv4/6 pools and number of active clients

`# sh ip | ipv6 dhcp binding` - display list of all IPv4/6 address to mac address bindings provided by the DHCPv4/6 service

`# sh ip dhcp server statistics` - Displays count information regarding the number of DHCPv4/6 messages that have been sent and received

`# sh ip protocols (| include Router ID)` - displays routing protocols configured on the device and their router IDs

`# sh ip ospf interface {interface}` - displays OSPF information for specific interface

`# sh ip route (| include {ip})` - display routing table entries for specific destination network

`# sh ip ospf neighbor` - displays OSPF neighbor information

`# sh ip ospf database [router {router-id} | network {network-id} | summary]` - displays contents of the OSPF link-state database