---
title: 'Reparticionar un VPS tras un upgrade'
updated: 2021-05-18
---

> [!primary]
> Esta traducción ha sido generada de forma automática por nuestro partner SYSTRAN. En algunos casos puede contener términos imprecisos, como en las etiquetas de los botones o los detalles técnicos. En caso de duda, le recomendamos que consulte la versión inglesa o francesa de la guía. Si quiere ayudarnos a mejorar esta traducción, por favor, utilice el botón «Contribuir» de esta página.
>

## Objetivo

Al realizar el upgrade de un VPS, es posible que tenga que reparticionar su espacio de almacenamiento.

> [!warning]
>
> El reparticionamiento de un VPS puede dañar los datos que contiene de forma definitiva. OVHcloud no podrá ser considerado responsable de su deterioro o pérdida. Antes de realizar cualquier acción, le recomendamos que haga una copia de seguridad de sus datos.
>

**Esta guía explica los pasos necesarios para aumentar el espacio de almacenamiento de su VPS**.

## Requisitos

- Tener acceso de administrador al VPS (Windows).
- Haber reiniciado el servidor en [modo de rescate](/pages/bare_metal_cloud/virtual_private_servers/rescue) (Linux).

## Procedimiento

Tras el upgrade, la RAM y el procesador (CPU) se ajustarán de manera automática. Sin embargo, el espacio de almacenamiento no se actualiza sistemáticamente.

### Realizar una copia de seguridad de los datos

Ampliar una partición puede provocar la pérdida de datos, por lo que **le recomendamos encarecidamente que realice una copia de seguridad** de los datos de su VPS.

### Desmontar la partición

En las antiguas gamas de VPS, las particiones se montarán automáticamente en modo de rescate. Utilice el siguiente comando para identificar la ubicación de montaje de la partición:

```sh
lsblk
```

La partición correspondiente al modo de rescate será la montada en el directorio `/`, que es en realidad la raíz del sistema. En cambio, es probable que la partición del VPS se sitúe en un directorio asociado a "/mnt".

No obstante, si su VPS pertenece a la gama actual, la partición no se montará automáticamente. Si la columna del resultado MOUNTPOINT lo confirma, puede ignorar el paso de desmontaje.

```sh
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda 254:0 0 10G 0 disk
└─sda1 254:1 0 10G 0 part /
sdb 254:16 0 25G 0 disk
└─sdb1 254:17 0 25G 0 part /mnt/sdb1
```

Para cambiar el tamaño de la partición, debe desmontarla. Para desmontar dicha partición, utilice el siguiente comando:

```sh
umount /dev/sdb1
```

### Comprobar el sistema de archivos (*filesystem*)

Una vez desmontada la partición, es aconsejable comprobar el sistema de archivos (*filesystem check*) para detectar posibles errores. Utilice el siguiente comando:

```sh
e2fsck -yf /dev/sdb1
 
e2fsck 1.42.9 (4-Feb-2014)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sdb1: 37870/1310720 files (0.2% non-contiguous), 313949/5242462 blocks
```

Si encuentra un error, deberá adoptar las medidas adecuadas en cada caso. Estos son algunos de los errores más frecuentes:

- **bad magic number in superblock**: No continúe. Para solucionar este problema, consulte el apartado [Cómo solucionar los errores «bad magic number in superblock»](/pages/bare_metal_cloud/virtual_private_servers/upsize_vps_partition#como-solucionar-los-errores-bad-magic-number-in-superblock){.external} de esta guía.

- **/dev/vdb1 has unsupported feature(s): metadata_csum**, seguido de **e2fsck: Get a newer version of e2fsck!**: Actualice **e2fsck**. Si la última versión no está disponible a través de **apt** o cualquier otro gestor de paquetes, deberá compilarla a partir del código fuente.

La lista anterior no es exhaustiva.

### Abrir la aplicación fdisk

Una vez haya comprobado que no existe ningún error en el sistema de archivos, abra la aplicación **fdisk**. Una vez allí, deberá introducir el nombre del disco (y no el de la partición) como parámetro. Si su partición es «sdb1» en lugar de «vdb1», por ejemplo, el nombre del disco será «/dev/sdb».

```sh
fdisk -u /dev/sdb
```

> [!primary]
>
> Esta aplicación dispone de diversos subcomandos, que podrá consultar con el comando `m`.
>

### Eliminar la antigua partición

Antes de eliminar la antigua partición, le recomendamos que anote el número correspondiente al primer sector de la partición. Puede obtener esta información con el comando `p`. El número es el que aparece en el campo «Start». Conserve esta información, ya que la necesitará más adelante.

```sh
Command (m for help): p
 
Disk /dev/sdb: 21.5 GB, 21474836480 bytes
54 heads, 49 sectors/track, 15851 cylinders, total 41943040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000132ff
 
Device Boot Start End Blocks Id System
/dev/sdb1 * *2048* 41941745 20969849 83 Linux
```

> [!warning]
>
> La siguiente operación es irreversible. Asegúrese de disponer de una copia de seguridad de sus datos.
>

A continuación, elimine la partición con el comando `d`.

```sh
Command (m for help): d
Selected partition 1
```

La partición se eliminará automáticamente.

### Crear una nueva partición

Ahora deberá crear la nueva partición con el comando `n`. Le recomendamos que utilice los valores por defecto.

```sh
Command (m for help): n
Partition type:
p primary (0 primary, 0 extended, 4 free)
e extended
Select (default p): p
Partition number (1-4, default 1): 1
First sector (2048-41943039, default 2048): 2048
Last sector, +sectors or +size{K,M,G} (2048-41943039, default 41943039): 41943039
```

En la línea «First sector», asegúrese de que el valor por defecto coincide con el que ha anotado anteriormente. Si es diferente, utilice el valor anotado.

### Hacer que la partición sea de arranque

A continuación, asegúrese de que la partición sea de arranque (*bootable*). Puede hacerlo con el comando `a`.

```sh
Command (m for help): a
 
Partition number (1-4): 1
```

Guarde los cambios y salga de la aplicación con el comando `w`.

```sh
Command (m for help): w
 
The partition table has been altered!
 
Calling ioctl() to re-read partition table.
Syncing disks.
```

### Ampliar el sistema de archivos en la partición

Ahora ya ha ampliado la partición, pero el sistema de archivos sigue ocupando el mismo espacio que antes. Para ampliarlo, introduzca el siguiente comando:

```sh
resize2fs /dev/sdb1
 
resize2fs 1.42.9 (4-Feb-2014)
Resizing the filesystem on /dev/sdb1 to 5242624 (4k) blocks.
The filesystem on /dev/sdb1 is now 5242624 blocks long.
```

### Comprobar los resultados

Para asegurarse de que la operación se ha realizado correctamente, puede montar la partición que acaba de crear y comprobar su tamaño.

```sh
mount /dev/sdb1 /mnt
```

```sh
df -h
 
Filesystem Size Used Avail Use% Mounted on
/dev/sda1 991M 793M 132M 86% /
none 4.0K 0 4.0K 0% /sys/fs/cgroup
udev 1.9G 12K 1.9G 1% /dev
tmpfs 386M 360K 386M 1% /run
none 5.0M 0 5.0M 0% /run/lock
none 1.9G 0 1.9G 0% /run/shm
none 100M 0 100M 0% /run/user
/dev/sdb1 50G 842M 48G 2% /mnt
```

El nuevo tamaño de la partición se mostrará en la columna «Size».

### Cómo solucionar los errores «bad magic number in superblock»

Si el comando `e2fsck` devuelve el mensaje de error «**bad magic number in superblock**», deberá reparar el sistema de archivos utilizando un superbloque de backup. Para acceder a los superbloques de backup disponibles, introduzca el siguiente comando: 

```sh
dumpe2fs /dev/sdb1 | grep superblock
 
Primary superblock at 0, Group descriptors at 1-6
Backup superblock at 32768, Group descriptors at 32769-32774
Backup superblock at 98304, Group descriptors at 98305-98310
Backup superblock at 163840, Group descriptors at 163841-163846
Backup superblock at 229376, Group descriptors at 229377-229382
Backup superblock at 294912, Group descriptors at 294913-294918
Backup superblock at 819200, Group descriptors at 819201-819206
Backup superblock at 884736, Group descriptors at 884737-884742
Backup superblock at 1605632, Group descriptors at 1605633-1605638
Backup superblock at 2654208, Group descriptors at 2654209-2654214
Backup superblock at 4096000, Group descriptors at 4096001-4096006
Backup superblock at 7962624, Group descriptors at 7962625-7962630
Backup superblock at 11239424, Group descriptors at 11239425-11239430
Backup superblock at 20480000, Group descriptors at 20480001-20480006
Backup superblock at 23887872, Group descriptors at 23887873-23887878
```

A continuación, utilice el primer superbloque de backup para comprobar y reparar el sistema de archivos:

```sh
fsck -b 32768 /dev/sdb1
```

### Windows

#### Acceder a File and Storage Services

Puede encontrarlo en el servidor Manager:

![File and Storage Services](images/file-and-storage.png){.thumbnail}

#### Redimensionar el volumen

Haga clic derecho en C: y seleccione `Extend Volume...`{.action}.

A continuación, elija el nuevo tamaño de volumen:

![Set New Volume Size](images/extend.png){.thumbnail}

Escriba el tamaño deseado y haga clic en `Aceptar`{.action}. El volumen se ampliará.

## Más información

Interactúe con nuestra comunidad de usuarios en <https://community.ovh.com/en/>.
