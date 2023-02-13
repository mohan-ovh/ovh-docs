---
title: 'Poner una instancia en modo de rescate'
excerpt: 'Poner una instancia en modo de rescate'
slug: poner_una_instancia_en_modo_de_rescate
legacy_guide_number: g2029
section: 'Gestión de las instancias desde el área de cliente'
order: 03
updated: 2023-01-04
---

**Última actualización: 04/01/2023**

## Objetivo

Si su instancia no se ha configurado correctamente o si ha perdido su clave SSH, es posible que no pueda acceder a su instancia.

En esos casos, puede utilizar el modo de rescate para reconfigurar su instancia o recuperar sus datos. 

**Esta guía muestra cómo poner una instancia en modo de rescate**

## Requisitos

* Tener una [instancia de Public Cloud](https://www.ovhcloud.com/es/public-cloud/){.external} en su cuenta de OVHcloud
* Tener acceso al [área de cliente de OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.es/&ovhSubsidiary=es){.external}
* Tener acceso a la instancia por SSH como administrador (usuario raíz).

## Procedimiento

> [!alert]
>
> Hasta la fecha, el modo de rescate para las instancias Metal no está accesible desde el área de cliente de OVHcloud. Para más información, consulte nuestra guía sobre el [modo de rescate para las instancias Metal](https://docs.ovh.com/es/public-cloud/metal-instance-rescue-mode/).

### Activar el modo de rescate

En primer lugar, inicie sesión en el [área de cliente de OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.es/&ovhSubsidiary=es){.external} para acceder al panel de control y, seguidamente, haga clic en el menú `«Public Cloud»`{.action}.

A continuación, seleccione su proyecto de Public Cloud en el menú lateral a la izquierda de la pantalla y acceda a «Instancias».

A continuación, haga clic en los 3 puntos a la derecha de la instancia y seleccione `«Reiniciar en modo de rescate»`{.action}

![control panel](images/rescue2022.png){.thumbnail}

Entonces verá el cuadro de diálogo «Reiniciar en modo de rescate». Haga clic en la lista desplegable para seleccionar la distribución de Linux que desea utilizar en el modo de rescate y, a continuación, en el botón `«Reiniciar»`{.action}.

![control panel](images/rescue2.png){.thumbnail}

Una vez que la instancia se haya reiniciado en modo de rescate, se mostrará un panel informativo con los métodos de acceso disponibles. La **contraseña del modo de rescate** temporal solo se mostrará en la consola VNC. Haga clic en su instancia en la tabla y acceda a la pestaña `Consola VNC`{.action} para consultarla.

![control panel](images/rescuedata.png){.thumbnail}


### Acceso a sus datos

Una vez activado el modo de rescate, los datos de su instancia se adjuntarán como un disco adicional. Ahora, deberá instalarlo realizando los pasos siguientes.

En primer lugar, cree una conexión SSH a su instancia. Una vez conectado, verifique los discos disponibles con este comando:

```
root@instance:/home/admin# lsblk

NAME MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
vda 253:0 0 1G 0 disk
└─vda1 253:1 0 1023M 0 part /
vdb 253:16 0 10G 0 disk
└─vdb1 253:17 0 10G 0 part
```

A continuación, instale la partición:

```
root@instance:/home/admin# mount /dev/vdb1 /mnt
```

Podrá acceder a sus datos desde la carpeta /mnt.

### Desactivar el modo de rescate

Una vez que haya completado sus tareas, puede desactivar el modo de rescate reiniciando normalmente su instancia. Para hacerlo, haga clic en la flecha desplegable de su instancia y seleccione `«Salir del modo de rescate»`{.action}.

![control panel](images/rescueexit2022.png){.thumbnail}

> [!warning]
> Si el botón `Salir del modo de rescate`{.action} no aparece una vez que la instancia esté en modo de rescate, le recomendamos que actualice la pestaña.
>

### Activar el modo rescate utilizando la API de OpenStack

También puede activar el modo de rescate a través de la API OpenStack utilizando el siguiente comando:

```
# root@server:~# nova rescue INSTANCE_ID
```

Para salir del modo de rescate, utilice el siguiente comando:

```
# root@server:~# nova unrescue INSTANCE_ID
```

## Más información

Interactúe con nuestra comunidad de usuarios en <https://community.ovh.com/en/>.