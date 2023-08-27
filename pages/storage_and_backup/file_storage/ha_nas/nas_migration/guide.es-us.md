---
title: Migración de datos de un NAS-HA a otro a través de NFS
excerpt: Cómo migrar los datos de un NAS-HA a otro mediante NFS compartido.
updated: 2021-02-09
---

> [!primary]
> Esta traducción ha sido generada de forma automática por nuestro partner SYSTRAN. En algunos casos puede contener términos imprecisos, como en las etiquetas de los botones o los detalles técnicos. En caso de duda, le recomendamos que consulte la versión inglesa o francesa de la guía. Si quiere ayudarnos a mejorar esta traducción, por favor, utilice el botón «Contribuir» de esta página.
> 

## Objetivo

Esta guía explica cómo transferir los datos de un NAS-HA a otro. 

## Requisitos

Para realizar la transferencia de sus datos, es necesario :

- Un NAS-HA OVHcloud
- Una distribución compatible con NFS
- Haber montado previamente un NAS-HA siguiendo la guía para [montar un NAS-HA utilizando un NFS](/pages/storage_and_backup/file_storage/ha_nas/nas_nfs){.external} compartido.

## Procedimiento

Compatibilidad: Debian 6/7/8 y Ubuntu 12/13/14

Para transferir sus datos, utilizaremos el comando `rsync`. Existen diversas formas de transferir los datos. Puede utilizar una en lugar de otra.

En el ejemplo que se muestra a continuación, podrá transferir sus datos de un punto de montaje de Origen a un punto de montaje de Destino.

```sh
rsync -Pva /mnt/SrcNas /mnt/DstNas
```

|Argumento|Descripción|
|---|---|
|SrcNas|Punto de montaje de origen|
|DstNas|Punto de montaje de destino|

> [!alert]
>
> Atención: Si añade más opciones a rsync, estas opciones podrían no ser compatibles con el sistema de permisos y permisos de los NAS-HA.
>

## Más información

Si necesita formación o asistencia técnica para implantar nuestras soluciones, póngase en contacto con su representante de ventas o haga clic en [este enlace](https://www.ovhcloud.com/es/professional-services/) para obtener un presupuesto y solicitar un análisis personalizado de su proyecto a nuestros expertos del equipo de Servicios Profesionales.

Interactúe con nuestra comunidad de usuarios en [https://community.ovh.com/en/](https://community.ovh.com/en/){.external}.