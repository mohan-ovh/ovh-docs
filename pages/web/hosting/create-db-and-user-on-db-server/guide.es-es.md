---
title: 'Crear bases de datos y usuarios en un servidor de bases de datos'
slug: crear-bases-de-datos-y-usuarios
excerpt: 'Cómo crear una base de datos en un servidor de bases de datos'
section: CloudDB
order: 2
---

**Última actualización: 03/02/2022**

## Objetivo

Una base de datos (también llamada *database*, DB o BD) permite almacenar elementos dinámicos, como comentarios o artículos. Prácticamente todos los sistemas de gestión de contenidos (*content management system* o CMS), como WordPress o Joomla, utilizan bases de datos.

**Esta guía explica cómo crear una base de datos en un servidor de bases de datos.**

## Requisitos

- Tener contratado un plan de [Cloud Databases](https://www.ovh.es/cloud-databases/){.external}.
- Haber iniciado sesión en el [área de cliente de OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.es/&ovhSubsidiary=es){.external}.

## Procedimiento

### Crear una base de datos

Acceda al [área de cliente de OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.es/&ovhSubsidiary=es){.external}. Haga clic en la pestaña `Web Cloud` y seleccione `Base de datos`{.action}. Seleccione el nombre del servidor de bases de datos.

Abra la pestaña `Bases de datos` y haga clic en `Añadir una base de datos.`{.action}

![private-sql](images/private-sql-createdb01.png){.thumbnail}

Introduzca los campos de acuerdo con los criterios indicados. Es posible crear directamente un usuario marcando la casilla **"Crear un usuario"**:

- **Nombre de la BD** (obligatorio): Nombre que tendrá la base de datos.
- **Nombre de usuario** (solo si está marcada la casilla `Crear un usuario`): usuario que podrá conectarse a la base de datos y realizar consultas.
- **Permisos** (solo si está marcada la casilla `Crear un usuario`): son los permisos que se asociarán al usuario sobre la base de datos. Para un uso convencional, seleccione `Administrador`{.action}. Más adelante podrá modificar los permisos.
- **Contraseña**/**Confirmar contraseña**\** (solo si está marcada la casilla `Crear usuario`): seleccione una contraseña y luego confírmela introduciéndola de nuevo.

Haga clic en `Aceptar`{.action}.

![private-sql](images/private-sql-createdb02.png){.thumbnail}

### Crear un usuario

Para utilizar un servidor de bases de datos de OVHcloud, es necesario crear usuarios que tengan permisos específicos para conectarse a una base de datos. 

Acceda al [área de cliente de OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.es/&ovhSubsidiary=es){.external}. Haga clic en la pestaña `Web Cloud` y seleccione `Base de datos`{.action}. Seleccione el nombre del servidor de bases de datos.

Acceda a la pestaña `Usuarios y permisos` y haga clic en `Añadir un usuario`{.action}

![private-sql](images/private-sql-user01.png){.thumbnail}

Introduzca un nombre de usuario y una contraseña y haga clic en `Aceptar`{.action}. 

### Gestionar los derechos de los usuarios

Para autorizar a un usuario a realizar acciones en una base de datos, es necesario asignarle permisos.

Para administrar los permisos de cada usuario, acceda al [área de cliente de OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.es/&ovhSubsidiary=es){.external}. Haga clic en la pestaña `Web Cloud` y seleccione `Base de datos`{.action}. Seleccione el nombre del servidor de bases de datos. Haga clic en la pestaña `Usuarios y permisos`.

Haga clic en el botón `...`{.action} a la derecha del usuario correspondiente y, seguidamente, en `Gestionar los permisos`{.action}.

![private-sql](images/private-sql-rights01.png){.thumbnail}

En la columna izquierda, **"Bases de datos"**, encontrará una lista de las bases de datos del servidor de bases de datos.

La descripción de los tres tipos de derechos propuestos es la siguiente:

- **Administrador:** autorización de consultas de tipo **Select, Insert, Update, Delete, Create, Alter y Drop.**
- **Lectura/Escritura:** autorización de consultas de tipo **Select, Insert, Update y Delete.**
- **Lectura:** autorización de consultas de tipo **Select**
- **Ninguno:** sin derechos sobre la base de datos

> [!primary]
> 
> La segmentación de los permisos mencionados es exclusiva de OVHcloud. De este modo, un usuario con permisos **"_Administrador_"** podrá realizar **DLL** (Data_Definición_Language) y **DML** (Data_Manipulation_Language), mientras que un usuario con permisos **"Lectura/Escritura"** solo realizará la Manipulación del DML (Data_Manipulation_Language).

![private-sql](images/private-sql-rights02.png){.thumbnail}

#### Eliminar una base de datos

> [!warning]
>
> Antes de eliminar una base de datos en un servidor de bases de datos, no se comprueba el contenido de la base de datos.
> Se eliminará incluso si los datos todavía están almacenados en él.
> Por este motivo, se recomienda que se cree y descargue una copia de seguridad de su lado antes de cualquier eliminación.
> 

Acceda al [área de cliente de OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.es/&ovhSubsidiary=es){.external}. Haga clic en la pestaña `Web Cloud` y seleccione `Base de datos`{.action}. Seleccione el nombre del servidor de bases de datos.

Para eliminar una base de datos en su servidor de bases de datos, abra la pestaña `Bases de datos`, haga clic en el botón `...`{.action} situado a la derecha de la base de datos correspondiente y seleccione `Eliminar la base`{.action}.

![private-sql](images/private-sql-deldb01.png){.thumbnail}


## Más información

Interactúe con nuestra comunidad de usuarios en <https://community.ovh.com/en/>.

