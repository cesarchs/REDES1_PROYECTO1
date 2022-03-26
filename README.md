# REDES1_PROYECTO1

# Grupo #8 | Proyecto 1

### Universidad de San Carlos de Guatemala, 25 Marzo 2022
### Facultad de Ingeniería
### Escuela de Ciencias y Sistemas
### Redes de Computadoras 1

<img src='https://user-images.githubusercontent.com/36779113/128587817-1a6c2fdc-d106-4dd3-b092-104c8299bded.png' background='white'>

> Integrantes
> - Cesar Leonel Chamale Sican		  201700634
> - Leonardo Roney Martínez Maldonado	  201780044
> - Julio Enrique Wu Chiu 		  201906180
> - Marcos Enrique Curtidor Sagui 	  201900874

---
# MANUAL DE CONFIGURACIÓN
## CONTENIDO
* [Descripción de Problema](#descripción-de-problema)
  * [Red Física](#red-física)
  * [Red Virtualizada](#red-virtualizada)
* [Requerimientos del Sistema](#requerimientos-del-sistema)
    * [Instalacion Imagen de Switch](#instalacion-imagen-de-switch) 
* [TOPOLOGIAS](#topologias)
  * [Tabla 1](#tabla-1) 
  * [TOPOLOGIA 1: Área de Trabajo](#topologia-1-área-de-trabajo)
    * [Configuracion topologia 1](#configuracion-topologia-1)
  * [TOPOLOGIA 2: Backbone](#topologia-2-backbone)
    * [Configuracion topologia 2](#configuracion-topologia-2)
  * [TOPOLOGIA 3: Zona de Servidores](#topologia-3-zona-de-servidores)
    * [Configuracion topologia 3](#configuracion-topologia-3)
<!-- toc! -->


## Descripción de Problema
Se debe configurar y administrar el cableado estructurado para una empresa de venta, se
les proporciona el diseño de la topología de red que será utilizado como infraestructura de
red para dicha compañía, pero deberán de configurarla para proveer comunicación de
acuerdo a las necesidades que se indican.
La compañía cuenta con 4 departamentos: recursos humanos, informática, contabilidad y
ventas. Se debe proveer comunicación entre los usuarios del mismo departamento y con su
servidor web si tuvieran uno, por ejemplo, los usuarios del departamento de ventas no se
podrán comunicar con ningún otro departamento solamente con host de su mismo
departamento.

## Red Física
Se tendrá de manera física 4 computadoras conectadas a la VPN formando una pequeña
red donde estas tienen conexión y acceso a propiedades de red tradicionales como archivos
compartidos por defecto.

## Red Virtualizada
Se deberá configurar y administrar los equipos de una infraestructura de red para una
empresa la cual cuenta con un servidor web en cada departamento.

---
## Requerimientos del Sistema
Para usar hacer uso de este proyecto primero deberá cumplir con los siguientes requerimientos:

#### Simulador de red: 
`Se debe tener instalado el simulador de redes GNS3 en una versión actualizada y estable EN ESTE CASO USAMOS LA VERSION: 2.2.29`
#### Imágenes de dispositivos virtuales: 
` Se deben hacer las configuraciones pertinentes para correr la simulación con todos los dispositivos necesarios, por ello primero se debe agregar la imagen virtual de una dispositivo Switch de capa 3.`

#### Sistema operativo: 
`Sistema operativo Windows 10.`
### Instalacion Imagen de Switch:
*Primero deberá obtener un archivo de imagen para GNS3 de un Switch de capa 3 previamente descargada en alguna carpeta de preferencia pues será de utilidad posteriormente.*

  -*En la pantalla principal debe ir a la cinta de opciones del menú en la parte superior y seleccionar la opción* `Edit -> Preferences`

  -*Luego debe seleccionar buscar la opción dispositivos de `Dynamips->IOS Routers`, en la ventana emergente deberá seleccionar la opción* `New`*. Las configuraciones posteriores para el dispositivo debe ser tal y como se muestra en las capturas siguientes.*
  
  -*Para finalizar se deben presionar los botones* `Apply` *y* `OK` *para que se guarden los cambios, luego en el área de dispositivos será visible el nuevo Switch.*

---
## TOPOLOGIAS
Se debe configurar la siguiente topología, tomando en cuenta estos parámetros iniciales y
los que se detallan a continuación en cada sección de la topología.
> <img src='https://github.com/cesarchs/REDES1_PROYECTO1/blob/main/IMG/topoCompleta.JPG'>

Tabla de distribución de direcciones ip correspondientes a cada
departamento de la empresa. La X representa el número de grupo elegido.

### TABLA 1

| Nombre        | No.VLAN | Direccion de Red | Primera Direccion Asignable | Ultimo Direccion Asignable |Gateway |
|---------------|---------|------------------|-----------------------------|----------------------------|------------------------|
| RRHH          | 10      | 192.168.X1.0/24  | 192.168.X1                  | 192.168.X1.254             | 192.168.X1.1         |
| Informatica   | 20      | 192.168.X2.0/24  | 192.168.X2                  | 192.168.X2.254             | 192.168.X2.1         |
| Constabilidad | 30      | 192.168.X3.0/24  | 192.168.X3                  | 192.168.X3.254             | 192.168.X3.1         |
| Ventas        | 40      | 192.168.X4.0/24  | 192.168.X4                  | 192.168.X4.254             | 192.168.X4.1         |

Nota: /24 es una notación de máscara subred, un término que se explicará en la siguiente
fase. Tome en cuenta que esto es equivalente a 255.255.255.0.

### TOPOLOGIA 1: Área de Trabajo
Esta zona, corresponde a la sección de cableado horizontal y área de trabajo, donde los
Los usuarios finales tendrán acceso a los puntos de red y conectar un dispositivo final. La
topografía y características correspondientes de la red es la siguiente:
> <img src='https://github.com/cesarchs/REDES1_PROYECTO1/blob/main/IMG/TOPOLOGIA%201/topologia_1.png' width='100%'>

### Configuracion topologia 1
Se debe configurar los puertos de los switch en modo access o modo troncal, según corresponda. 
* Configurar VTP con los siguientes datos:
  * Dominio: Grupo# (# - será el número de grupo asignado)
  * Contraseña: Grupo# (#-será el número de grupo asignado)
  * Modos de configuración:
    * Cliente:
      * ESW1
      * ESW2
      * ESW3

* Configurar la nube con el puerto 4001 de salida y 4002 de entrada.


A continuacion puede observarse las configuraciones necesarias en cada uno de los dispositivos y switchs para la toplogia 1:

---
## VPCs
### RRHH
<img src='https://github.com/cesarchs/REDES1_PROYECTO1/blob/main/IMG/TOPOLOGIA%201/rrhh1_topo1.PNG' width='100%' >

> <img src='https://github.com/cesarchs/REDES1_PROYECTO1/blob/main/IMG/TOPOLOGIA%201/rrhh2_topo1.PNG' width='100%' >

### informatica
<img src='https://github.com/cesarchs/REDES1_PROYECTO1/blob/main/IMG/TOPOLOGIA%201/informatica1_topo1.PNG' width='100%' >

### contabilidad
> <img src='https://github.com/cesarchs/REDES1_PROYECTO1/blob/main/IMG/TOPOLOGIA%201/conta1_topo1.PNG' width='100%' >

<img src='https://github.com/cesarchs/REDES1_PROYECTO1/blob/main/IMG/TOPOLOGIA%201/conta2_topo1.PNG' width='100%' >

### ventas
<img src='https://github.com/cesarchs/REDES1_PROYECTO1/blob/main/IMG/TOPOLOGIA%201/ventas1_topo1.PNG' width='100%' >

### switches
> <img src='https://github.com/cesarchs/REDES1_PROYECTO1/blob/main/IMG/TOPOLOGIA%201/esw1_topo1.PNG' width='100%' >

<img src='https://github.com/cesarchs/REDES1_PROYECTO1/blob/main/IMG/TOPOLOGIA%201/esw2_topo1.PNG' width='100%' >

> <img src='https://github.com/cesarchs/REDES1_PROYECTO1/blob/main/IMG/TOPOLOGIA%201/esw3_topo1.PNG' width='100%' >


### TOPOLOGIA 2: Backbone
La zona de cableado vertical será la encargada de conectar el área de trabajo con la zona
de servidores, para esto se tiene nodos altamente redundantes cuya finalidad es brindar
una conectividad el 100% del tiempo
> <img src='https://github.com/cesarchs/REDES1_PROYECTO1/blob/main/IMG/TOPOLOGIA%202/topologia.JPG' width='100%'>

#### Configuracion topologia 2

* Debe agregarse las máquinas, tomando en cuenta que todas son vpc.
* Configurar los puertos de los switch en modo access o modo troncal (dot1Q), según corresponda.
* Crear las 4 VLAN únicamente en el ESW4 como lo muestra la [tabla 1.0]($tabla-1).
* Configurar VTP con los siguientes datos:
  * Dominio: Grupo# (# - será el número de grupo asignado).
  * Contraseña: Grupo# (#-será el número de grupo asignado).
  * Versión: Configurar la versión 2.
  * Modos de configuración:
    * Cliente:
      * ESW5
      * ESW6
      * ESW7
    * Server:
      * ESW4
* Configurar STP con los siguientes datos:
  * ESW4 será el root bridge para la vlan 1,10,20,30,40.
* Configurar la nube 1, con el puerto 4002 de salida y 4001 de entrada. Configurar la nube 2, con el puerto 4003 de salida y 4004 de entrada.

---
A continuacion puede observarse las configuraciones necesarias en cada uno de los dispositivos y switchs para la toplogia 2:

### VPC
> <img src='https://github.com/cesarchs/REDES1_PROYECTO1/blob/main/IMG/TOPOLOGIA%202/ip%20de%20informatica_2.JPG' width='100%'>

### Switches
> <img src='https://github.com/cesarchs/REDES1_PROYECTO1/blob/main/IMG/TOPOLOGIA%202/switch%20cliente%20VLAN%20y%20TRUNK.JPG' width='100%'>
> <img src='https://github.com/cesarchs/REDES1_PROYECTO1/blob/main/IMG/TOPOLOGIA%202/switch%20cliente%20VTP.JPG' width='100%'>
> <img src='https://github.com/cesarchs/REDES1_PROYECTO1/blob/main/IMG/TOPOLOGIA%202/switch%20server%20VTP.JPG' width='100%'>


### TOPOLOGIA 3: Zona de Servidores
Lugar donde se almacenan los servidores web de la empresa. Se requiere que los mismos
estén siempre activos, debido a esto la topología se vuelve extremadamente pesada. Por lo
que se usará un nodo maestro-esclavo para equilibrar la carga del mismo.
> <img src='images/toplogia3.png' width='85%'>

#### Maestro
Con una interfaz gráfica, es quien controla la topología y gestiona los recursos. Es la
huesped de las vpc.

#### Esclavo
Un equipo que servirá como host para sobrellevar la carga del maestro.

### Configuracion topologia 3

* En este apartado, los servidores web son simples VPC’S, no se debe configurar nada en ellos más que su dirección ip. Se comprobará el acceso a ellos por medio de un PING.
* Configurar los puertos de los switch en modo access o modo troncal, según corresponda.
* Configurar VTP con los siguientes datos:
  * Dominio: Grupo# (# - será el número de grupo asignado).
  * Contraseña: Grupo# (#-será el número de grupo asignado).
  * Versión: Configurar la versión 2.
  * Modos de configuración:
    * Cliente:
      * ESW8
      * ESW9
      * ESW10
      * ESW11
    * Server:
      * 1. (-)
    * Transparent:
      * 1. (-)


## Envío de paquetes
### Topología 1



### Topologia 2

![image](https://user-images.githubusercontent.com/36779113/134792759-3d628427-0b56-41ff-b92b-7e4db9af307f.png)

### Topología 3

