---
title: Primeros pasos con un VPS
excerpt: Aprenda a gestionar un VPS en su área de cliente y descubra las primeras etapas de su uso, incluyendo las conexiones a distancia y las medidas de seguridad
updated: 2024-02-19
---

> [!primary]
> Esta traducción ha sido generada de forma automática por nuestro partner SYSTRAN. En algunos casos puede contener términos imprecisos, como en las etiquetas de los botones o los detalles técnicos. En caso de duda, le recomendamos que consulte la versión inglesa o francesa de la guía. Si quiere ayudarnos a mejorar esta traducción, por favor, utilice el botón «Contribuir» de esta página.
> 

## Objetivo

Un servidor privado virtual (VPS) es un servidor dedicado virtualizado. A diferencia de los planes de hosting de OVHcloud, que son gestionados por OVHcloud, la configuración y el mantenimiento de un sistema VPS es responsabilidad suya como administrador de sistemas.

**Descubra la información necesaria para empezar a utilizar un VPS.**


## Requisitos

- Tener un [VPS](https://www.ovhcloud.com/es-es/vps/) en el área de cliente de OVHcloud
- Tienes acceso a tu [área de cliente de OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.es/&ovhSubsidiary=es).

## Procedimiento

Conéctese al [área de cliente de OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.es/&ovhSubsidiary=es), acceda a la sección `Bare Metal Cloud`{.action} y seleccione su servidor en la sección `Servidores privados virtuales`{.action}.

### Panel de control

La pestaña `Inicio`{.action} contiene información importante sobre su servicio y le permite realizar operaciones esenciales.

![VPS Home](images/vpshome.png){.thumbnail}

#### Su VPS <a name="yourvps"></a>

Esta sección muestra información básica sobre este VPS y el estado del servicio.

##### **Nombre**

Si hace clic en `...`{.action} y selecciona `Cambiar nombre`{.action}, puede introducir un nombre distinto para este VPS. Esta funcionalidad es útil para facilitar la navegación por el área de cliente cuando se gestionan varios servicios VPS. El nombre del servicio interno permanece en formato *vps-XXXXX.vps.ovh.net*.

##### **Boot**

El modo de arranque mostrado aquí es el modo «normal», en el que el sistema carga el sistema operativo instalado (*LOCAL*), o el **modo de rescate** proporcionado por OVHcloud en caso de solución de problemas. Utilice el botón `...`{.action} para [reiniciar el VPS](#reboot-current-range) o inicie el VPS en modo de rescate.

Para más información, consulte nuestra guía sobre el [modo de rescate](/pages/bare_metal_cloud/virtual_private_servers/rescue).

##### **SO/Distribución**

Este es el sistema operativo instalado actualmente. Utilice el botón `...`{.action} para [reinstalar el mismo sistema operativo o seleccione otro de las opciones disponibles](#reinstallvps).

Tenga en cuenta que la reinstalación borrará todos los datos alojados actualmente en el VPS (excepto los discos adicionales).

> [!primary]
>
> Si ha contratado un VPS **Windows**, solo puede elegir un SO Windows para la reinstalación. Asimismo, si Windows no ha sido seleccionado durante el pedido, no podrá instalarse después de la entrega del VPS.
>

Una vez instalado el sistema, deberá implementar las actualizaciones de seguridad. Para más información, consulte [a continuación](#reinstallvps) y en nuestra guía [Proteger un VPS](/pages/bare_metal_cloud/virtual_private_servers/secure_your_vps).

##### **Zona** / **Localización**

Estas secciones proporcionan información sobre la localización de su VPS. Esto puede ser útil, por ejemplo, para identificar los impactos en el servicio que se indican en [status reports](https://bare-metal-servers.status-ovhcloud.com/).

#### Su configuración

##### **Modelo**

Este elemento indica la referencia comercial que identifica el modelo de VPS correspondiente a las [ofertas de VPS en nuestro sitio](https://www.ovhcloud.com/es-es/vps) web.

##### **vCores**, **Memoria** y **Almacenamiento**

Los recursos actuales de su VPS se muestran aquí y pueden actualizarse por separado haciendo clic en el botón correspondiente. Tenga en cuenta que las actualizaciones están limitadas por el modelo de VPS elegido y solo pueden estar disponibles pasando a una [gama superior](https://www.ovhcloud.com/es-es/vps).

#### IP

##### **IPv4**

La dirección IPv4 pública principal del VPS se configura automáticamente durante la instalación. Para más información sobre la gestión de las IP, consulte nuestra guía [Configuring IP aliasing](/pages/bare_metal_cloud/virtual_private_servers/configuring-ip-aliasing).

##### **IPv6** / **Gateway**

Aquí puede ver la dirección IPv6 pública y la dirección de la puerta de enlace asociada. que se asocian automáticamente al VPS durante la instalación. Para más información, consulte [esta guía](/pages/bare_metal_cloud/virtual_private_servers/configure-ipv6).

##### **DNS secundario**

Esta funcionalidad es útil para alojar servicios DNS. La guía [Configurar el DNS secundario de OVHcloud en un VPS](/pages/bare_metal_cloud/virtual_private_servers/adding-secondary-dns-on-vps) explica en detalle este aspecto.

#### Resumen de las opciones

Estas opciones hacen referencia a servicios VPS adicionales que pueden solicitarse desde el área de cliente.

- La opción `Snapshot` permite crear un snapshot manual como punto de restauración único.
- La opción de `Backup automatizado` permite conservar varios snapshots de su VPS (excepto en discos adicionales).
- La opción `Discos adicionales` permite asociar espacio de almacenamiento a su VPS, por ejemplo, para almacenar datos de backup.

Encontrará toda la información sobre las soluciones de backup disponibles para su servicio en la [página del producto](https://www.ovhcloud.com/es-es/vps/options/) y en las respectivas [guías](/products/bare-metal-cloud-virtual-private-servers-backups).

#### Suscripción

En estas secciones se ofrece la información más importante sobre la facturación del servicio. Para más información, consulte la [documentación correspondiente](/products/account-and-service-management-managing-billing-payments-and-services).

### Funciones VPS disponibles en la pestaña «Inicio»

> [!warning]
>
> OVHcloud pone a su disposición servicios cuya configuración y gestión son responsabilidad suya. Por lo tanto, es su responsabilidad asegurarse de que funcionen correctamente.
>
> El objetivo de esta guía es ayudarle a realizar las tareas más habituales. No obstante, le recomendamos que se ponga en contacto con un [proveedor de servicios especializado](https://partner.ovhcloud.com/es-es/directory/) o con [nuestra comunidad](https://community.ovh.com/en/) si tiene problemas o dudas sobre la administración, el uso o la implementación de servicios en un servidor.
>

### Reinstalación de su VPS <a name="reinstallvps"></a>

Las reinstalaciones pueden realizarse desde el área de cliente. Haga clic en `...`{.action} al lado de **OS / Distribución** y luego en `Reinstalar mi VPS`{.action}.

![VPSnewreinstallation](images/2023panel_01.png){.thumbnail}

En la nueva ventana, seleccione un sistema operativo de la lista desplegable. Las opciones ofrecidas son imágenes compatibles [con un VPS de OVHcloud](/pages/public_cloud/compute/image-life-cycle) y funcionan inmediatamente después de la instalación.

También puede seleccionar una **llave SSH** para instalarla en el sistema, si previamente ha guardado una en el [área de cliente de OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.es/&ovhSubsidiary=es). Para más información, consulte nuestra guía [Crear y utilizar llaves SSH](/pages/bare_metal_cloud/dedicated_servers/creating-ssh-keys-dedicated).

> [!primary]
>
> **Licencias**
>
> Algunos sistemas operativos o plataformas propietarias, como Plesk o cPanel, requieren licencias que generan costes adicionales. Las licencias pueden administrarse desde el área de cliente. Acceda a la sección `Bare Metal Cloud`{.action} y, en la columna izquierda, haga clic en `Licencias`{.action}.
>
> Para tener un sistema operativo **Windows** que funcione en un VPS, es necesario **seleccionar en el proceso de pedido**. Un VPS con otro SO instalado no puede reinstalarse con Windows como se describe anteriormente.
>

En el área de cliente de OVHcloud podrá consultar el progreso de la instalación. Tenga en cuenta que este proceso puede tardar hasta 30 minutos.

### Reinicio del VPS <a name="reboot-current-range"></a>

Es posible que sea necesario reiniciar para aplicar configuraciones actualizadas o solucionar un problema. En la medida de lo posible, realice un reinicio por software desde la interfaz gráfica del servidor (Windows, Plesk, etc.) o desde la línea de comandos:

```bash
sudo reboot
```

No obstante, puede realizar un reinicio de hardware en cualquier momento desde el [área de cliente de OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.es/&ovhSubsidiary=es). En la pestaña `Inicio`{.action} , haga clic en `...`{.action} junto a `Boot` en la sección **Su VPS**. Seleccione `Reiniciar mi VPS`{.action} y haga clic en `Aceptar`{.action} en la ventana que se abre.

![Reboot](images/reboot-vps01.png){.thumbnail}

### Conexión a su VPS (SO GNU/Linux)

Al instalar por primera vez o al reinstalar desde el Panel de control, se crea automáticamente un usuario con permisos elevados. El nombre del usuario dependerá del sistema operativo, por ejemplo, «ubuntu» o «rocky».

Recibirá por correo electrónico el nombre de usuario y la contraseña necesarios para conectarse a su VPS por SSH. SSH es un protocolo de comunicación seguro que se utiliza para establecer conexiones cifradas con un host remoto.

La mayoría de los sistemas operativos de escritorio actuales tendrán un cliente **Open SSH** instalado de forma nativa. Esto significa que sus claves de acceso le permiten establecer rápidamente una conexión con su VPS en la aplicación de línea de comandos adecuada (`Terminal`, `Command prompt`, `Powershell`, etc.). Introduzca el siguiente comando:

```bash
ssh username@IPv4_VPS
```

Por ejemplo:

```bash
ssh ubuntu@169.254.10.250
```

También puede utilizar cualquier aplicación de terceros compatible con **Open SSH**.

Una vez que se haya conectado, puede sustituir la contraseña predefinida del usuario actual por una frase de contraseña segura utilizando este comando:

```bash
passwd
```

En una distribución GNU/Linux, **una petición de contraseña no mostrará sus entradas de teclado**.

Escriba su contraseña actual y pulse `Enter`{.action}. Escriba la nueva frase de contraseña y vuelva a escribirla en el siguiente mensaje para confirmarla.

```console
Changing password for ubuntu.
Current password:
New password: 
Retype new password: 
passwd: password updated successfully
```

> [!warning]
> 
> **Activación de la cuenta de usuario root**
>
> No es necesario utilizar la cuenta de usuario root para iniciar la administración del servidor. Esta cuenta debe estar habilitada en el sistema operativo del servidor para poder usarla. Además, como medida de seguridad, las conexiones SSH con el usuario root están **desactivadas** por defecto.
> 
A menos que se indique lo contrario, todas las acciones de administración descritas en nuestra documentación pueden ser realizadas por la cuenta de usuario por defecto, es decir, escribiendo `sudo` seguido del pedido correspondiente. Para más información, consulte nuestra guía "[Configuración de las cuentas de usuario y del acceso root en un servidor](/pages/bare_metal_cloud/dedicated_servers/changing_root_password_linux_ds)".
>

**Le recomendamos que siga estos pasos**:

- Familiarícese con las conexiones SSH consultando nuestra guía [Introducción al SSH](/pages/bare_metal_cloud/dedicated_servers/ssh_introduction).
- Utilice las llaves SSH como método avanzado y más práctico para las conexiones a distancia en nuestra guía [Crear y utilizar llaves SSH](/pages/bare_metal_cloud/dedicated_servers/creating-ssh-keys-dedicated).
- Utilice nuestra guía [Proteger un VPS](/pages/bare_metal_cloud/virtual_private_servers/secure_your_vps) para proteger su sistema contra ataques automatizados por *brute force* y otras amenazas habituales.

> [!primary]
>
Tenga en cuenta que si ha seleccionado una **distribución con aplicación** (Plesk, cPanel, Docker), es posible que las medidas de seguridad genéricas no se apliquen a su sistema. Consulte nuestras guías [Primeros pasos con las aplicaciones preinstaladas](/pages/bare_metal_cloud/virtual_private_servers/apps_first_steps) y [Desplegar cPanel en un VPS](/pages/bare_metal_cloud/virtual_private_servers/cpanel), así como la documentación oficial del editor correspondiente.
>

### Conexión a su VPS Windows

Una vez instalado el VPS de Windows, recibirá un mensaje de correo electrónico con el nombre de usuario predeterminado de `Windows user`.

A continuación, complete la instalación de Windows estableciendo el idioma para mostrar, la distribución del teclado y la contraseña del administrador.

Para ello, utilice nuestra consola KVM: haga clic en `...`{.action} al lado del nombre de su VPS en la sección [Su VPS](#yourvps) y seleccione `KVM`{.action}. Para más información sobre esta herramienta, consulte nuestra [guía KVM](/pages/bare_metal_cloud/virtual_private_servers/secure_your_vps).

Para finalizar la instalación de su VPS Windows a través de KVM, siga los pasos descritos en nuestra guía [Configurar una nueva instalación de Windows Server](/pages/bare_metal_cloud/virtual_private_servers/windows_first_config).

En su dispositivo Windows local, puede utilizar la aplicación cliente `Remote Desktop Connection` para conectarse al VPS.

![windows remote](images/windows-connect-03.png){.thumbnail}

Introduzca la dirección IPv4 de su VPS, su identificador y su contraseña. Normalmente, aparece un mensaje de advertencia solicitándole que confirme la conexión debido a un certificado desconocido. Haga clic en `Sí`{.action} para iniciar sesión.

También puede utilizar cualquier aplicación de terceros compatible con RDP. Este requisito es necesario si Windows no está instalado en el dispositivo local.

> [!primary]
>
Si tiene problemas con este procedimiento, compruebe que las conexiones remotas (RDP) están permitidas en su dispositivo comprobando la configuración del sistema, las reglas de firewall y las posibles restricciones de red.
>

### Proteger el VPS

Como administrador de su VPS, es responsable de la seguridad de las aplicaciones y los datos alojados en él.

Para más información sobre la protección de su sistema, consulte nuestra guía [Proteger un VPS](/pages/bare_metal_cloud/virtual_private_servers/secure_your_vps).

> [!primary]
>
Tenga en cuenta que si ha seleccionado una **distribución con aplicación** (Plesk, cPanel, Docker), es posible que las medidas de seguridad genéricas no se apliquen a su sistema. Consulte nuestras guías [Primeros pasos con las aplicaciones preinstaladas](/pages/bare_metal_cloud/virtual_private_servers/apps_first_steps) y [Desplegar cPanel en un VPS](/pages/bare_metal_cloud/virtual_private_servers/cpanel), así como la documentación oficial del editor correspondiente.
>

### Asociar un dominio

Por lo general, la conexión de un VPS a internet requiere la asignación de un dominio y su configuración DNS. Si gestiona su dominio con OVHcloud, puede consultar nuestra guía [Editar una zona DNS de OVHcloud](/pages/web_cloud/domains/dns_zone_edit) para obtener instrucciones.

### Proteger un dominio con un certificado SSL

Una vez configurado el VPS, puede proteger su dominio y su sitio web. Para ello, es necesario disponer de un certificado SSL, que permita el acceso a internet de su VPS a través de *HTTPS* en lugar de *HTTP* no seguro.

Puede instalar el certificado SSL directamente en el VPS. Consulte la documentación oficial de su distribución VPS.

Para un proceso más automatizado, OVHcloud también ofrece la solución SSL Gateway. Para más información, consulte la [página del producto](https://www.ovh.es/ssl-gateway/) o la [guía](/products/web-cloud-ssl-gateway).

## Más información

[FAQ VPS](/pages/bare_metal_cloud/virtual_private_servers/vps-faq)

[Introducción al SSH](/pages/bare_metal_cloud/dedicated_servers/ssh_introduction)

[Proteger un VPS](/pages/bare_metal_cloud/virtual_private_servers/secure_your_vps)

[Configurar una nueva instalación de Windows Server](/pages/bare_metal_cloud/virtual_private_servers/windows_first_config)

Únase a nuestra comunidad de usuarios en <https://community.ovh.com/en/>.
