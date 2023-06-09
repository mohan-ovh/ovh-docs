---
title: "¿Qué hacer en caso de página 403 forbidden?"
excerpt: Cómo volver a publicar un sitio web cuando este muestre la página 403 forbidden
updated: 2022-06-16
---

> [!primary]
> Esta traducción ha sido generada de forma automática por nuestro partner SYSTRAN. En algunos casos puede contener términos imprecisos, como en las etiquetas de los botones o los detalles técnicos. En caso de duda, le recomendamos que consulte la versión inglesa o francesa de la guía. Si quiere ayudarnos a mejorar esta traducción, por favor, utilice el botón «Contribuir» de esta página.
>

**Última actualización: 16/06/2022**

## Objetivo

Los cambios en los permisos de acceso a los archivos de su sitio web, el archivo **.htaccess** o la instalación de un plugin de seguridad pueden traducirse a veces en una página **"403 forbidden"**.

También puede ocurrir que, debido a una detección de anomalías, nuestros robots de seguridad hayan tenido que bloquear temporalmente el acceso a los archivos de su alojamiento. Este tipo de bloqueo automático tiene como objetivo impedir el envío de código malicioso a otras entidades y protegerle jurídicamente.

![403error](images/403error.png){.thumbnail}

**Esta guía explica cómo desbloquear el acceso a su sitio web en caso de que aparezca "403 forbidden".**

> [!warning]
>
> La configuración, la gestión y la responsabilidad de los servicios que OVHcloud pone a su disposición recaen sobre usted. Por lo tanto, usted deberá asegurarse de que estos funcionen correctamente.
>
> Esta guía le ayudará a realizar las operaciones más habituales. No obstante, si tiene alguna duda le recomendamos que contacte con un [proveedor especializado](https://partner.ovhcloud.com/es/directory/) o con el editor del servicio. Nosotros no podremos asistirle al respecto. Para más información, consulte el apartado [Más información](#gofurther) de esta guía.
>

## Requisitos

- Tener contratado un [plan de hosting](https://www.ovhcloud.com/es/web-hosting/) de OVHcloud.
- Disponer de las [claves de conexión](/pages/web/hosting/ftp_connection#1-obtener-los-datos-de-conexion) al espacio de almacenamiento del alojamiento.
- Haber iniciado sesión en el [área de cliente de OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/world/&ovhSubsidiary=ws).

## Procedimiento

### Etapa 1: analizar la situación

Si la página **"403 forbidden"** aparece debido a una modificación errónea de su sitio web, [restablezca la totalidad o parte del espacio de almacenamiento de su alojamiento](/pages/web/hosting/ftp_save_and_backup) a una fecha anterior.

Si las copias de seguridad disponibles no le permiten restablecer el acceso a su sitio web, contacte con un [proveedor especializado](https://partner.ovhcloud.com/es/directory/).

Si la página **"403 forbidden"** no ha aparecido debido a una modificación de su sitio web, consulte su mensajería. Si por motivos de seguridad nuestros servicios le han enviado un mensaje de correo electrónico indicándole que quiere cerrar el alojamiento, vaya al [paso 2](#step2).

Si la página **"403 forbidden"** ha aparecido sin ninguna acción por su parte y no ha recibido ningún correo de nuestros servicios al respecto, contacte con un [proveedor especializado](https://partner.ovhcloud.com/es/directory/).

### Etapa 2: proteger sus soluciones <a name="step2"></a>

En primer lugar, compruebe la seguridad de sus equipos informáticos:

- Realice las actualizaciones de seguridad.
- Compruebe también que haya instalado un antivirus, actualícela y lance una exploración completa. Si no tiene ninguno, consulte con un [proveedor especializado](https://partner.ovhcloud.com/es/directory/) antes de instalar el módulo.
- Cambie todas sus contraseñas locales, incluidas las de sus direcciones de correo, respetando las [buenas prácticas](/pages/account/customer/manage-ovh-password#generar-una-contrasena-adecuada).
- Cambie las contraseñas de todos sus servicios de OVHcloud, especialmente de su [base de datos](../cambiar-contrasena-base-de-datos/) y del acceso a su [espacio de almacenamiento FTP](/pages/web/hosting/ftp_change_password).

> [!warning]
>
> Antes de cambiar la contraseña de la base de datos del sitio web desde el [área de cliente de OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/world/&ovhSubsidiary=ws), actualice el archivo de configuración del sitio web para que se conecte a la base de datos con la nueva contraseña.
>
> En caso contrario, si cambia la contraseña de la base de datos, el sitio web o los servicios que lo utilizan se cortarán.
>
> Si tiene alguna duda sobre las operaciones que debe realizar, contacte con los [partners de OVHcloud](https://partner.ovhcloud.com/es/directory/).
>

### Etapa 3: intervenir en su alojamiento

En primer lugar, la fecha de envío del mensaje de correo electrónico de OVHcloud indica la desactivación de su alojamiento, así como el directorio o carpetas que contienen ejemplos de archivos ilegítimos.

#### Caso n° 1: el alojamiento se desactivó hace menos de dos semanas.

Si su alojamiento ha sido cerrado hace menos de dos semanas y solo contiene un sitio, restablezca su espacio de almacenamiento siguiendo las instrucciones de esta [guía](/pages/web/hosting/ftp_save_and_backup#restaurar-el-espacio-de-almacenamiento-desde-el-area-de-cliente).

Si su alojamiento ha sido cerrado hace menos de dos semanas y contiene varios sitios web, restablezca únicamente el directorio o carpetas que contengan los archivos ilegítimos siguiendo las instrucciones de esta [guía](/pages/web/hosting/ftp_save_and_backup#restaurar-un-archivo-desde-un-programa-o-una-interfaz-web).

> [!warning]
>
> Solo la restauración de su espacio de almacenamiento no bastará para corregir posibles fallos de seguridad presentes previamente en su sitio web.
> Para identificar estos fallos de seguridad, puede analizar los ["logs web"](/pages/web/hosting/logs_and_statistics#logs) de su alojamiento o recurrir a un [proveedor especializado](https://partner.ovhcloud.com/es/directory/) para realizar una auditoría de seguridad de sus soluciones.
>

#### Caso n° 2: su alojamiento ha sido desactivado más de dos semanas antes.

Si su alojamiento ha sido cerrado más de dos semanas antes, póngase en contacto con un [proveedor especializado](https://partner.ovhcloud.com/es/directory/) para realizar una auditoría de seguridad de sus soluciones. 

### Etapa 4: reactivar su alojamiento web <a name="reactivate-web-hosting"></a>

> [!warning]
>
> Le recomendamos que realice una auditoría de seguridad **antes** de reabrir el alojamiento. Cualquier envío de código malicioso desde su alojamiento puede conllevar su responsabilidad jurídica.
>

#### Reactivar el alojamiento con FileZilla

> [!primary]
>
> Si desea instalar **FileZilla** para manipular los archivos de su sitio web, siga las indicaciones de esta [guía](/pages/web/hosting/ftp_filezilla_user_guide).
>

Abra FileZilla y conéctese al espacio de almacenamiento. En el menú superior, haga clic en `Servidor`{.action} y seleccione `Introducir comando personalizado`{.action} (el nombre puede variar ligeramente según la versión de FileZilla que utilice).

![command_filezilla1](images/command_filezilla1.png){.thumbnail}

En la nueva ventana, introduzca el siguiente comando y acepte:

```
SITE CHMOD 705 /
```

![command_filezilla2](images/command_filezilla2.png){.thumbnail}

Una respuesta **"200 Permissions changed on /"** confirma que la operación se ha realizado correctamente. Para comprobarlo, vuelva a intentar acceder al sitio web.

#### Reactivar el alojamiento con el explorador FTP "net2ftp"

En el [área de cliente de OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/world/&ovhSubsidiary=ws), acceda a la sección `Web Cloud`{.action} y, seguidamente, haga clic en `Alojamientos`{.action} en la pestaña `FTP-SSH`{.action} del alojamiento correspondiente.

Haga clic en el botón `Explorador FTP `{.action} y conéctese al espacio de almacenamiento siguiendo las instrucciones de esta [guía](/pages/web/hosting/ftp_connection#21-conexion-mediante-un-explorador-ftp). Haga clic en el botón `Avanzado`{.action} y, a continuación, en el botón `Go`{.action} situado junto a "Send arbitrary FTP commands to the FTP server".

![net2ftp](images/net2ftp.png){.thumbnail}

Introduzca el siguiente comando en la parte superior de la página y haga clic en el botón con forma de "V" verde.

![result_command_on_net2ftp](images/result_command_on_net2ftp.png){.thumbnail}

Una respuesta **"200 Permissions changed on /"** confirma que la operación se ha realizado correctamente. Para comprobarlo, vuelva a intentar acceder al sitio web.

## Más información <a name="gofurther"></a>

[Pirateo de su sitio web WordPress: Consejos y casos prácticos](/pages/web/hosting/cms_what_to_do_if_your_site_is_hacked)

[Activación del firewall de aplicación](/pages/web/hosting/multisites_activating_application_firewall)

[Cambiar la versión de PHP de un alojamiento web](/pages/web/hosting/php_configure_php_on_your_web_hosting_2014)

Para servicios especializados (posicionamiento, desarrollo, etc.), contacte con los [partners de OVHcloud](https://partner.ovhcloud.com/es/directory/).

Si quiere disfrutar de ayuda para utilizar y configurar sus soluciones de OVHcloud, consulte nuestros distintos [servicios de soporte](https://www.ovhcloud.com/es/support-levels/).

Interactúe con nuestra comunidad de usuarios en <https://community.ovh.com/en/>.