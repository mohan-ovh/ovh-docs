---
title: 'Configurar IPv6 en una instancia de Public Cloud'
excerpt: 'Cómo configurar el protocolo IPv6 en una instancia de Public Cloud'
updated: 2022-11-15
---

> [!primary]
> Esta traducción ha sido generada de forma automática por nuestro partner SYSTRAN. En algunos casos puede contener términos imprecisos, como en las etiquetas de los botones o los detalles técnicos. En caso de duda, le recomendamos que consulte la versión inglesa o francesa de la guía. Si quiere ayudarnos a mejorar esta traducción, por favor, utilice el botón «Contribuir» de esta página.
>


## Objetivo
El protocolo de internet versión 6 (IPv6), la última versión del protocolo de internet (IP), está diseñado para resolver el agotamiento de las direcciones IPv4 utilizando direcciones compuestas por 128 bits en vez de los 32 bits de las direcciones IPv4.

Todas las instancias de Public Cloud se entregan con una dirección IPv4 y una dirección IPv6.

Por defecto solo está configurada la IPv4.

**Esta guía explica cómo configurar una dirección IPv6 en una instancia de Public Cloud.**

> [!primary]
> 
> Actualmente las opciones Floating IP y Gateway no permiten la IPv6. La IPv6 solo puede utilizarse con las instancias en [modo público](/pages/public_cloud/public_cloud_network_services/concepts-01-public-cloud-networking-concepts#publicmode).
>

## Requisitos

* Tener una instancia de Public Cloud.
* Tener acceso administrativo (root) por SSH o escritorio remoto (Windows) al servidor.
* Tener conocimientos básicos de redes.
* Estar conectado al [área de cliente de OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/world/&ovhSubsidiary=ws).

## Procedimiento

> [!warning]
>
> Tenga en cuenta que en las versiones recientes de los sistemas operativos Linux, la dirección IPv6 está configurada por defecto en las instancias de Public Cloud. Asegúrese de comprobar el archivo de configuración de su sistema operativo antes de realizar cualquier cambio.
>

### Léxico

Antes de empezar, la recomendamos que eche un vistazo a la siguiente tabla, en la que se recogen los valores que utilizaremos en esta guía junto con su descripción:

|Valor|Descripción|
|---|---|
|YOUR_IPV6|Dirección IPv6 asignada al servicio.|
|IPV6_PREFIX|Prefijo del bloque IPv6 (p. ej.: 2607:5300:60:62ac::/128 -> netmask = 128).|
|IPV6_GATEWAY|Puerta de enlace del bloque IPv6.|


### Obtener la información relativa a la red

Conéctese al área de cliente de OVHcloud en la sección `Public Cloud`{.action} y seleccione el proyecto correspondiente. En la columna izquierda, seleccione el menú `Instances`{.action} y haga clic en el botón `...`{.action} junto a la instancia correspondiente y haga clic en `Detalles de la instancia`{.action}.

![public-cloud ipv6](images/pci2022.png){.thumbnail}

Puede consultar la información en la columna `Redes`{.action}.

![public-cloud ipv6](images/pci2022.1.png){.thumbnail}

### Ejemplos de configuraciones persistentes

> [!primary]
> **Ejemplos**
>
>La siguiente información se incluye solo a modo de ejemplo.
>
>Como administrador del servicio, deberá adaptarlo a su distribución.
>

> [!warning]
>
> Antes de editar un archivo de configuración, cree siempre una copia de seguridad del original si surge algún problema.
>

<br>En primer lugar, conéctese a su instancia por SSH.

#### En Debian

Si su interfaz es «eth0», la configuración tendrá que ser parecida a la siguiente:

Archivo a modificar (con privilegios su): `/etc/network/interfaces`

```console
iface eth0 inet static
address YOUR_IPV6
netmask IPV6_PREFIX
post-up /sbin/ip -6 route add IPV6_GATEWAY dev eth0
post-up /sbin/ip -6 route add default via IPV6_GATEWAY dev eth0
pre-down /sbin/ip -6 route del default via IPV6_GATEWAY dev eth0
pre-down /sbin/ip -6 route del IPV6_GATEWAY dev eth0
```

Veamos a continuación un ejemplo concreto:

```console
iface eth0 inet static
address 2001:41d0:xxx:xxxx::999
netmask 128
post-up /sbin/ip -6 route add 2001:41d0:xxx:xxxx::111 dev eth0
post-up /sbin/ip -6 route add default via 2001:41d0:xxx:xxxx::111 dev eth0
pre-down /sbin/ip -6 route del default via 2001:41d0:xxx:xxxx::111 dev eth0
pre-down /sbin/ip -6 route del 2001:41d0:xxx:xxxx::111 dev eth0
```

#### En Ubuntu

Los archivos de configuración de red se encuentran en el directorio `/etc/netplan/`. En primer lugar, cree una copia del archivo de configuración IPv6:

```bash
cd /etc/netplan
cp 50-cloud-init.yaml 51-cloud-init-ipv6.yaml
```

De este modo, podrá separar la configuración IPv6 y, en caso de error, cancelar fácilmente los cambios.

Si su interfaz es «eth0», la configuración tendrá que ser parecida a la siguiente:

Archivo a modificar (con privilegios su): `/etc/netplan/51-cloud-init-ipv6.yaml`

```yaml
network:
    ethernets:
        eth0:
            dhcp6: false
            match:
                macaddress: fb:17:3r:39:56:75
            set-name: eth0
            addresses:
              - "YOUR_IPV6/IPv6_PREFIX"
            gateway6: "IPv6_GATEWAY"
            routes:
              - to: "IPv6_GATEWAY"
                scope: link
    version: 2
```

> [!warning]
>
> Es importante mantener la alineación de cada elemento del archivo, tal y como se muestra en el ejemplo anterior. No use la tecla de tabulación para crear el espacio. Sólo es necesaria la tecla espacio.
>

Para probar su configuración, utilice el siguiente comando:

```bash
netplan try
```

Si es correcta, puede aplicarla con el siguiente comando:

```bash
netplan apply
```

#### En RedHat/CentOS

Si su interfaz es «eth0», la configuración tendrá que ser parecida a la siguiente:

Archivo a modificar (con privilegios root): `/etc/sysconfig/network-scripts/ifcfg-eth0`

```console
IPV6INIT=yes
IPV6ADDR=YOUR_IPV6/IPV6_PREFIX
IPV6_DEFAULTGW=IPV6_GATEWAY
```

Veamos a continuación un ejemplo concreto:

```console
IPV6INIT=yes
IPV6ADDR=2001:41d0:xxx:xxxx::999
IPV6_DEFAULTGW=2001:41d0:xxx:xxxx::111
```

#### En Windows

Acceda a la sección `Conexiones de red`{.action} de su Windows.

![public-cloud ipv6](images/pcipv63.png){.thumbnail}

A continuación, acceda a las `Propiedades`{.action} de su tarjeta de red haciendo clic derecho.

![public-cloud ipv6](images/pcipv64.png){.thumbnail}

Haga clic en `IPv6`{.action} y seleccione `Propiedades`{.action}.

![public-cloud ipv6](images/pcipv65.png){.thumbnail}

Introduzca la información de su IPv6.

![public-cloud ipv6](images/pcipv66.png){.thumbnail}

## Diagnóstico

¿Ha configurado su IPv6 pero no funciona? 

Existe un procedimiento muy sencillo para determinar si el problema se encuentra en la configuración realizada o en la red de OVHcloud.

En primer lugar, [ponga su instancia en modo de rescate](/pages/public_cloud/compute/put_an_instance_in_rescue_mode).

Utilice los siguientes comandos para configurar su IP de forma no persistente:

```bash
ip addr add YOUR_IPV6/IPV6_PREFIX dev eth0
ip -6 route add IPV6_GATEWAY dev eth0
ip -6 route add default via IPV6_GATEWAY dev eth0
```

Vuelva a probar su red mediante un ping6, por ejemplo:

```bash
ping6 ipv6.google.com
```
Si la instancia responde, es posible que no haya seguido correctamente alguno de los pasos de la configuración inicial.

Si el problema persiste, puede ponerse en contacto con nuestro equipo de soporte.

## Más información

Si necesita formación o asistencia técnica para implantar nuestras soluciones, póngase en contacto con su representante de ventas o haga clic en [este enlace](https://www.ovhcloud.com/es/professional-services/) para obtener un presupuesto y solicitar un análisis personalizado de su proyecto a nuestros expertos del equipo de Servicios Profesionales.

Interactúe con nuestra comunidad de usuarios en <https://community.ovh.com/en/>.
