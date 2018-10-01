---
title: 'Transferir un dominio a OVH'
slug: transferir-un-dominio-generico
excerpt: 'Cómo realizar la transferencia de un dominio a OVH'
section: 'Operaciones en los dominios'
order: 1
---

**Última actualización: 18/09/2018**

## Objetivo

La transferencia de un dominio permite cambiar el agente registrador que lo gestiona. Esta operación suele tardar entre uno y diez días.

**Esta guía explica cómo transferir un dominio a OVH.**

## Requisitos

- Tener un dominio registrado con otro agente registrador.
- Estar facultado para solicitar la transferencia del dominio. El propietario y las personas que lo administren deben haber sido informados.
- El solicitante debe poseer el código de transferencia o tener la posibilidad de obtenerlo.
- El dominio debe haber sido creado más de 60 días antes.
- El dominio no debe haber sido transferido o haber cambiado de propietario en los últimos 60 días.
- El dominio debe estar desbloqueado.

## Procedimiento

Si tiene un dominio registrado con otro proveedor y quiere cambiar de agente registrador, puede transferirlo a OVH.

La operación de transferencia se desarrolla en varias etapas e involucra a varias entidades: su actual agente registrador, OVH y otras partes. A continuación se resumen las etapas de una transferencia.

|Etapa|Descripción|Quién realiza la acción|Dónde|Plazo|
|---|---|---|---|---|
|1|Comprobar la información relativa al dominio|El administrador del dominio|En el actual agente registrador| - |
|2|Desbloquear el dominio y obtener el código de transferencia|El administrador del dominio, con el consentimiento del propietario|En el actual agente registrador| - |
|3|Solicitar la transferencia del dominio|Cualquiera que disponga del código de transferencia, con el consentimiento del propietario|En el nuevo agente registrador (OVH en este caso)| - |
|4|Realizar la primera fase de verificación|El propietario del dominio y el administrador que figuran en el nuevo agente registrador|Por correo electrónico|Máximo 5 días|
|5|Realizar la segunda fase de verificación|El actual agente registrador|A través de una solicitud enviada por la entidad que gestiona la extensión del dominio|Máximo 5 días|

> [!warning]
>
> Este procedimiento se aplica a la mayoría de las transferencias. Sin embargo, según la extensión del dominio, es posible que varíe. Puede consultar la información del dominio en cuestión en la página <https://www.ovh.es/dominios/precios/>.
>

### 1. Comprobar la información relativa al dominio

**En primer lugar, es importante comprobar que la información relativa al dominio esté actualizada.** Tras la entrada en aplicación del **RGPD**, son pocos los datos visibles en el **Whois**. Por lo tanto, le recomendamos que consulte la información relativa al dominio en su agente registrador actual.

- **Si los datos con correctos**, vaya al siguiente paso.
- **Si los datos son incorrectos o no son visibles**, contacte con su actual agente registrador para comprobarlos y/o corregirlos.

> [!primary]
>
> Si no sabe o no recuerda cuál es su actual agente registrador, las líneas **Registrar** que aparecen en el resultado de la herramienta [Whois](https://www.ovh.es/soporte/herramientas/check_whois.pl){.external} pueden darle una orientación sobre su identidad.
>

### 2. Desbloquear el dominio y obtener el código de transferencia

Una vez que haya comprobado la información, es necesario desbloquear el dominio. Esta operación solo puede realizarse en el actual agente registrador. Por lo tanto, le invitamos a que se ponga en contacto con él para conocer el procedimiento que este haya establecido.

Una vez desbloqueado el dominio, el agente registrador deberá comunicarle un código de transferencia. Este código puede llamarse de distintas formas: código de transferencia, Auth-Code, Auth-Info, código EPP...

Tenga en cuenta que OVH no es el actual agente registrador del dominio, por lo que no podemos desbloquearlo ni proporcionarle el código de transferencia.

> [!warning]
>
> Una vez desbloqueado el dominio, dispone de 7 días para solicitar su transferencia a OVH. Pasado ese plazo, el dominio volverá a bloquearse si no se ha realizado ninguna solicitud de cambio de agente registrador.
>

### 3. Solicitar la transferencia del dominio a OVH

Una vez desbloqueado el dominio, y con el código de transferencia en su poder, puede solicitar la transferencia a OVH. Para ello, realice un pedido de transferencia desde [nuestra web](https://www.ovh.es/){.external}. Introduzca el nombre de dominio y continúe con el pedido.

Cuando se le pida el código de transferencia, introdúzcalo en el campo situado junto al dominio. Si todavía no tiene el código de transferencia, puede marcar la casilla `Indicar el código de autenticación posteriormente`{.action}. Le recomendamos que se asegure previamente de que podrá obtener el código antes de continuar.

Si lo desea, puede completar el dominio con un [plan de hosting](https://www.ovh.es/hosting/){.external} u otras soluciones de OVH. Estas opciones pueden ser interesantes si la transferencia del dominio se inscribe en un proyecto más amplio de migración de sus servicios. En ese caso, la guía [Migrar un sitio web y el correo a OVH](https://docs.ovh.com/es/hosting/web_hosting_transferir_un_sitio_web_y_el_correo_sin_cortes_del_servicio/){.external} explica en detalle cómo hacerlo.

> [!warning]
>
> Preste especial atención a los siguientes elementos durante el pedido:
>
> - **Los datos del propietario del dominio**: Con la entrada en aplicación del RGPD, asegúrese de que la información del propietario introducida es la misma que la registrada en el actual agente registrador para evitar cualquier sospecha de robo de dominio.
> - **Los servidores DNS del dominio**: Si el dominio es utilizado por un sitio web o el correo, introduzca los servidores DNS que estén configurados actualmente para evitar una interrupción del servicio.  
>

Una vez generada la orden de pedido, deberá abonarla para que comience la transferencia. El procedimiento de transferencia se iniciará cuando se reciba el pago. Puede consultar el progreso desde el [área de cliente de OVH](https://www.ovh.com/auth/?action=gotomanager){.external}, seleccionando `Dominios`{.action} en la columna izquierda y haciendo clic en `Operaciones en curso`{.action}.

### 4. Realizar la primera fase de verificación

Una vez iniciada la transferencia, se realizarán dos fases de verificación. La primera puede durar hasta 5 días y comienza en el momento en que se inicia la transferencia, con el envío de dos solicitudes de verificación. 

|Quién recibe la solicitud de verificación|A dónde se envía la solicitud de verificación|
|---|---|
|El propietario del dominio|A la dirección de correo electrónico del propietario que figure en el **Whois**, si esta es visible; si no lo es, a la dirección de correo electrónico del propietario indicada al realizar el pedido en OVH|
|El administrador indicado al realizar el pedido en OVH|A la dirección de correo electrónico que figura en el perfil del administrador en OVH|

La confirmación se realiza desde una interfaz de OVH. Los mensajes enviados por correo electrónico contienen un enlace a dicha interfaz. 

![Dominio](images/domaintransfer_gTLD_validation.png){.thumbnail}

A continuación, pueden darse varias situaciones.

|Escenarios posibles|Consecuencias|
|---|---|
|El propietario y el administrador confirman la solicitud|La transferencia pasa a la segunda fase de verificación en un plazo de 24 horas|
|Uno de los dos contactos confirma la solicitud y el otro la deja sin responder|La transferencia pasa a la segunda fase de verificación al cabo de 5 días|
|Ninguno de los dos contactos responde a la solicitud|La transferencia pasa a la segunda fase de verificación al cabo de 5 días|
|Uno de los dos contactos rechaza la solicitud|La transferencia se abandona una vez notificado el rechazo por uno cualquiera de los dos contactos|

En caso de que la transferencia haya sido abandonada, asegúrese de que las distintas partes implicadas estén de acuerdo con la misma y de que sus direcciones de correo electrónico estén actualizadas. El proceso podrá reanudarse más adelante desde el [área de cliente de OVH](https://www.ovh.com/auth/?action=gotomanager){.external}, seleccionando `Dominios`{.action} en la columna izquierda y haciendo clic en `Operaciones en curso`{.action}.

### 5. Realizar la segunda fase de verificación

En la segunda fase, el actual agente registrador (que todavía no es OVH) recibirá una solicitud de validación. Aquí pueden darse varias situaciones.

|Escenarios posibles|Consecuencias|
|---|---|
|El actual agente registrador valida la transferencia|La transferencia se realiza en un plazo de 24 horas|
|El actual agente registrador no responde a la solicitud|La transferencia se realiza al cabo de 5 días|
|El actual agente registrador rechaza la solicitud|La transferencia se abandona una vez notificado el rechazo por el agente registrador|

En caso de que el actual agente registrador rechace la transferencia, le invitamos a que contacte con él para conocer el motivo. El proceso podrá reanudarse más adelante desde el [área de cliente de OVH](https://www.ovh.com/auth/?action=gotomanager){.external}, seleccionando `Dominios`{.action} en la columna izquierda y haciendo clic en `Operaciones en curso`{.action}.

### 6. Gestionar el dominio en OVH

Una vez finalizado el procedimiento de transferencia, podrá administrar el dominio desde el [área de cliente de OVH](https://www.ovh.com/auth/?action=gotomanager){.external}.

Para ello, haga clic en `Dominios`{.action} en la columna izquierda y seleccione el dominio.

## Más información

[Migrar un sitio web y el correo a OVH](https://docs.ovh.com/es/hosting/web_hosting_transferir_un_sitio_web_y_el_correo_sin_cortes_del_servicio/){.external}

Interactúe con nuestra comunidad de usuarios en [ovh.es/community](https://www.ovh.es/community/){.external}.