---
title: 'Cambiar los servidores DNS de un dominio en OVHcloud'
excerpt: 'Cómo cambiar los servidores DNS de un dominio registrado en OVHcloud'
updated: 2021-02-18
---

**Última actualización: 05/05/2020**

## Objetivo

La función de los servidores DNS es alojar la configuración DNS de los dominios. La configuración DNS, también llamada zona DNS, contiene una serie de datos técnicos: los registros. Estos registros permiten relacionar el dominio con el servidor o servidores en los que están alojados el sitio web y las cuentas de correo electrónico.

Dicho de otra forma, los registros DNS, que se almacenan en los servidores DNS, permiten que se pueda acceder a los dominios desde internet.

**Esta guía explica cómo cambiar los servidores DNS de un dominio en OVHcloud.**

## Requisitos

- Tener un dominio registrado en OVHcloud.
- Estar conectado al [área de cliente de OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/world/&ovhSubsidiary=ws){.external}.

> [!warning]
>
> Si el dominio no está registrado en OVHcloud, deberá editar los servidores DNS desde el panel que le ofrezca el proveedor que tenga su gestión.
>

## Procedimiento

**Le recomendamos que preste especial atención cuando edite los servidores DNS de un dominio**, ya que una modificación errónea podría deshabilitar el acceso al sitio web y la recepción de nuevos mensajes en las direcciones de correo electrónico. A continuación explicamos lo que ocurre cuando se editan los servidores DNS para que entienda las consecuencias que ello implica.

Al cambiar los servidores DNS de un dominio, también se modifica su configuración DNS. La nueva configuración, que sustituye a la antigua, se almacena en los nuevos servidores DNS. Técnicamente, el dominio pasa a utilizar una nueva zona DNS.

Tenga en cuenta los siguientes aspectos:

- El contenido de la antigua configuración DNS no se replica automáticamente en la nueva. Por lo tanto, deberá asegurarse de que la nueva configuración contiene toda la información necesaria para que los servicios asociados al dominio (como el sitio web o las direcciones de correo electrónico) funcionen correctamente.

- Si quiere modificar un único elemento de la configuración DNS actual (un registro DNS, por ejemplo), le recomendamos que edite la zona DNS como se indica en la guía [Editar una zona DNS de OVHcloud](/pages/web_cloud/domains/dns_zone_edit).

- Existen registros (las entidades encargadas de gestionar las extensiones de dominio) que aplican requisitos particulares relativos a los servidores DNS: número de servidores de nombres, valor de los registros... En caso de duda, consulte con el registro responsable de la extensión.

> [!warning]
>
> Antes de realizar cualquier cambio, asegúrese de que la modificación no hará que su dominio deje de estar accesible. Si no está seguro, contacte con la persona que haya solicitado la modificación.
>

### 1. Acceder a la zona de gestión de los servidores DNS del dominio

En primer lugar, conéctese al [área de cliente de OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/world/&ovhSubsidiary=ws){.external} en la sección `Web Cloud`{.action}. Haga clic en `Dominios`{.action} y seleccione el dominio correspondiente. A continuación, abra la pestaña `Servidores DNS`{.action}.

Se mostrará una tabla con los servidores DNS actualmente configurados en OVHcloud para el dominio. Cada línea de la tabla contiene un servidor DNS (puede haber varios).

> [!primary]
>
> Cuando se utilizan los servidores DNS de OVHcloud, los números de servidores no guardan relación con el servicio o servicios que utiliza. Sólo la opción [DNS anycast](https://www.ovhcloud.com/es/domains/options/dns-anycast/) utiliza servidores DNS específicos que se le atribuyen automáticamente.

![Servidor DNS](images/edit-dns-server-ovh-step1.png){.thumbnail}

### 2. Editar los servidores DNS de un dominio

Para editar los servidores DNS, haga clic en el botón `Cambiar los servidores DNS`{.action}.

Sustituya en los campos de texto los detalles actuales del servidor DNS por la información relativa a los nuevos servidores que desee configurar. Para añadir más servidores a la lista, haga clic en el botón `+`{.action} situado al final de la última línea de la tabla. Aparecerá una nueva línea, donde deberá completar los campos de texto.

Una vez que haya introducido los datos, haga clic en el botón `Aplicar la configuración`{.action}. El estado de los servidores DNS se actualizará en la tabla, mostrando los cambios que acaba de realizar.

> [!primary]
>
> El botón `Restaurar los servidores DNS`{.action} permite sustituir los servidores DNS actuales del dominio por los servidores de OVHcloud de origen. Le recomendamos que solo utilice esta opción si quiere volver a utilizar los servidores DNS de OVHcloud. 
>

![Servidor DNS](images/edit-dns-server-ovh-step2.png){.thumbnail}

### 3. Esperar a que se propaguen los cambios

Una vez que haya realizado los cambios, deberá esperar a que se apliquen. Ocurrirán dos cosas:

- En primer lugar, el registro encargado de gestionar la extensión del dominio debe aplicar los cambios realizados desde OVHcloud. Puede consultar el progreso de esta operación en el [área de cliente de OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/world/&ovhSubsidiary=ws){.external}. Para ello, haga clic en `Dominios`{.action} y seleccione `Operaciones en curso`{.action}.
- Una vez que el registro encargado de gestionar la extensión del dominio haya aplicado los cambios, estos tardan un máximo de 48 horas en propagarse y ser efectivos.

## Más información

[Editar una zona DNS de OVHcloud](/pages/web_cloud/domains/dns_zone_edit)

Para servicios especializados (posicionamiento, desarrollo, etc.), contacte con [partners de OVHcloud](https://partner.ovhcloud.com/es/directory/).

Si quiere disfrutar de ayuda para utilizar y configurar sus soluciones de OVHcloud, puede consultar nuestras distintas soluciones [pestañas de soporte](https://www.ovhcloud.com/es/support-levels/).

Interactúe con nuestra comunidad de usuarios en <https://community.ovh.com/en/>.
