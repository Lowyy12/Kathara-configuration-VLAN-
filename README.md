# Kathara-configuration-VLAN

I am going to use this repository for the notes necessary to understand 
the configuration of the VLANs, for Kathara laboratories.

## Physical Interfaces

| IFCONFIG | IP |
| --------- | --------- |
| ifconfig **interface** up | ip link set **interface** up |
| ifconfig **interface_virtual** up | ip link set **interface_virtual** up |

## Add IP addresses

| IFCONFIG | IP |
| --------- | --------- |
| ifconfig **interface** *IP_adress* | ip link add  *IP_adress* dev **interface** |
| ifconfig **interface_virtual** *IP_adress* | ip link add  *IP_adress* dev **interface_virtual** |

## Virtual Interfaces

Create virtual interfaces

| VCONFIG | IP |
| --------- | --------- |
| vconfig add **interface** **ID** | ip link add link **interface** name **interface**.**ID** type vlan id **ID** |

## Create bridge

| BRCTL |
| --------- |
| brctl addbr *name_bridge* |
| brctl addif *name_brdige* **interface**  |
| brctl addif *name_brdige* **interface_virtual**  |
| ifconfig *name_brdige* up |

## VLAN filtering method

Only with IP command

````bash
ip link set "interface" up
````

````bash
ìp link add "name_bridge" type bridge
ip link set "name_bridge" up
ip link set "name_bridge" type bridge vlan_filtering (1 on // 0 off)
````

*WITH ALL INTERFACE*
````bash
ip link set "interface" master "name_bridge"
````

Each terminal port is associated with the corresponding vlan and defined as untagged and pvid

````bash
bridge vlan add dev "interface" vid "ID" pvid untagged
````

Each trunk port is associated with each vlan to which it belongs

````bash
bridge vlan add dev "interface" vid "ID"
````
