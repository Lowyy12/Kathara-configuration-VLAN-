# Kathara-configuración-VLAN

Voy a utilizar este repositorio para las notas necesarias para comprender
la configuración de las VLAN, para los laboratorios Kathara.

## Interfaces físicas

| IFCONFIG | IP |
| --------- | --------- |
| ifconfig **interface** up | ip link set **interface** up |
| ifconfig **interface_virtual** up | ip link set **interface_virtual** up |

## Añadir direccion IP

| IFCONFIG | IP |
| --------- | --------- |
| ifconfig **interface** *IP_adress* | ip link add  *IP_adress* dev **interface** |
| ifconfig **interface_virtual** *IP_adress* | ip link add  *IP_adress* dev **interface_virtual** |

## Interfaces virtuales

Crear interfaces virtuales

| VCONFIG | IP |
| --------- | --------- |
| vconfig add **interface** **ID** | ip link add link **interface** name **interface**.**ID** type vlan id **ID** |

## Crear puente

| BRCTL |
| --------- |
| brctl addbr *name_bridge* |
| brctl addif *name_brdige* **interface**  |
| brctl addif *name_brdige* **interface_virtual**  |
| ifconfig *name_brdige* up |

## Método VLAN filtering

Solo con el comando IP

````bash
ip link set "interface" up
````

````bash
ìp link add "name_bridge" type bridge
ip link set "name_bridge" up
ip link set "name_bridge" type bridge vlan_filtering (1 on // 0 off)
````

*CON TODAS LAS INTERFACES*
````bash
ip link set "interface" master "name_bridge"
````

Cada puerto de terminal está asociado con la VLAN correspondiente y se define como "sin etiquetar" y pvid.

````bash
bridge vlan add dev "interface" vid "ID" pvid untagged
````

Cada puerto troncal está asociado a cada vlan a la que pertenece

````bash
bridge vlan add dev "interface" vid "ID"
````

