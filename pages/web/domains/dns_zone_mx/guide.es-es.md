---
title: 'Añadir un registro MX a la configuración del dominio'
excerpt: 'Cómo añadir un registro MX a la configuración de un dominio en OVHcloud'
updated: 2018-05-30
---

**Última actualización: 21/09/2022**

## Objetivo

El registro MX permite asociar un dominio a un servidor de correo para que los servidores que tengan que enviar mensajes hacia sus direcciones de correo sepan a dónde tienen que enviarlos. Es probable que su proveedor disponga de varios servidores de correo, en cuyo caso deberá crear varios registros MX.

**Esta guía explica cómo añadir un registro MX a la configuración de un dominio en OVHcloud.**

## Requisitos

- Tener acceso a la gestión del dominio desde el [área de cliente de OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.es/&ovhSubsidiary=es){.external}.
- Estar conectado al [área de cliente de OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.es/&ovhSubsidiary=es){.external}.
- El dominio debe utilizar la configuración de OVHcloud (es decir, los servidores DNS de OVHcloud).

> [!warning]
>
> - Si el dominio no utiliza los servidores DNS de OVHcloud, deberá editar los MX desde el panel que le ofrezca el proveedor que gestione su configuración.
>
> - Si el dominio está registrado en OVHcloud, puede comprobar si utiliza nuestra configuración desde el [área de cliente](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.es/&ovhSubsidiary=es){.external}. Para ello, haga clic en `Dominios`{.action} y seleccione el dominio. A continuación, abra la pestaña `Servidores DNS`{.action}.
>

## Procedimiento

### 1. Los registros MX

Los registros MX permiten asociar un dominio al servidor de un proveedor de correo, como OVHcloud. Cuando una persona envía un mensaje de correo electrónico, el servidor que realiza el envío sabe a qué servidor debe dirigirlo gracias al registro MX.

Dado que es posible configurar varios registros MX para un mismo dominio, es necesario establecer una prioridad para cada uno de ellos. De este modo, los servidores que envían los mensajes de correo electrónico saben a qué servidor deben dirigirlos en primer lugar. Sin embargo, solo es posible añadir registros MX pertenecientes a un mismo proveedor.

**Editar los registros MX de un dominio es una operación delicada**, ya que una configuración errónea podría deshabilitar la recepción de nuevos mensajes en sus direcciones de correo. Así pues, debe prestar especial atención al modificar los registros MX de un dominio.

### 2. Conocer la configuración MX de OVHcloud

A continuación se indica la configuración MX de OVHcloud que deberá utilizar para su MX Plan (solo o incluido en un [plan de hosting de OVHcloud](https://www.ovhcloud.com/es-es/web-hosting/){.external}), [Email Pro](https://www.ovhcloud.com/es-es/emails/email-pro/){.external} o [Exchange](https://www.ovhcloud.com/es-es/emails/){.external}. Le recordamos que nuestros servidores de correo disponen de antispam y antivirus.

|Dominio|TTL|Registro|Prioridad|Destino|
|---|---|---|---|---|
|Dejar el campo vacío|3600|MX|1|mx0.mail.ovh.net.|
|Dejar el campo vacío|3600|MX|5|mx1.mail.ovh.net.|
|Dejar el campo vacío|3600|MX|50|mx2.mail.ovh.net.|
|Dejar el campo vacío|3600|MX|100|mx3.mail.ovh.net.|
|Dejar el campo vacío|3600|MX|200|mx4.mail.ovh.net.|

Deberá utilizar los registros MX anteriores en la configuración DNS del dominio. A continuación explicamos cómo realizar esta operación.

### 3. Modificar los registros MX de OVHcloud

Para modificar un registro MX en la configuración de su dominio en OVHcloud, conéctese al [área de cliente de OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.es/&ovhSubsidiary=es){.external}. En la columna izquierda, haga clic en `Dominios`{.action} y seleccione el dominio correspondiente. A continuación, abra la pestaña `Zona DNS`{.action}.

La tabla mostrará la configuración del dominio en OVHcloud. Cada línea corresponde a un registro DNS. En primer lugar, compruebe si los registros MX ya existen en la configuración DNS del dominio en OVHcloud utilizando el campo de búsqueda.

![Registro MX en la zona DNS](images/mx-records-dns-zone.png){.thumbnail}

Si los registros MX ya existen y quiere sustituirlos, haga clic en el botón `...`{.action} a la derecha de cada línea de la tabla correspondiente y seleccione  `Eliminar el registro`{.action}. No obstante, asegúrese de que siempre haya algún registro MX. Para ello, le recomendamos que vaya creando los nuevos registros MX deseados a medida que elimine los anteriores.

Para comprobar más rápidamente si ya existen registros MX, seleccione, utilizando el filtro situado sobre la tabla DNS, el campo de tipo **MX** y acepte para mostrar únicamente los registros DNS MX de su zona DNS.

Para crear un nuevo registro MX, haga clic en el botón `Añadir un registro`{.action} a la derecha de la tabla y seleccione `MX`{.action}. Complete la información solicitada (en función de la solución de correo de que disponga):

- **Si tiene contratada una solución de correo de OVHcloud**, consulte la información del paso [2. Conocer la configuración MX de OVHcloud](/pages/web/domains/dns_zone_mx#2-conocer-la-configuracion-mx-de-ovh){.external}.

- **Si tiene contratada una solución de correo externa**, consulte la información que le haya proporcionado el proveedor de su servicio de correo.

Una vez que haya completado la información, siga los pasos que se indican y haga clic en `Aceptar`{.action}.

> [!primary]
>
> Los cambios tardan entre 4 y 24 horas en propagarse y ser efectivos.
>

## Más información

[Información general sobre los servidores DNS](/pages/web/domains/dns_server_general_information){.external}

[Editar una zona DNS de OVHcloud](/pages/web/domains/dns_zone_edit){.external}

Para servicios especializados (posicionamiento, desarrollo, etc.), contacte con [partners de OVHcloud](https://partner.ovhcloud.com/es-es/).

Si quiere disfrutar de ayuda para utilizar y configurar sus soluciones de OVHcloud, puede consultar nuestras distintas soluciones [pestañas de soporte](https://www.ovhcloud.com/es-es/support-levels/).

Interactúe con nuestra comunidad de usuarios en <https://community.ovh.com/en/>.