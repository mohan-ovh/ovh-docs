---
title: Configurar una nueva instalación de Windows Server
excerpt: "Cómo activar la conexión al escritorio remoto, la respuesta ICMP y los registros de arranque"
updated: 2023-02-15
---

> [!primary]
> Esta traducción ha sido generada de forma automática por nuestro partner SYSTRAN. En algunos casos puede contener términos imprecisos, como en las etiquetas de los botones o los detalles técnicos. En caso de duda, le recomendamos que consulte la versión inglesa o francesa de la guía. Si quiere ayudarnos a mejorar esta traducción, por favor, utilice el botón «Contribuir» de esta página.
> 

**Última actualización: 15/02/2023**

## Objetivo

Tras la nueva instalación de un sistema operativo Windows Server en un VPS, es posible desactivar el acceso remoto y la respuesta ICMP (Internet Control Message Protocol).<br>
No obstante, puede utilizar el KVM de OVHcloud para acceder a su VPS y así configurar el firewall de Windows para reactivar ICMP y autorizar las conexiones a través del Remote Desktop Protocol.<br>
La activación de los logs de arranque (*boot logs*) Windows puede ser útil para los diagnósticos de errores del servidor.

**Esta guía explica cómo activar ICMP, Remote Desktop Protocol y los logs de arranque en un VPS Windows.**

## Requisitos

- Una distribución Windows instalada en un [VPS](https://www.ovhcloud.com/es/vps/).
- Tienes acceso a tu [Panel de configuración de OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/world/&ovhSubsidiary=ws).

## Procedimiento

### Paso 1: acceso al KVM

Para acceder a la consola KVM de su VPS, consulte la [guía KVM VPS](/pages/cloud/vps/using_kvm_for_vps).

### Paso 2: finalizar la instalación de Windows

Una vez establecida la sesión KVM, se mostrarán los monitores de configuración inicial. Aquí debe configurar su **país/región**, el **idioma de Windows** y su **teclado**. Una vez realizada la operación, haga clic en `Next`{.action}.

![KVM](images/setup-03.png){.thumbnail}

En la segunda pantalla, introduzca una contraseña para su cuenta de administrador y confírmela y haga clic en `Finish`{.action}.

![KVM](images/setup-04.png){.thumbnail}

Windows aplicará sus preferencias y mostrará la pantalla de conexión. Haga clic en el botón `Send CtrlAltDel`{.action} en la esquina superior derecha para conectarse.

![KVM](images/setup-05.png){.thumbnail}

Introduzca la contraseña que haya creado para su cuenta de administrador y haga clic en la flecha.

![KVM](images/setup-06.png){.thumbnail}

La configuración inicial ha finalizado. Una vez conectado, deberá modificar los parámetros necesarios del firewall de Windows.

### Paso 3: modificar el firewall de Windows

Abra las `Herramientas de administración`{.action} del panel de configuración `Sistema y Seguridad`{.action} y haga doble clic en `Firewall Windows con seguridad avanzada`{.action}.

![Admin](images/windows4.png){.thumbnail}

Aquí puede activar las respectivas reglas "ICMP" y "Remote Desktop" (escritorio remoto). Haga clic derecho en la regla y seleccione `Autorizar regla`{.action} en el menú contextual.

![Activado](images/windows5.png){.thumbnail}

El servidor debe responder a las solicitudes que utilicen estos protocolos.

> [!primary]
> Para proteger su sistema Windows con reglas de firewall, consulte nuestra guía [Configurar el firewall de Windows](/pages/cloud/vps/activate-port-firewall-soft-win).
>

### Activación de los logs de arranque (boot logs) Windows (opcional)

Conéctese al servidor a través de una sesión de escritorio remoto o de [KVM](/pages/cloud/vps/using_kvm_for_vps). Abra el menú Iniciar Windows y haga clic en `Ejecutar`{.action}.

![Bootlog](images/windowsboot1.png){.thumbnail}

Introduzca "msconfig" y haga clic en `OK`{.action}.

![Bootlog](images/windowsboot2.png){.thumbnail}

En la nueva ventana, marque la casilla situada junto a `Boot log`. Haga clic en `OK`{.action}.

![Bootlog](images/windowsboot3.png){.thumbnail}

La próxima vez que inicie el servidor, los logs se guardarán en un archivo .txt. La ruta del archivo es `C:\Windows\ntbtlog.txt`.

Para acceder al contenido de este archivo en modo de rescate, siga las indicaciones de [la guía del modo de rescate del VPS](/pages/cloud/vps/rescue).

## Más información

Interactúe con nuestra comunidad de usuarios en <https://community.ovh.com/en/>.