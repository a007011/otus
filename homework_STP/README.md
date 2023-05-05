 Otus lesson 2 homework 2

# Spanning tree (STP)
  

### Creating network topology in emulator

![Network topology](/homework_VLAN/Topology.png)

### Use addresing table

 ip's

 |  Device  |  Interface  |  IP Address  |  Subnet Mask  
|----------|------------------|--------------|---------------
|S1          |VLAN 1     |192.168.1.1   |255.255.255.0  
|S2          |VLAN 1     |192.168.1.2   |255.255.255.0  
|S3          |VLAN 1     |192.168.1.3   |255.255.255.0           


#### 1. Configuring switches

##### Change name to S1 S2 S3

Rename switches in emulator


##### Change basic settings: 


```enable```  Enter in priveleged mode

```configure terminal```  Enter in config mode

```hostname S1``` Change name (S2 for switch2) (S3 for switch3) 

```no ip domain-lookup``` Disable resolving err inputs

```enable secret cisco```  set password to 'enable'

```line console 0``` ```password cisco``` set password to 'console'

```line vty 0 4``` ```password cisco``` set password to 'vty'

```enable password encryption``` password encrypt

```banner motd "Authorized access only!!!"``` Create login banner

```ntp server 95.174.96.44``` set ntp server

```exit``` ```exit``` ```copy running-config startup-config``` Save settings
 
##### 