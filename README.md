# Kathara-configuration-VLAN

I am going to use this repository for the notes necessary to understand 
the configuration of the VLANs, for Kathara laboratories.

## Physical Interfaces

| IFCONFIG | IP |
| --------- | --------- |
| ifconfig **interface** up | ip link set **interface** up |

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

##
