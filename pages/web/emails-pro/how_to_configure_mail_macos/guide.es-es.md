---
title: Configurar una cuenta Email Pro en Mail de macOS
slug: configurar-email-pro-mail-macos
excerpt: Cómo configurar una cuenta Email Pro en Mail de macOS El Capitan, Sierra y High Sierra
section: Configuración del cliente de correo
order: 4
---

**Última actualización: 12/03/2018**

## Objetivo

Es posible configurar sus cuentas Email Pro en el cliente de correo que usted utilice, siempre que sea compatible, para acceder a ellas sin necesidad de una nueva aplicación.

**Esta guía explica cómo configurar una cuenta Email Pro en Mail de macOS El Capitan, Sierra y High Sierra.**

## Requisitos

- Tener una cuenta [Email Pro](https://www.ovh.es/emails/email-pro/){.external}.
- Tener la aplicación Mail instalada en su dispositivo.
- Disponer del nombre de usuario y la contraseña de la cuenta de correo electrónico que quiera configurar.

> [!primary]
>
> Esta guía es aplicable a las siguientes versiones de macOS: El Capitan, Sierra y High Sierra.
>

## Procedimiento

Existen dos maneras diferentes de añadir la cuenta de correo a Mail:

- **Utilizando nuestra herramienta Apple Devices**: Haga clic en el siguiente enlace y siga los pasos de configuración: <https://autodiscover.mail.ovh.net/AppleDevices/>.

- **Utilizando el asistente de configuración de la aplicación Mail**: Ejecute la aplicación Mail en su dispositivo.

Esta guía solo hace referencia a la configuración desde la aplicación Mail.

### 1. Añadir la cuenta

Una vez que ejecute la aplicación Mail en su dispositivo, puede añadir una cuenta de dos formas diferentes:

- **La primera vez que inicie la aplicación**, se abrirá una ventana donde deberá elegir el proveedor de su cuenta de correo. Seleccione `Otra cuenta de Mail`{.action} y haga clic en continuar. 

- **Si ya tiene alguna cuenta configurada**, haga clic en `Mail`{.action} en el menú superior y luego en `Añadir cuenta`{.action}. Seleccione `Otra cuenta de Mail`{.action} y haga clic en continuar. 

![Email Pro](images/configuration-mail-sierra-step1.png){.thumbnail}

Cumplimente la información de su cuenta:

|Campo|Descripción|  
|---|---|  
|Nombre|Introduzca el nombre que quiera que figure como remitente cuando envíe mensajes desde esa dirección.| 
|Correo electrónico|Introduzca la dirección de correo electrónico completa.| 
|Contraseña|Introduzca la contraseña de la dirección de correo electrónico.|  

A continuación, haga clic en el botón `Iniciar sesión`{.action}. Aparecerá un mensaje que le pedirá continuar y rellenar otros campos.

|Campo|Descripción|  
|---|---|  
|Tipo de cuenta|Deje IMAP seleccionado en el menú desplegable.| 
|Servidor de correo entrante|Introduzca el servidor **pro1.mail.ovh.net**.| 
|Servidor de correo saliente|Introduzca el servidor **pro1.mail.ovh.net**.|  

Haga de nuevo clic en `Iniciar sesión`{.action}. Si los datos introducidos son correctos, la aplicación se conectará a la cuenta.

![Email Pro](images/configuration-mail-sierra-step2.png){.thumbnail}

Al elegir las aplicaciones, asegúrese de dejar `Mail`{.action} marcado para que la aplicación pueda utilizar la cuenta, y haga clic en `Listo`{.action}.

Si lo desea, puede realizar una prueba de envío para comprobar que la cuenta esté correctamente configurada.

Si la aplicación le pide que introduzca de forma manual algunos datos en las preferencias de la cuenta, estos son los valores que debe utilizar para su cuenta Email Pro:

|Tipo de servidor|Nombre del servidor|SSL|Puerto|
|---|---|---|---|
|Entrante|pro1.mail.ovh.net|Sí|993|
|Saliente|pro1.mail.ovh.net|Sí|587|

### 2. Utilizar la dirección de correo electrónico

Una vez que haya configurado la dirección de correo electrónico, ya puede empezar a utilizarla enviando y recibiendo mensajes.

OVH ofrece una aplicación web que tiene [funciones colaborativas](https://www.ovh.es/emails/){.external} y está disponible en la dirección [https://pro1.mail.ovh.net](https://pro1.mail.ovh.net){.external}. Puede acceder con el nombre de usuario y la contraseña de su dirección de correo electrónico.  

## Más información

[Configurar una dirección de correo electrónico incluida con un plan de hosting o un MX Plan en Mail de macOS](https://docs.ovh.com/es/emails/correo_guia_de_configuracion_en_mail_de_mac_-_el_capitan/){.external}

[Configurar una cuenta Exchange en Mail de macOS](https://docs.ovh.com/es/microsoft-collaborative-solutions/configuracion-mail-macos/){.external}

Interactúe con nuestra comunidad de usuarios en [ovh.es/community](https://www.ovh.es/community/){.external}.