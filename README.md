# otusl1
 Otus lesson 1 homework 1

# Vlan routing
  

### Creating network topology in emulator

 (topology.png)

### Use addresing table

 ip's

### Use VLAN table
 
vlan's

#### 1. Configuring Virtual PC 1 

##### Change name to PC-A 

Rename VPC in emulator

##### Assgn ip address on interface eth0


```ip 192.168.3.3 255.255.255.0 192.168.3.1```

#### 1. Configuring Virtual PC 2

##### Change name to PC-B

Rename VPC in emulator

##### Assgn ip address on interface eth0


```ip 192.168.4.3 255.255.255.0 192.168.4.1```


#### 1. Configuring switch 1 and 2

##### Change name to S1(2 for switch2)

Rename switch in emulator


##### Change basic settings: 


```enable```  Enter in priveleged mode

```configure terminal```  Enter in config mode

```hostname S1``` Change name (S2 for switch2)

```no ip domain-lookup``` Disable resolving err inputs

```enable secret cisco```  set password to 'enable'

```line console 0``` ```password cisco``` set password to 'console'

```line vty 0 4``` ```password cisco``` set password to 'vty'

```enable password encryption``` password encrypt

```banner motd "Authorized access only!!!"``` Create login banner

```ntp server 95.174.96.44``` set ntp server

```exit``` ```exit``` ```copy running-config startup-config``` Save settings

##### Creating vlan's

```enable```  Enter in priveleged mode

```configure terminal```  Enter in config mode

```vlan 3``` ```name Management``` Create vlan id 3 with name 'Management'

```vlan 4``` ```name Operations``` Create vlan id 4 with name 'Operations'

```vlan 7``` ```name ParkingLot``` Create vlan id 7 with name 'ParkingLot'

```vlan 8``` ```name Native``` Create vlan id 8 with name 'Native'

##### Creating interface vlan for s1

```interface vlan 3``` ```ip address 192.168.3.11 255.255.255.0``` assign ip address on interface vlan 3
```no shutdown``` enable interface

##### Creating interface vlan for s2

```interface vlan 3``` ```ip address 192.168.3.12 255.255.255.0``` assign ip address on interface vlan 3
```no shutdown``` enable interface

##### Creating default gateway for s1 and s2

```ip route 0.0.0.0 0.0.0.0 192.168.3.1``` Create default route  


##### Assigning access vlan's on ports Switch S1

```interface ethernet 0/1``` ```switchport mode access``` ```switchport  access vlan 3 ``` 'ethernet 0/1 acces mode vlan id 3'

##### Assigning access vlan's on ports Switch S2

```interface ethernet 0/1``` ```switchport mode access``` ```switchport  access vlan 4 ``` 'ethernet 0/1 acces mode vlan id 4'

##### Assigning trunk vlan's on ports Switch S1

```interface range ethernet 0/0 , ethernet 0/2``` ```switchport trunk encapsulation dot1q``` ```switchport mode trunk ``` ```switchport trunk allowed vlan 3,4 ``` 'ethernet 0/0,2 trunk mode vlan 3 and 4'

##### Assigning trunk vlan's on ports Switch S2

```interface ethernet 0/0 ``` ```switchport trunk encapsulation dot1q``` ```switchport mode trunk ``` ```switchport trunk allowed vlan 3,4 ``` 'ethernet 0/0 trunk mode vlan 3 and 4'

##### Assigning not used ports to ParkingLot on s1 

```interface ethernet 0/1``` ```switchport mode access``` ```switchport  access vlan 7 ``` 'ethernet 0/1 acces mode vlan id 7'
```shutdown``` disable interface

##### Assigning not used ports to ParkingLot on s2 

```interface range ethernet 0/2 , ethernet 0/3``` ```switchport mode access``` ```switchport  access vlan 7 ``` 'ethernet 0/1 acces mode vlan id 7'
```shutdown``` disable interface

#### Configuring router r1

```enable```  Enter in priveleged mode

```configure terminal```  Enter in config mode

```hostname R1``` Change name 

```no ip domain-lookup``` Disable resolving err inputs

```banner motd "Authorized access only!!!"``` Create login banner

```ntp server 95.174.96.44``` set ntp server

```enable secret cisco```  set password to 'enable'

```line console 0``` ```password cisco``` set password to 'console'

```line vty 0 4``` ```password cisco``` set password to 'vty'

##### Create subinterfaces and assign ip addresses 
```interface ethernet 0/0.1 ``` ```encapsulation dot1Q 3 ``` ```ip address 192.168.3.1 255.255.255.0 ``` ip address on subinterface 0/0.1
 ```interface ethernet 0/0.2 ``` ```encapsulation dot1Q 3 ``` ```ip address 192.168.4.1 255.255.255.0 ``` ip address on subinterface 0/0.2


 Now pc's can ping each other icluding router r1