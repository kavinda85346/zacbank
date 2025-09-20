#### ZACBank_L2_S3_AL Device Configuration Alterations ⚙️

**Changing Default VLAN**
```
ZACBank_L2_S3_AL(config-vlan)#vlan 200
ZACBank_L2_S3_AL(config-vlan)#name native
```

**Adding Native VLAN into Trunk Configuration**
```
ZACBank_L2_S3_AL(config-if)#interface range gigabitEthernet 0/1-2
ZACBank_L2_S3_AL(config-if-range)#switchport mode trunk
ZACBank_L2_S3_AL(config-if-range)#switchport trunk native vlan 200
ZACBank_L2_S3_AL(config-if-range)#no switchport trunk allowed vlan 50-176
ZACBank_L2_S3_AL(config-if-range)#switchport trunk allowed vlan 50-200
ZACBank_L2_S3_AL(config-if-range)#interface range fastEthernet 0/23-24
ZACBank_L2_S3_AL(config-if-range)#switchport mode trunk
ZACBank_L2_S3_AL(config-if-range)#switchport trunk native vlan 200
ZACBank_L2_S3_AL(config-if-range)#no switchport trunk allowed vlan 50-176
ZACBank_L2_S3_AL(config-if-range)#switchport trunk allowed vlan 50-200
ZACBank_L2_S3_AL(config-if-range)#interface range fastEthernet 0/2
ZACBank_L2_S3_AL(config-if-range)#switchport mode trunk
ZACBank_L2_S3_AL(config-if-range)#switchport trunk native vlan 200
ZACBank_L2_S3_AL(config-if-range)#no switchport trunk allowed vlan 50-176
ZACBank_L2_S3_AL(config-if-range)#switchport trunk allowed vlan 50-200
```

**Assigning unused switchports to crated native vlan**
```
ZACBank_L2_S3_AL(config-if-range)#interface range fastEthernet 0/3-20
ZACBank_L2_S3_AL(config-if-range)#switchport mode access
ZACBank_L2_S3_AL(config-if-range)#switchport access vlan 200
```

**Administratively shutting down unused swithports**
```
ZACBank_L2_S3_AL(config-if-range)#interface range fastEthernet 0/3-20
ZACBank_L2_S3_AL(config-if-range)#shutdown
```

**Restricting access to the device for unauthorized users**
```
ZACBank_L2_S3_AL(config)#enable secret cisco@123
ZACBank_L2_S3_AL(config)#line console 0
ZACBank_L2_S3_AL(config-line)#password cisco@123
ZACBank_L2_S3_AL(config-line)#logging synchronous
ZACBank_L2_S3_AL(config-line)#line vty 0 15
ZACBank_L2_S3_AL(config-line)#password cisco@123
ZACBank_L2_S3_AL(config-line)#transport input ssh
ZACBank_L2_S3_AL(config-line)#login local
ZACBank_L2_S3_AL(config-line)#exit
ZACBank_L2_S3_AL(config)#banner motd "Authorized Users Only!"
ZACBank_L2_S3_AL(config)#service password-encryption
```

**Enabling Switchport Security**
```
ZACBank_L2_S3_AL(config)#interface range fastEthernet 0/1-20
ZACBank_L2_S3_AL(config-if-range)#switchport port-security
ZACBank_L2_S3_AL(config-if-range)#switch port-security mac-address sticky
ZACBank_L2_S3_AL(config-if-range)#switch port-security aging time 1440
ZACBank_L2_S3_AL(config-if-range)#switchport port-security violation shutdown
```

**Configure SSH access to the device**
```
ZACBank_L2_S3_AL(config)#crypto key generate rsa general-keys modulus 1024
ZACBank_L2_S3_AL(config)#ip ssh version 2
ZACBank_L2_S3_AL(config)#username ZACBank_L2_S3_AL secret cisco@123
ZACBank_L2_S3_AL(config)#no ip domain-lookup
```
