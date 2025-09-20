#### ZACBank_L2_S2_AL Device Configurations ⚙️

**Startup Configuration**
```
Switch>enable
Switch#configure terminal
Switch(config)#hostname ZACBank_L2_S2_AL
ZACBank_L2_S2_AL(config)#ip domain-name zacbank.com
```

**Vlan Configuration**
```
ZACBank_L2_S2_AL(config)#vlan 50
ZACBank_L2_S2_AL(config-vlan)#name management
ZACBank_L2_S2_AL(config-vlan)#vlan 100
ZACBank_L2_S2_AL(config-vlan)#name core
ZACBank_L2_S2_AL(config-vlan)#vlan 150
ZACBank_L2_S2_AL(config-vlan)#name voice
ZACBank_L2_S2_AL(config-vlan)#vlan 96
ZACBank_L2_S2_AL(config-vlan)#name security
ZACBank_L2_S2_AL(config-vlan)#vlan 128
ZACBank_L2_S2_AL(config-vlan)#name atm
ZACBank_L2_S2_AL(config-vlan)#vlan 160
ZACBank_L2_S2_AL(config-vlan)#name staff
ZACBank_L2_S2_AL(config-vlan)#vlan 176
ZACBank_L2_S2_AL(config-vlan)#name recovery
```

**Trunk Configuration**
```
ZACBank_L2_S2_AL(config-if)#interface range gigabitEthernet 0/1-2
ZACBank_L2_S2_AL(config-if-range)#switchport mode trunk
ZACBank_L2_S2_AL(config-if-range)#switchport trunk allowed vlan 50-176
ZACBank_L2_S2_AL(config-if-range)#switchport nonegotiate
ZACBank_L2_S1_AL(config-if-range)#interface range fastEthernet 0/23-24
ZACBank_L2_S1_AL(config-if-range)#switchport mode trunk
ZACBank_L2_S1_AL(config-if-range)#switchport trunk allowed vlan 50-176
ZACBank_L2_S1_AL(config-if-range)#switchport nonegotiate
ZACBank_L2_S1_AL(config-if-range)#channel-group 3 mode active
ZACBank_L2_S1_AL(config-if-range)#interface range fastEthernet 0/21-22
ZACBank_L2_S1_AL(config-if-range)#switchport mode trunk
ZACBank_L2_S1_AL(config-if-range)#switchport trunk allowed vlan 50-176
ZACBank_L2_S1_AL(config-if-range)#switchport nonegotiate
ZACBank_L2_S1_AL(config-if-range)#channel-group 2 mode passive
```

**Assigning VLANS to Switchports**
```
ZACBank_L2_S1_AL(config-if)#interface fastEthernet 0/1
ZACBank_L2_S1_AL(config-if)#switchport mode access
ZACBank_L2_S1_AL(config-if)#switchport access vlan 150
ZACBank_L2_S1_AL(config-if)#interface fastEthernet 0/2
ZACBank_L2_S1_AL(config-if)#switchport mode access
ZACBank_L2_S1_AL(config-if)#switchport access vlan 96
```

