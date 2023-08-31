---
title: 'Proteger su cuenta de OVHcloud con la doble autenticación'
excerpt: 'Cómo mejorar la seguridad de su cuenta de OVHcloud activando la doble autenticación'
updated: 2022-07-20
---

> [!primary]
> Esta traducción ha sido generada de forma automática por nuestro partner SYSTRAN. En algunos casos puede contener términos imprecisos, como en las etiquetas de los botones o los detalles técnicos. En caso de duda, le recomendamos que consulte la versión inglesa o francesa de la guía. Si quiere ayudarnos a mejorar esta traducción, por favor, utilice el botón «Contribuir» de esta página.
>

## Objetivo

OVHcloud pone a su disposición herramientas para reforzar la seguridad de su cuenta y de sus servicios.
Puede activar la autentificación de dos factores (2FA). Esta se agrega a su nombre de usuario y contraseña, y se gestiona desde uno de sus dispositivos, ya sea un teléfono, una tableta o una llave de seguridad.  

**Cuáles son los diferentes métodos propuestos y cómo activarlos**

## Requisitos

- Haber iniciado sesión en el [área de cliente de OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.es/&ovhSubsidiary=es).
- Disponer de un móvil (para el método por SMS), un teléfono inteligente o una tableta (para el método a través de la aplicación móvil) o una llave de seguridad U2F (Universal Second Factor).
- Haber consultado las [recomendaciones sobre la gestión de la contraseña de acceso a su cuenta](/pages/account_and_service_management/account_information/manage-ovh-password).

## Procedimiento

Tiene la posibilidad de activar uno o varios métodos de doble autenticación con el fin de proteger y controlar el acceso a su área de cliente.
Le proponemos tres métodos diferentes:

- **Mediante SMS**. Introduzca su número de teléfono móvil. Se le enviará por SMS un código de uso único cada vez que intente conectarse a su cuenta de OVHcloud. La principal ventaja de este método es que utiliza un código que se envía a un dispositivo distinto a su ordenador. En caso de sufrir una intrusión, por ejemplo, de un programa maligno, su cuenta permanecerá protegida. Sin embargo, debe tener suficiente cobertura de red para recibir los SMS.

- **Mediante una aplicación móvil de OTP**. Instale una aplicación móvil de OTP en su teléfono inteligente o tableta con sistema operativo Android o iOS. Luego, asocie la aplicación a su cuenta de OVHcloud. En cada intento de conexión, la aplicación generará un código de uso único válido durante un corto tiempo.
Tras asociar por primera vez la aplicación a su cuenta, ya no será necesario que su dispositivo esté conectado a internet para que se generen los códigos.

- **Mediante una llave de seguridad U2F**. Para aplicar este método, es necesario conectar una memoria USB de seguridad U2F a su ordenador cada vez que inicie sesión en su cuenta de OVHcloud. Entonces la autenticación se realiza automáticamente. Este método ofrece un nivel de seguridad más alto, pues se basa en un dispositivo de seguridad independiente; totalmente aparte de su ordenador, teléfono inteligente o tableta, y que está menos expuesto a los riesgos de pirateo.

### Etapa 1: activar su primer método de doble autenticación

- [Activar el método de doble autenticación por SMS](/pages/account_and_service_management/account_information/enable-2fa-with-sms).
- [Activar el método de doble autenticación por aplicación móvil](/pages/account_and_service_management/account_information/enable-2fa-with-mobile-app).
- [Activar el método de doble autenticación por llave de seguridad](/pages/account_and_service_management/account_information/enable-2fa-with-security-key).

Tras añadir el primer método, puede agregar uno o dos más a fin de disponer de múltiples medios para iniciar sesión en su cuenta.

### Etapa 2: guardar los códigos de seguridad

Cuando añade una doble autenticación por primera vez, se le comunicarán los códigos de seguridad. Guárdelos cuidadosamente. En consecuencia, le aconsejamos guardarlos en un gestor de contraseñas.

![2FA](images/2facodes.png){.thumbnail}

Podrá eliminarlos o regenerarlos en su área de cliente:

![2FA](images/2facodesaction.png){.thumbnail}

> [!warning]
>
> Le recordamos que es indispensable guardar estos códigos de seguridad y asegurarse de que sean válidos. En caso de indisponibilidad de su/s método/s de seguridad seleccionado/s (debido al robo o pérdida de su teléfono o de su llave de seguridad), el acceso a su área de cliente podría quedar bloqueado.
>

### Etapa 3: iniciar sesión en el área de cliente con la doble autenticación

Tras activar la doble autenticación, la pantalla de identificación le mostrará el método de seguridad seleccionado. Si desea utilizar otro, haga clic en el botón `«Intentarlo con otro método»`{.action}.

![2FA](images/2fasmsloginedit.png){.thumbnail}

Entonces aparecerán todos los métodos que activó:

![2FA](images/2faloginchoice.png){.thumbnail}

### ¿Qué se debe hacer en caso de pérdida o avería de uno de los dispositivos?

Si perdió su dispositivo (teléfono inteligente, tableta o llave de seguridad) o este dejó de funcionar, le aconsejamos que utilice los otros métodos de doble autenticación activos en su cuenta.

También puede utilizar uno de los códigos de seguridad que tiene a su disposición. 

### Eliminar un dispositivo asociado a la doble autenticación <a name="delete-device"></a>

> [!warning]
>
> Aunque se elimine un dispositivo, la doble autenticación sigue activa. 
> 
> Antes de eliminar un dispositivo y para evitar que se bloquee el acceso a su cuenta, compruebe que dispone de alguna de las siguientes opciones:
> 
> - Un dispositivo operativo
> - Otro método de doble autenticación operativo 
> - Códigos de seguridad válidos.
> 

Si desea eliminar un dispositivo, inicie sesión en su [área de cliente de OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.es/&ovhSubsidiary=es){.external}. Haga clic en su nombre en la esquina superior derecha (primer paso en la siguiente imagen) y, seguidamente, en sus iniciales (segundo paso). 

![2FA](images/hub2FAb.png){.thumbnail}

Haga clic en `«Seguridad»`{.action} (primer paso en la siguiente imagen) y, seguidamente, en el icono de 3 puntos `«...»`{.action} (segundo paso) a la derecha del dispositivo que va a eliminar. Por último, haga clic en `«Eliminar»`{.action} (tercer paso).

![2FA](images/hub2FAc.png){.thumbnail}

Recibirá un último código de verificación en el dispositivo que quiera eliminar. Introduzca el código en la ventana que se abre y haga clic en `Aceptar`{.action} para finalizar la eliminación.

> [!warning]
>
> Si ya no tiene acceso al dispositivo que desea eliminar, no podrá eliminarlo usted mismo desde el área de cliente de OVHcloud.
>
> En ese caso, **contacte directamente** con nuestro equipo de soporte siguiendo el proceso descrito [aquí](#2FA-deletion).
>

### Desactivar la doble autenticación por completo <a name="disable-2fa"></a>

#### Si tiene acceso al área de cliente de OVHcloud

Para desactivar por completo la doble autenticación en su cuenta de OVHcloud, es necesario eliminar **todos** los periféricos indicados **y también desactivar los códigos de seguridad**.

Para eliminar cada dispositivo, consulte la [sección dedicada de esta guía](#delete-device).

Una vez que haya eliminado todos los dispositivos, desactive los códigos de seguridad haciendo clic en el botón `Desactivar los códigos 2FA`{.action}.

![2FA codes](images/disabling-codes.png){.thumbnail}

#### Si no tiene acceso al área de cliente de OVHcloud <a name="2FA-deletion"></a>

Si ya no dispone de dispositivos válidos y no dispone de códigos de seguridad válidos, puede solicitar la desactivación de la doble autenticación contactando con nuestro equipo de soporte.

Antes de contactarnos, debe reunir los siguientes justificantes:

|Tipo de cuenta OVHcloud|Justificantes a adjuntar|
|---|---|
|Particular|- Documento de identidad (DNI, permiso de conducir o pasaporte), que menciona el nombre completo, la fecha de nacimiento y la fecha de expiración, a nombre del titular de la cuenta de OVHcloud. <br><br>- Justificante de domicilio correspondiente al registrado en la cuenta OVHcloud, de menos de dos meses.<br>**Si, después de un traslado, no ha actualizado su dirección en su área de cliente de OVHcloud, deberá proporcionar :**<br>- Un justificante de domicilio en la antigua dirección <br>- Un justificante de domicilio en la nueva dirección, de menos de dos meses.<br> Si vive ahora en un tercero, deberá proporcionar:<br>- Un justificante de domicilio a nombre de la persona que le aloje, de menos de dos meses<br>- Un certificado de alojamiento firmado por la persona que le aloje|
|Empresa|- Documento de identidad (DNI, permiso de conducir o pasaporte) que mencione el nombre completo, la fecha de nacimiento y la fecha de expiración al nombre de una persona autorizada para representar a la empresa.<br><br>- Documento de registro de la empresa que indica la persona autorizada para representar la empresa.|

Una vez que haya reunido los documentos justificativos, póngase en contacto con nuestro equipo de soporte, llamando al 91 758 34 77.

> [!warning]
>
> Los justificantes deberán enviarnos desde una dirección de correo electrónico registrada en su cuenta de OVHcloud.

Tras comprobar sus documentos, un asesor podrá desactivar manualmente la doble autenticación en su cuenta de OVHcloud.

## Más información

Para servicios especializados (posicionamiento, desarrollo, etc.), contacte con [partners de OVHcloud](https://partner.ovhcloud.com/es-es/directory/).

Si quiere disfrutar de ayuda para utilizar y configurar sus soluciones de OVHcloud, puede consultar nuestras distintas soluciones [pestañas de soporte](https://www.ovhcloud.com/es-es/support-levels/).

Interactúe con nuestra comunidad de usuarios en <https://community.ovh.com/en/>.