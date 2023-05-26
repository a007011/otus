 Otus lesson 2 homework 2

# Spanning tree (STP)
  

### Creating network topology in emulator

![Network topology](/homework_STP/Topology.png)

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
 
#####  Cheking switches accessibility

![ping](/homework_STP/pingfromS1.png)

![ping](/homework_STP/pingfromS2.png)

![ping](/homework_STP/pingfromS3.png)

#### Root bridge definition

```interface range ethernet 0/0-3 ``` Select interface range

```shutdown``` shutdown selected ports 
###### repeat this on all switches

```switchport trunk encapsulation dot1q``` select vlan type

```switchport mode trunk``` set type to trunk mode

```interface ethernet 0/1``` select ports

```no shutdown``` enable ports

```interface ethernet 0/3``` select ports

```no shutdown``` enable ports

```show spanning-tree``` show spanning tree state

![show sp](/homework_STP/spantrees1.png)


![show sp](/homework_STP/spantrees2.png)


![show sp](/homework_STP/spantrees3.png)

##### answers to questions

|  Device  |  BridgeID                  |  ports       | sts   
|----------|------------------          |--------------|-------
|S1        |32768 + 1 + aabb:cc00:0100  |              |  
|          |                            |e0/0          |fwd
|          |                            |e0/1          |fwd 
|          |                            |e0/2          |fwd
|          |                            |e0/3          |fwd
|S2        |32768 + 1 + aabb:cc00:0200  |              |  
|          |                            |e0/0          |fwd
|          |                            |e0/1          |blk 
|          |                            |e0/2          |fwd
|          |                            |e0/3          |fwd
|S3        |32768 + 1 + aabb:cc00:0200  |              |  
|          |                            |e0/0          |fwd
|          |                            |e0/1          |blk 
|          |                            |e0/2          |fwd
|          |                            |e0/3          |fwd






|          |                            |              | 
|          |                            |              |
|          |                            |              |
|          |                            |              |
|          |                            |              | 
|          |                            |              |
|          |                  |              |
|          |                  |              |
|          |                  |              | 
|          |                  |              |
|          |                  |              |



