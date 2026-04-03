# Troubleshooting

Guide for troubleshooting common issues on Cisco devices.

---

## General troubleshooting end-to-end connectivity

The outcome of this process is operational end-to-end connectivity. If all steps have been performed without any resolution, the network administrator may either want to repeat the previous steps or escalate the issue to a higher level of support.

### Step 1: Verify the physical layer

Check physical connectivity at the point where network communication stops. This includes cables and hardware. The problem might be with a faulty cable or interface, or involve misconfigured or faulty hardware.

It is worthwhile to verify the operation of general components. The most commonly used Cisco IOS commands for this purpose are `show processes cpu`, `show memory`, and `show interfaces`.

When troubleshooting performance-related issues and hardware is suspected to be at fault, the `show interfaces` command can be used to verify the interfaces through which the traffic passes.

Lines to watch for include:

- Input queue drops
  - Input queue drops signify that at the some point, more traffic was delivered to router than it could process. This can be caused by a temporary traffic spike, but if it happens often, it can be a sign of a hardware issue.
- Output queue drops
  - Output queue drops indicate that packets were dropped due to congestion on the interface. This can be caused by a temporary traffic spike, but if it happens often, it can be a sign of a hardware issue.
- Input errors
  - Input errors indicate errors that are experienced during the reception of the frame, such as CRC errors. High number of CRC errors could indicate cabling problems, interface problems, or, in an Ethernet-based network, duplex mismatches.
- Output errors
  - Output errors indicate errors, such as collisions, during the transmission of the frame. Collisions (especially late collisions) often indicate duplex mismatches.

### Step 2: Check for duplex mismatch

Another common cause for interface errors is a mismatched duplex mode between two ends of an Ethernet link. In many Ethernet-based networks, point-to-point connections are now the norm, and the use of hubs and the associated half-duplex operation is becoming less common. This means that most Ethernet links today operate in full-duplex mode, and while collisions were normal for an Ethernet link, collisions today often indicate that duplex negotiation has failed, or the link is not operating in the correct duplex mode.

The IEEE 802.3ab Gigabit Ethernet standard mandates the use of autonegotiation for speed and duplex. In addition, although it is not strictly mandatory, practically all Fast Ethernet NICs also use autonegotiation by default. The use of autonegotiation for speed and duplex is the current recommended practice.

However, if duplex negotiation fails for some reason, it might be necessary to set the speed and duplex manually on both ends. Typically, this would mean setting the duplex mode to full-duplex on both ends of the connection. If this does not work, running half-duplex on both ends is preferred over a duplex mismatch.

### Step 3: Verify addressing on the local network

### Step 4: Verify default gateway

### step 5: Verify correct path

### Step 6: Verify transport layer

### Step 7: Verify ACLs

### Step 8: Verify DNS

---

## Issues and commands to troubleshoot them

Usual issues that can occur on Cisco devices and commands to troubleshoot them.

---

### Interface status is down

`# sh int {interface-id}` - check if interface is administratively down or if there is a physical issue with the interface

`# sh log` - check for any error messages related to the interface

`# sh int {interface-id} status` - check the status of the interface and if it is connected to a device

---

### Forgot password and can't access device

#### Router

`# reload` - reload the device or restart the device's power and interrupt the boot sequence with `ctrl+c` (or `alt+b`) to enter ROMMON mode. Then use the `confreg 0x2142` to ignore the startup configuration and reset the password. Use `reset` to restart the device and access it without password.

To keep your original configuration, enter privileged EXEC mode and copy the startup configuration to running configuration with `# copy start run`. Then you can change the password.

Remember to change the configuration register back to `0x2102` with `# confreg 0x2102` and save the configuration to avoid booting into ROMMON mode on next restart.

#### Switch

---

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

### CDP

`# sh cdp` - displays information about directly connected Cisco devices

`# sh cdp neighbors (detail)` - displays summary information about directly connected Cisco devices

`# sh cdp interface {interface-id}` - displays information about directly connected Cisco devices on specific interface

`# sh cdp entry {device-name}` - displays detailed information about specific directly connected Cisco device

`# sh cdp traffic` - displays CDP traffic statistics

### LLDP

`# sh lldp` - displays information about directly connected devices using LLDP protocol

`# sh lldp neighbors (detail)` - displays summary information about directly connected devices using LLDP protocol

`# sh lldp interface {interface-id}` - displays information about directly connected devices using LLDP protocol on specific interface

`# sh lldp entry {device-name}` - displays detailed information about specific directly connected device using LLDP protocol

`# sh lldp traffic` - displays LLDP traffic statistics

### NTP

`# sh ntp status` - displays NTP synchronization status

`# sh ntp associations` - displays NTP associations configured on the device and their status

`# sh clock detail` - displays detailed information about the device's clock, including NTP synchronization status and time source
