# Kathara-configuration-VLAN

I am going to use this repository for the notes necessary to understand 
the configuration of the VLANs, for Kathara laboratories.

## Physical Interfaces

| IFCONFIG | IP |
| --------- | --------- |
| ifconfig **interface** up | ip link set **interface** up |

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
| ifconfig *name_brdige* up |
