---
title: 'Cambiar la clave de activación de Windows Server'
excerpt: 'Cómo cambiar la clave de activación de Windows Server'
updated: 2022-07-07
---

> [!primary]
> Esta traducción ha sido generada de forma automática por nuestro partner SYSTRAN. En algunos casos puede contener términos imprecisos, como en las etiquetas de los botones o los detalles técnicos. En caso de duda, le recomendamos que consulte la versión inglesa o francesa de la guía. Si quiere ayudarnos a mejorar esta traducción, por favor, utilice el botón «Contribuir» de esta página.
> 

## Objetivo

Al instalar un sistema operativo Windows Server, es posible que la clave de activación registrada no sea la correcta. Eso ocurre cuando el sistema se instala en versión de prueba, en cuyo caso la clave tiene una duración de 120 días. Una vez transcurrido este período, ya no podrá utilizar el sistema.

**Esta guía explica cómo cambiar la clave de activación de su entorno Windows Server.**

## Requisitos

- Disponer de un [servidor dedicado](https://www.ovhcloud.com/es-es/bare-metal/os/server-windows/) con Windows instalado en su cuenta OVHcloud
- Disponer de una licencia Windows SPLA en su cuenta de OVHcloud
- Tener acceso administrativo al servidor a través de una conexión de escritorio remoto

## Procedimiento

### Eliminar la clave anterior

Cuando el sistema está en versión de prueba, se registra una clave por defecto. Para modificarla, abra el cuadro de diálogo **Ejecutar** (teclas `Windows`+`R`).

![Abrir el cuadro de diálogo Ejecutar](images/executer.png){.thumbnail}

![Ejecutar](images/executer2.png){.thumbnail}

A continuación, introduzca el siguiente comando:

```
cscript.exe c:\windows\system32\slmgr.vbs -upk
```

### Introducir la nueva clave

Ya puede introducir la nueva clave. Para ello, en el cuadro de diálogo **Ejecutar**, introduzca el siguiente comando:

```
cscript.exe c:\windows\system32\slmgr.vbs -ipk CLAVE_KMS
```

Estas son las claves KMS disponibles para cada sistema operativo:

|Sistema operativo|Clave KMS|
|---|---|
|Windows Server 2008 Standard|TM24T-X9RMF-VWXK6-X8JC9-BFGM2|
|Windows Server 2008 Entreprise|YQGMW-MPWTJ-34KDK-48M3W-X4Q6V|
|Windows Server 2008 Datacenter|7M67G-PC374-GR742-YH8V4-TCBY3|
|Windows Server 2008 R2 Standard|YC6KT-GKW9T-YTKYR-T4X34-R7VHC|
|Windows Server 2008 R2 Entreprise|489J6-VHDMP-X63PK-3K798-CPX3Y|
|Windows Server 2008 R2 Datacenter|74YFP-3QFB3-KQT8W-PMXWJ-7M648|
|Windows Server 2012 Standard|XC9B7-NBPP2-83J2H-RHMBY-92BT4|
|Windows Server 2012 Datacenter|48HP8-DN98B-MYWDG-T2DCC-8W83P|
|Windows Server 2012 R2 Standard|D2N9P-3P6X9-2R39C-7RTCD-MDVJX|
|Windows Server 2012 R2 Datacenter|W3GGN-FT8W3-Y4M27-J84CP-Q3VJ9|
|Windows 8.1 Pro|GCRJD-8NW9H-F2CDX-CCM8D-9D6T9|
|Windows Server 2016 Datacenter|CB7KF-BWN84-R7R2Y-793K2-8XDDG|
|Windows Server 2016 Standard|WC2BQ-8NRM3-FDDYY-2BFGV-KHKQY|
|Windows Server 2016 Essentials|JCKRF-N37P4-C2D82-9YXRT-4M63B|
|Windows Server 2019 Standard|N69G4-B89J2-4G8F4-WWYCC-J464C|
|Windows Server 2019 Datacenter|WMDGN-G9PQG-XVVXX-R3X43-63DFG|
|Windows Server 2022 Standard|VDYBN-27WPP-V4HQT-9VMD4-VMK7H|
|Windows Server 2022 Datacenter|WX4NM-KYWYW-QJJR4-XV3QB-6VM33|

Fuente: [Microsoft](https://docs.microsoft.com/en-gb/windows-server/get-started/kmsclientkeys){.external}

> [!primary]
>
> Las versiones Core utilizan las mismas claves KMS que las versiones no Core.
> 

### Utilizar kms.ovh.net

Para asociar su clave a nuestro robot de activación, introduzca el siguiente comando en el cuadro de diálogo `Ejecutar`{.action}:

```
cscript.exe c:\windows\system32\slmgr.vbs -skms kms.ovh.net
```

> [!primary]
>
> Si tiene un VPS o una instancia de Public Cloud, debe utilizar **kms.cloud.ovh.net**.
> 

### Activar el sistema
Por último, para activar su sistema Windows, ejecute el siguiente comando:

```
cscript.exe c:\windows\system32\slmgr.vbs -ato
```

## Más información

Interactúe con nuestra comunidad de usuarios en <https://community.ovh.com/en/>.