---
title: 'Particularidades técnicas de los alojamientos compartidos'
excerpt: 'Esta guía ofrece toda la información relativa a las particularidades técnicas de los alojamientos compartidos'
updated: 2022-11-18
---

> [!primary]
> Esta traducción ha sido generada de forma automática por nuestro partner SYSTRAN. En algunos casos puede contener términos imprecisos, como en las etiquetas de los botones o los detalles técnicos. En caso de duda, le recomendamos que consulte la versión inglesa o francesa de la guía. Si quiere ayudarnos a mejorar esta traducción, por favor, utilice el botón «Contribuir» de esta página.
>

## Objetivo

**Esta guía le informa de los detalles técnicos de la infraestructura de los alojamientos Web OVHcloud, en función de las preguntas más frecuentes**

## Requisitos

- Tener contratado un [plan de hosting](https://www.ovhcloud.com/es/web-hosting/){.external} compatible.
- Haber iniciado sesión en el [área de cliente de OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/world/&ovhSubsidiary=ws){.external}.

## Procedimiento

> [!warning]
>
> La configuración, la gestión y la responsabilidad de los servicios que OVHcloud pone a su disposición recaen sobre usted. Por lo tanto, usted deberá asegurarse de que estos funcionen correctamente.
> 
> Esta guía le ayudará a realizar las operaciones más habituales. No obstante, si tiene alguna duda le recomendamos que contacte con un proveedor de servicios especializado o con el editor del servicio. Nosotros no podremos asistirle. Para más información, consulte el apartado «Más información» de esta guía.
> 

### FTP

- Error de acceso ("Fallo de autenticación de conexión 530"): Puede comprobar que los datos de acceso a su espacio FTP son correctos verificándolos en el [área de cliente de OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/world/&ovhSubsidiary=ws){.external} en la pestaña `FTP - SSH`. Las contraseñas nunca se muestran, pero pueden modificarse. Consulte nuestras [guías FTP](/pages/web_cloud/web_hosting/ftp_connection).

- Las conexiones FTP deben utilizar el **modo pasivo**. Asegúrese de que su script o su cliente FTP estén configurados correctamente.

## Emails <a name="emails"></a>

Para garantizar una buena calidad de servicio para todos y facilitar el envío de sus mensajes a sus destinatarios, aplicamos cuotas para nuestros servicios de alojamiento web.

En un período de 3600 segundos (es decir, 1 hora), su plan de hosting le permitirá enviar los siguientes límites de correo:

|Solución|Personal|Pro|Performance|
|---|---|---|---|
|Cantidad máxima de envío de correo por hora y servicio|100|200|2000|

- Aparte de las sospechas de spamming o phishing, el envío de los mensajes de correo podría aplazarse. Su correo se conservará en una cola de espera hasta que el número de mensajes enviados durante la hora anterior sea inferior al de tráfico.
- En caso de abuso o riesgo comprobado, el servicio se suspenderá y usted recibirá una notificación por correo electrónico de la suspensión del servicio. ¿Qué hacer en caso de cuenta bloqueada por spam? Consulte [nuestra guía](/pages/web_cloud/email_and_collaborative_solutions/troubleshooting/locked_for_spam).

### Bases de datos/SQL

### Conexiones simultáneas a la base de datos

- En los planes de hosting (bases de datos compartidas), existe un límite de 30 conexiones simultáneas por base de datos. Consulte los [detalles de nuestros planes de hosting](https://www.ovhcloud.com/es/web-hosting/) para comprobar las opciones disponibles en cada plan de alojamiento web.

#### Conexiones desde un servidor externo

- Por razones de seguridad, no es posible conectarse desde un servidor externo a la base de datos de un plan de hosting OVHcloud. Solo los servidores OVHcloud Web Hosting pueden conectarse a los servidores de base de datos. Cualquier otra conexión generará el siguiente error:

```bash
Warning: MySQL Connection Failed: Host ip.your.connection is not allowed to connect ...
```

#### Variables servidor SQL compartido

- Conéctese a la interfaz PhpMyAdmin, e introduzca el comando **show variables** para verificar las variables del servidor MySQL.

- La versión MySQL no puede modificarse para las bases de datos integradas en el alojamiento web.

Para saber más sobre la gestión de las bases de datos, consulte la guía [Crear una base de datos en un alojamiento web](/pages/web_cloud/web_hosting/sql_create_database).

### PHP

- Le recomendamos que consulte nuestros [planes de hosting](https://www.ovhcloud.com/es/web-hosting/) para asegurarse de que el alojamiento web que desea contratar sea compatible con sus necesidades.

> [!warning]
>
> La modificación del archivo **php.ini** no está disponible en los planes de hosting. Esto se debe a que la configuración PHP es global al conjunto de la infraestructura compartida.
>

- Puede verificar los detalles de la configuración de su alojamiento web. Para ello, consulte la sección [« Información técnica de su alojamiento web »](./#informacion-tecnica-de-su-alojamiento-web) al final de esta guía. 

- Podrá modificar la versión PHP de su alojamiento web, o bien en [el área de cliente de OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/world/&ovhSubsidiary=ws) ("**Configuración**"), o bien modificando el archivo .ovhconfig. También se pueden llevar a cabo configuraciones mixtas en estas últimas. Tiene a su disposición instrucciones detalladas en nuestras guías:

[Configurar el archivo .ovhconfig de un alojamiento web](/pages/web_cloud/web_hosting/ovhconfig_configuration)  
[Modificar la configuración de un alojamiento web](/pages/web_cloud/web_hosting/ovhconfig_modify_system_runtime)

> [!primary]
> El archivo .ovhconfig funciona en la raíz del alojamiento web y en las subcarpetas de primer nivel (normalmente _/www/_). La única forma de reemplazar los parámetros principales del archivo .ovhconfig es utilizar otro archivo .ovhconfig en una subcarpeta.
> El hecho de ubicar este archivo más en profundidad en la estructura de la carpeta no tendrá ningún efecto (por ejemplo, _/www/test/_, _/www/test/test2/_). Asegúrese de que el archivo puede ser leído por su CMS (CHMOD 604 o 644).

#### PHP-FPM

PHP-FPM está activo por defecto en la infraestructura de alojamiento web con el objetivo de acelerar las respuestas PHP. Tenga en cuenta que puede que no esté activo si ejecuta un antiguo plan de alojamiento web que no haya actualizado (servicios contratados antes de 2014).

*Algunas variables son diferentes sin PHP-FPM:*

|Variable|Sin PHP-FPM|Con PHP-FPM|
|---|---|---|
|max_execution_time|120s|165s|
|max_input_vars|2000|16000|
|memory_limit|128M|512M|

#### Scripts PHP

Una vez conectado a su alojamiento web por SSH, el tráfico saliente se bloqueará por razones de seguridad. Le recomendamos que utilice scripts PHP. Para más información, consulte nuestra [guía SSH](/pages/web_cloud/web_hosting/ssh_on_webhosting). Puede consultar el manual oficial [PHP manual](https://www.php.net/manual/es/function.system.php) para la ejecución de comandos.

Por ejemplo, puede utilizar la función *gethostbyaddr()* para recuperar el nombre del host:

```php
1. <?php
2. echo gethostbyaddr($_SERVER["REMOTE_ADDR"]);
3. ?>
```

> [!warning]
> OVHcloud no fuerza las actualizaciones PHP. Los clientes son los responsables de la seguridad de sus servicios y de la actualización periódica del software instalado.
>

#### Información técnica de su alojamiento web

Consulte las páginas de información respectiva para verificar las librerías disponibles para su plan de hosting.

Puede consultar información detallada de su cluster en este enlace: <https://webhosting-infos.hosting.ovh.net>

Sustituya el cluster indicado en la URL por el suyo. Para saber en qué cluster de alojamiento web se encuentra su servicio, conéctese al [área de cliente de OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/world/&ovhSubsidiary=ws){.external} y seleccione `Web Cloud`{.action}. Haga clic en `Alojamientos`{.action} y seleccione el alojamiento correspondiente. A continuación, haga clic en la pestaña `FTP - SSH`{.action}. La URL de acceso a su alojamiento le indicará el número de cluster.

Para conocer las particularidades técnicas del hosting Cloud Web, diríjase directamente al enlace <https://cloudweb-infos.hosting.ovh.net/>.

## Política de cookies

**Cookies y rastreadores utilizados como parte de la prestación del servicio de alojamiento compartido.**

Para asegurar el correcto funcionamiento de los sitios web alojados como parte del servicio de alojamiento compartido, la cookie «SERVER ID» se almacena en los terminales de los visitantes de estos sitios web. La cookie «SERVER ID» permite garantizar un servicio de balanceo de carga del tráfico entrante entre las diferentes infraestructuras utilizadas para el alojamiento del sitio web (OVHcloud Load Balancer). Permite al usuario permanecer en el mismo servidor host durante toda la sesión. Esto permite mantener y garantizar la coherencia del recorrido del usuario.

La cookie SERVER ID constituye una escritura en el terminal del usuario que indica la instancia (servidor) de la infraestructura con la que el usuario interacciona. La cookie es anónima en el sentido de que no se utiliza ningún dato de carácter personal del usuario.

La cookie «SERVER ID» se almacena en el terminal del usuario durante menos de 24 horas.

Al tratarse de una cookie necesaria para el funcionamiento del servicio de alojamiento compartido y anónimo, no requiere del consentimiento previo del visitante del sitio web en términos del Reglamento General de Protección de Datos (RGPD). 

## Información sobre las herramientas estadísticas

**OVHcloud Web Statistics**

OVHcloud pone a disposición del cliente estadísticas de afluencia y de medición de audiencia del o de los sitios web alojados como parte del servicio de alojamiento compartido (en lo sucesivo «OVHcloud Web Statistics»). OVHcloud Web Statistics permite en particular identificar la zona geográfica de los visitantes de los sitios web alojados como parte del servicio de alojamiento compartido, las características de sus terminales, de las páginas visitadas y los códigos HTTP. OVHcloud Web Statistics se activa por defecto como parte del servicio de alojamiento compartido y puede desactivarse a petición del cliente contactando con el servicio técnico. Para ofrecer «OVHcloud Web Statistics», es necesario el tratamiento de datos por parte de OVHcloud.

Los informes de OVHcloud Web Statistics se realizan a partir de datos de tráfico anonimizados, como la dirección IP y los logs de los usuarios de los sitios web alojados como parte del servicio de alojamiento compartido, la URL de la consulta, la duración de la consulta y el «useragent».

Para ser utilizados por OVHcloud Web Statistics, los datos mencionados anteriormente se anonimizan y se agrupan mediante algoritmos realizados por OVHcloud, en sus propias infraestructuras. En particular, la dirección IP del visitante presente en los datos de tráfico se extrae de forma anonimizada con el fin de procesarla y analizarla para determinar su geolocalización (a escala regional). De este modo no se conserva en el marco de OVHcloud Web Statistics ningún dato de carácter personal que permita la identificación directa o indirecta de los visitantes citados anteriormente.  

## Más información

[Conectarse al espacio de almacenamiento de su alojamiento web](/pages/web_cloud/web_hosting/ftp_connection)

[Habilitar HTTPS en un sitio web con certificado SSL](/pages/web_cloud/web_hosting/ssl-activate-https-website)

[Optimización del rendimiento de un sitio web](/pages/web_cloud/web_hosting/optimise_your_website_performance)

Interactúe con nuestra comunidad de usuarios en <https://community.ovh.com/en/>.
