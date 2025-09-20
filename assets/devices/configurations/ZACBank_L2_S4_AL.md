#### ZACBank_L2_S4_AL Device Configurations ⚙️

**Startup Configuration**
```
Switch>enable
Switch#configure terminal
Switch(config)#hostname ZACBank_L2_S4_AL
ZACBank_L2_S4_AL(config)#ip domain-name zacbank.com
```

**Vlan Configuration**
```
ZACBank_L2_S4_AL(config)#vlan 50
ZACBank_L2_S4_AL(config-vlan)#name management
ZACBank_L2_S4_AL(config-vlan)#vlan 100
ZACBank_L2_S4_AL(config-vlan)#name core
ZACBank_L2_S4_AL(config-vlan)#vlan 150
ZACBank_L2_S4_AL(config-vlan)#name voice
ZACBank_L2_S4_AL(config-vlan)#vlan 96
ZACBank_L2_S4_AL(config-vlan)#name security
ZACBank_L2_S4_AL(config-vlan)#vlan 128
ZACBank_L2_S4_AL(config-vlan)#name atm
ZACBank_L2_S4_AL(config-vlan)#vlan 160
ZACBank_L2_S4_AL(config-vlan)#name staff
ZACBank_L2_S4_AL(config-vlan)#vlan 176
ZACBank_L2_S4_AL(config-vlan)#name recovery
```

**Trunk Configuration**
```
ZACBank_L2_S4_AL(config-if)#interface range gigabitEthernet 0/1-2
ZACBank_L2_S4_AL(config-if-range)#switchport mode trunk
ZACBank_L2_S4_AL(config-if-range)#switchport trunk allowed vlan 50-176
ZACBank_L2_S4_AL(config-if-range)#switchport nonegotiate
ZACBank_L2_S4_AL(config-if)#interface range fastEthernet 0/23-24
ZACBank_L2_S4_AL(config-if-range)#switchport mode trunk
ZACBank_L2_S4_AL(config-if-range)#switchport trunk allowed vlan 50-176
ZACBank_L2_S4_AL(config-if-range)#switchport nonegotiate
ZACBank_L2_S4_AL(config-if-range)#channel-group 4 mode passive
```

**Assigning VLANS to Switchports**
```
ZACBank_L2_S4_AL(config-if)#interface fastEthernet 0/1
ZACBank_L2_S4_AL(config-if)#switchport mode access
ZACBank_L2_S4_AL(config-if)#switchport access vlan 176
```
