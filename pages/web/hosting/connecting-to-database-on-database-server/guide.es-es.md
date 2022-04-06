---
title: 'Conectarse a la base de datos de su servidor de bases de datos'
slug: coneccion-base-de-datos-servidor-bdd
excerpt: 'Cómo conectarse a la base de datos'
section: CloudDB
order: 3
---

**Última actualización: 03/02/2022**

## Objetivo

Es posible consultar el contenido de la base de datos a través de una interfaz. Para ello, existen varias formas de conectarse.

**Esta guía explica cómo conectarse a una base de datos en un servidor de bases de datos.**

## Requisitos

- Tener contratado un plan de [Cloud Databases](https://www.ovh.es/cloud-databases){.external}.
- Haber iniciado sesión en el [área de cliente de OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.es/&ovhSubsidiary=es){.external}.

## Procedimiento

> [!primary]
>
> Tenga en cuenta que este producto no permite acceso "root".
> <br> Los comandos SQL genéricos funcionan sin ningún problema, y los programas de tipo HeidiSQL o SQuirreL SQL son totalmente compatibles.
> 

### Importar una base de datos MySQL o MariaDB 

> [!primary]
>
> Como MariaDB es un derivado de MySQL, los distintos comandos son exactamente los mismos para los dos tipos de bases de datos.
> 

####  Por phpMyAdmin OVHcloud

Acceda a su área de cliente. Haga clic en la pestaña `Web` y seleccione `Base de datos`{.action}. Seleccione el nombre del servidor de bases de datos.

En la pestaña `Información general`, el enlace de acceso se encuentra en el recuadro **"Administración de la base de datos"**, bajo el epígrafe "Interfaz de usuario".

![private-sql](images/private-sql-phpma01.png){.thumbnail}

Acceda a la página de conexión de phpMyAdmin.

![private-sql](images/private-sql-phpma02.png){.thumbnail}

- **Servidor**: introduzca el nombre del host del servidor en la pestaña `Información general`, en el recuadro **"Administración de la base de datos"**, bajo el epígrafe "Nombre del host" del apartado **SQL**.
- **Usuario**: introduzca el nombre de usuario creado en la pestaña `Usuarios y permisos` del servidor de bases de datos.
- **Contraseña**: introduzca la contraseña del usuario correspondiente.
- **Puerto**: introduzca el puerto indicado en la pestaña `Información general`, en el recuadro **"Administración de la base de datos"**, bajo el epígrafe "Puerto" del apartado **SQL**.

Si la conexión se ha completado, se mostrará la siguiente página de phpMyAdmin.

![private-sql](images/private-sql-phpma03.png){.thumbnail}

> **En caso de error #1045**
> 
> En caso de error #1045, significa que la identificación es incorrecta. Por lo tanto, es necesario comprobar el nombre de usuario y/o la contraseña.
> 
> **En caso de error #2005**
> 
> En caso de error #2005, le recomendamos que compruebe el nombre del servidor y si este está en funcionamiento.

#### Conexión a la base de datos fuera del área de cliente

Para conectarse a la base de datos, asegúrese de que dispone de la siguiente información:

- **Servidor**: el nombre del host del servidor puede verse en la pestaña `Información general` del servidor de bases de datos, en el recuadro **"Administración de la base de datos"**, bajo el epígrafe "Nombre del host" del apartado **SQL**.
- **Usuario**: El nombre de usuario creado en la pestaña `Usuarios y permisos` del servidor de bases de datos.
- Cambiar la contraseña del usuario **root**
- **Puerto**: el puerto puede verse en la pestaña `Información general` del servidor de bases de datos, en el recuadro **"Administración de la base de datos"**, bajo el epígrafe "Puerto" de la parte **SQL**.
- **Nombre de la base de datos**: las bases de datos se muestran en la pestaña `Bases de datos` del servidor de bases de datos.

##### 1. Conexión en línea de comandos

```bash
mysql --host=servidor --user=usuario --port=puerto --contraseña nombre_de_la_BD
```

##### 2. Conexión mediante script PHP

```php
1. <?php
2. $db = new PDO('mysql:host=host;port=port;dbname=dbname', 'username', 'password');
3. ?>
```

##### 3. Conexión a través de la aplicación SQuirreL SQL

> [!primary]
>
> En nuestro ejemplo, utilizamos el software de código abierto SQuirrel, pero otras interfaces, como HeidiSQL o Adminer, son totalmente compatibles. 

- Ejecute SQuirreL SQL, abra el menú `{.action}Aliases`{.action} y haga clic en +.

![](images/1.png){.thumbnail} ejecutar SQuirreL SQL

- Cumplimente los campos como se indica a continuación y acepte con el botón `{.action}OK:
    - **Name**: Indique un nombre.
    - **Driver**: Seleccione « MySQL Driver »
    - **URL**: Indique la dirección del servidor y el puerto en formato \*\*jdbc:mysql://server:port
    - **User name**: Indique el nombre de usuario.
    - **Password**: Indique la contraseña.

![](images/2.png){.thumbnail} conexión a la base de datos

- Confirme con el botón `{.action}Connect.

![](images/3.png){.thumbnail} confirmación de la conexión

Se establecerá la conexión a la base de datos:

![](images/4.PNG){.thumbnail} conexión a la base de datos


##### 3.4. Conexión mediante phpMyAdmin

Puede utilizar su propia interfaz phpMyAdmin para explorar el contenido de su base de datos. Para ello, instale phpMyAdmin en su propio servidor o alojamiento web. Durante la instalación, asegúrese de que la información de su servidor de bases de datos y de la base de datos es correcta para que phpMyAdmin pueda conectarse a ella.



### Importar una base de datos PostgreSQL 


Para conectarse a la base de datos, asegúrese de que dispone de la siguiente información:

- **Servidor**: el nombre del host del servidor puede verse en la pestaña `Información general` del servidor de bases de datos, en el recuadro **"Administración de la base de datos"**, bajo el epígrafe "Nombre del host" del apartado **SQL**
- **Usuario**: El nombre de usuario creado en la pestaña `Usuarios y permisos` del servidor de bases de datos
- **Contraseña**: la contraseña del usuario 
- **Puerto**: el puerto puede verse en la pestaña `Información general` del servidor de bases de datos, en el recuadro **"Administración de la base de datos"**, bajo el epígrafe "Puerto" de la parte **SQL**
- **Nombre de la base de datos**: las bases de datos se muestran en la pestaña `Bases de datos` del servidor de bases de datos.

#### Conexión en línea de comandos

> [!primary]
>
> Para un servidor SQL privado, esta acción solo es posible por [SSH](https://docs.ovh.com/es/hosting/web_hosting_ssh_en_alojamiento_compartido/){.external} desde un alojamiento compartido de OVHcloud.

mysql --host=servidor --user=nombre_de_usuario --port=puerto --password=contraseña nombre_base_de_datos

#### Conexión mediante script PHP

> [!primary]
>
> Para un servidor SQL privado, la ejecución de este script solo puede realizarse desde un alojamiento compartido de OVHcloud.

1. <?php
2. $db = new PDO('mysql:host=host;port=puerto;dbname=nombre_base_de_datos', 'username', 'password');
3. ?>

#### Conexión a través de la aplicación SQuirreL SQL

> [!primary]
>
> En nuestro ejemplo, utilizamos el software de código abierto SQuirrel, pero otras interfaces, como HeidiSQL o Adminer, son totalmente compatibles.

- Ejecute SQuirreL SQL, abra el menú `{.action}Aliases`{.action} y haga clic en +.

![](images/1.png){.thumbnail} ejecutar SQuirreL SQL

- Cumplimente los campos como se indica a continuación y acepte con el botón `{.action}OK:
    - **Name**: Indique un nombre.
    - **Driver**: Seleccione « PostgreSQL »
    - **URL**: Indique la dirección del servidor y el puerto en formato \*\*jdbc:postgresql://server:port/database
    - **User name**: Indique el nombre de usuario.
    - **Password**: Indique la contraseña.

![](images/2.png){.thumbnail} conexión a la base de datos

- Confirme con el botón `{.action}Connect.

![](images/3.png){.thumbnail} confirmación de la conexión

Se establecerá la conexión a la base de datos:

![](images/4.PNG){.thumbnail} conexión a la base de datos

## Más información

Interactúe con nuestra comunidad de usuarios en <https://community.ovh.com/en/>.

