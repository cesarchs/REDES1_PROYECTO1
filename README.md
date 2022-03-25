# REDES1_PROYECTO1

# Grupo #8 | Proyecto 1

### Universidad de San Carlos de Guatemala, Agosto 2021
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
<!--
Generated with [markedpp](#markedpp). Get [nodejs](https://nodejs.org) first
1. $ npm i -g markedpp
2. $ markedpp --github -o README.md README.md
-->
<!-- !toc (minlevel=2 omit="CONTENIDO") -->
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

## Requerimientos del Sistema
Para usar hacer uso de este proyecto primero deberá cumplir con los siguientes requerimientos:
#### Sistema operativo: `Para el caso se usa el sistema operativo Windows 10.`
#### Simulador de red: `Se debe tener instalado el simulador de redes GNS3 en una versión actualizada y estable`
#### Imágenes de dispositivos virtuales: `Se deben hacer las configuraciones pertinentes para correr la simulación con todos los dispositivos necesarios, por ello primero se debe agregar la imagen virtual de una dispositivo Switch de capa 3.`
### Instalacion Imagen de Switch
*Primero deberá obtener un archivo de imagen para GNS3 de un Switch de capa 3 previamente descargada en alguna carpeta de preferencia pues será de utilidad posteriormente.*
  > <img src='images/conf0.jpg' width='60%'>
  *En la pantalla principal debe ir a la cinta de opciones del menú en la parte superior y seleccionar la opción* `Edit -> Preferences`
  > <img src='images/conf1.jpg' width='75%'>
  *Luego debe seleccionar buscar la opción dispositivos de `Dynamips->IOS Routers`, en la ventana emergente deberá seleccionar la opción* `New`*. Las configuraciones posteriores para el dispositivo debe ser tal y como se muestra en las capturas siguientes.*
  > <img src='images/conf2.jpg' width='75%'>
  
  <img src='images/conf3.jpg' width='75%'>
  
  > <img src='images/conf4.jpg' width='75%'>
  
  <img src='images/conf5.jpg' width='75%'>
  
  > <img src='images/conf6.jpg' width='75%'>
  
  <img src='images/conf7.jpg' width='75%'>
  
  *Para finalizar se deben presionar los botones* `Apply` *y* `OK` *para que se guarden los cambios, luego en el área de dispositivos será visible el nuevo Switch.*
  > <img src='images/conf8.jpg' width='75%'>
  > <img src='images/conf9.jpg' width='75%'>

## TOPOLOGIAS
Se debe configurar la siguiente topología, tomando en cuenta estos parámetros iniciales y
los que se detallan a continuación en cada sección de la topología.
> <img src='images/red_completa.png'>

Tabla de distribución de direcciones ip correspondientes a cada
departamento de la empresa. La X representa el número de grupo elegido.

### TABLA 1

| Nombre        | No.VLAN | Direccion de Red | Primera Direccion Asignable | Ultimo Direccion Asignable | Direccion de Broadcast |
|---------------|---------|------------------|-----------------------------|----------------------------|------------------------|
| RRHH          | 1X      | 192.168.X1.0/24  | 192.168.X1                  | 192.168.X1.254             | 192.168.X1.254         |
| Informatica   | 2x      | 192.168.X2.0/24  | 192.168.X2                  | 192.168.X2.254             | 192.168.X2.254         |
| Constabilidad | 3x      | 192.168.X3.0/24  | 192.168.X3                  | 192.168.X3.254             | 192.168.X3.255         |
| Ventas        | 4x      | 192.168.X4.0/24  | 192.168.X4                  | 192.168.X4.254             | 192.168.X4.255         |

Nota: /24 es una notación de máscara subred, un término que se explicará en la siguiente
fase. Tome en cuenta que esto es equivalente a 255.255.255.0.

### TOPOLOGIA 1: Área de Trabajo
Esta zona, corresponde a la sección de cableado horizontal y área de trabajo, donde los
Los usuarios finales tendrán acceso a los puntos de red y conectar un dispositivo final. La
topografía y características correspondientes de la red es la siguiente:
> <img src='images/topologia1.png' width='100%'>

### Configuracion topologia 1

Agregar las maquinas de la siguiente forma:

| NO. | Nombre        | Virtualizada |
|-----|---------------|--------------|
| 1   | RRHH_1        | SI           |
| 2   | RRHH_2        | NO           |
| 3   | Conta_1       | NO           |
| 4   | Conta_2       | SI           |
| 5   | Ventas_1      | NO           |
| 6   | Informatica_1 | NO           |

Se debe configurar los puertos de los switch en modo access o modo troncal, según corresponda. 
* Configurar VTP con los siguientes datos:
  * Dominio: Grupo# (# - será el número de grupo asignado)
  * Contraseña: Grupo# (#-será el número de grupo asignado)
  * Versión: Configurar la versión 2
  * Modos de configuración:
    * Cliente:
      * ESW1
      * ESW2
      * ESW3
    * Server:
      * 1. (-)
    * Transparent:
      * 1. (-)
* Configurar la nube con el puerto 4001 de salida y 4002 de entrada.
* 
A continuacion puede observarse las configuraciones necesarias en cada uno de los dispositivos switch para la toplogia 1:

---
> <img src='images/top1_01.jpeg' width='75%' >

<img src='images/top1_02.jpeg' width='75%' >

> <img src='images/top1_03.jpeg' width='75%' >

<img src='images/top1_04.jpeg' width='75%' >

> <img src='images/top1_05.jpeg' width='75%' >

<img src='images/top1_06.jpeg' width='75%' >

<img src='images/top1_07.jpeg' width='75%' >

> <img src='images/top1_08.jpeg' width='75%' >

<img src='images/top1_09.jpeg' width='75%' >

> <img src='images/top1_10.jpeg' width='75%' >

<img src='images/top1_11.jpeg' width='75%' >

> <img src='images/top1_12.jpeg' width='75%' >

<img src='images/top1_13.jpeg' width='75%' >

> <img src='images/top1_14.jpeg' width='75%' >

<img src='images/top1_15.jpeg' width='75%' >

> <img src='images/top1_16.jpeg' width='75%' >

### TOPOLOGIA 2: Backbone
La zona de cableado vertical será la encargada de conectar el área de trabajo con la zona
de servidores, para esto se tiene nodos altamente redundantes cuya finalidad es brindar
una conectividad el 100% del tiempo
> <img src='images/topologia2.png' width='85%'>

#### Configuracion topologia 2

* Debe agregarse las máquinas, tomando en cuenta que todas son vpc.
* Configurar los puertos de los switch en modo access o modo troncal, según corresponda.
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
  * ESW4 será el root bridge para la vlan 1,1X,2X,3X,4X.
* Configurar la nube 1, con el puerto 4002 de salida y 4001 de entrada. Configurar la nube 2, con el puerto 4003 de salida y 4004 de entrada.

---

> <img src='images/top2_1.jpeg' width='100%'>
> <img src='images/top2_2.jpeg' width='100%'>
> <img src='images/top2_3.jpeg' width='100%'>
> <img src='images/top2_4.jpeg' width='100%'>


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
*  Configurar la nube con el puerto 4004 de salida y 4003 de entrada

---
> <img src='images/top3_01.jpeg' width='100%' >

<img src='images/top3_02.jpeg' width='100%' >

> <img src='images/top3_03.jpeg' width='100%' >

<img src='images/top3_04.jpeg' width='100%' >

> <img src='images/top3_05.jpeg' width='100%' >

<img src='images/top3_06.jpeg' width='100%' >

> <img src='images/top3_07.jpeg' width='100%' >

<img src='images/top3_08.jpeg' width='100%' >

> <img src='images/top3_09.jpeg' width='100%' >

<img src='images/top3_10.jpeg' width='100%' >

> <img src='images/top3_11.jpeg' width='100%' >

<img src='images/top3_12.jpeg' width='100%' >

> <img src='images/top3_13.jpeg' width='100%' >

## Envío de paquetes
### Topología 1

![image](https://user-images.githubusercontent.com/36779113/134792781-3ab216a5-fd94-4fda-a4a9-1c84cb35246d.png)

![image](https://user-images.githubusercontent.com/36779113/134792791-850143b2-a21b-4646-8753-58a37bcb66e3.png)

![image](https://user-images.githubusercontent.com/36779113/134792804-8e031049-7c07-4162-a635-7b78a30b2cfb.png)

![image](https://user-images.githubusercontent.com/36779113/134792815-a6041bd7-3a1d-44c9-9844-c584aa5940f1.png)

![image](https://user-images.githubusercontent.com/36779113/134792824-2affb8dc-af26-433f-80d0-bb3b346124c8.png)

![image](https://user-images.githubusercontent.com/36779113/134792840-594f541a-ead4-4d84-8b2f-5937a4d07116.png)

### Topologia 2

![image](https://user-images.githubusercontent.com/36779113/134792759-3d628427-0b56-41ff-b92b-7e4db9af307f.png)

### Topología 3

![image](https://user-images.githubusercontent.com/36779113/134792868-1e25afd5-b820-4593-a00e-f6859c8ce51c.png)

![image](https://user-images.githubusercontent.com/36779113/134792879-9e7a4039-4c47-49ad-b3b2-fe70962a71ec.png)

![image](https://user-images.githubusercontent.com/36779113/134792890-be07bcc9-c6ee-4f72-a628-a3186911077c.png)

![image](https://user-images.githubusercontent.com/36779113/134792908-97c5ef41-3387-487e-8fd3-ae281b4b75ff.png)
