---
title: 'Configurar el firewall de red'
excerpt: 'Cómo configurar el Network Firewall'
updated: 2023-05-10
---

> [!primary]
> Esta traducción ha sido generada de forma automática por nuestro partner SYSTRAN. En algunos casos puede contener términos imprecisos, como en las etiquetas de los botones o los detalles técnicos. En caso de duda, le recomendamos que consulte la versión inglesa o francesa de la guía. Si quiere ayudarnos a mejorar esta traducción, por favor, utilice el botón «Contribuir» de esta página.
>

## Objetivo

Para proteger su infraestructura mundial y los servidores de sus clientes, OVHcloud ofrece un cortafuegos configurable integrado en su solución **anti-DDoS**: el Network Firewall. Se trata de una opción que permite limitar la exposición de los servicios a los ataques procedentes de la red pública.

**Esta guía explica cómo configurar el Network Firewall.**

> [!primary]
>
> Para más información sobre la solución anti-DDoS de OVHcloud, consulte la página <https://www.ovhcloud.com/es/security/anti-ddos/>.
> 

![El VAC en detalle](images/vac-inside.png){.thumbnail}

## Requisitos

- Tener contratado un servicio de OVHcloud que utilice el Network Firewall ([Servidores Dedicados](https://www.ovhcloud.com/es/bare-metal/){.external}, [VPS](https://www.ovhcloud.com/es/vps/){.external}, [instancias de Public Cloud](https://www.ovhcloud.com/es/public-cloud/){.external}, [Hosted Private Cloud](https://www.ovhcloud.com/es/enterprise/products/hosted-private-cloud/){.external}, [Additional IP](https://www.ovhcloud.com/en/bare-metal/ip/){.external}, etc.
- Estar conectado al [área de cliente de OVHcloud](https://ca.ovh.com/auth/?action=gotomanager&from=https://www.ovh.com/world/&ovhSubsidiary=ws){.external}, en la sección `Dedicado`{.action}.

> [!warning]
> Esta funcionalidad puede no estar disponible o estar limitada en los [servidores dedicados **Eco**](https://eco.ovhcloud.com/es/about/).
>
> Para más información, consulte nuestra [comparativa](https://eco.ovhcloud.com/es/compare/).

## Procedimiento

### Activar el Network Firewall

> [!primary]
>
> El Network Firewall protege la dirección IP asociada a un servidor. Por lo tanto, si tiene un servidor con varias direcciones IP, debe configurar cada IP de forma independiente. No es posible realizar la configuración global del servidor.
> 

Conéctese al área de cliente de OVHcloud, haga clic en el menú `Bare Metal Cloud`{.action} y abra la sección `IP`{.action}.<br>

Puede utilizar el menú desplegable "Mis direcciones IP públicas y servicios asociados" para filtrar sus servicios por categorías.

![filter service](images/selectservice.png){.thumbnail}

A continuación, haga clic en el botón `...`{.action} situado a la derecha de la IPv4 correspondiente y seleccione `Crear firewall`{.action}.

![Activación del firewall de red](images/firewallcreation2022.png){.thumbnail}

Confirme la operación haciendo clic en `Aceptar`{.action}.

![Confirmación](images/creationvalid_2020.png){.thumbnail}

Una vez creado el firewall, es necesario activarlo y configurarlo. Para ello, vuelva a hacer clic en el botón `···`{.action} situado al final de la línea correspondiente a la IPv4 y seleccione `Activar el firewall`{.action} (1). Repita el proceso y seleccione `Configurar el firewall`{.action} (2).

![Activación de la configuración](images/activationconfig.png){.thumbnail}

Es posible añadir hasta **20 reglas por IP**.

> [!warning]
>
> Si el Network firewall está configurado con reglas, estas reglas se aplican automáticamente a cada ataque DDoS. El firewall no puede desactivarse hasta que haya finalizado el ataque, por lo que es importante mantener las reglas de firewall actualizadas.
> Las IP de OVHcloud no tienen ninguna regla configurada por defecto, por lo que pueden establecerse todas las conexiones.
> No olvide comprobar regularmente sus reglas de firewall (si las tiene), aunque lo haya desactivado.
> 

> [!primary]
>
> - La fragmentación UDP está bloqueada (DROP) por defecto. Si utiliza una VPN, al activar el Network Firewall no olvide configurar correctamente su MTU (unidad de transmisión máxima). Por ejemplo, en OpenVPN, puede marcar `MTU test`{.action}.
> - El firewall de red no actúa dentro de la red de OVHcloud, por lo que las reglas creadas no afectan a las conexiones internas.
>

### Configurar el Network Firewall

> [!warning]
> Tenga en cuenta que el Network Firewall de OVHcloud no puede utilizarse para abrir puertos en un servidor. Para abrir puertos en un servidor, debe utilizar el cortafuegos del sistema operativo instalado en el servidor.<br>
> Para más información, consulte las siguientes guías: [Configurar el firewall de Windows](/pages/bare_metal_cloud/dedicated_servers/activate-port-firewall-soft-win) y [Configurar el firewall de Linux con iptables](/pages/bare_metal_cloud/dedicated_servers/firewall-Linux-iptable).
>

Para añadir una regla, haga clic en el botón `Añadir una regla`{.action}.

![Añadir una regla](images/addarule2022.png){.thumbnail}

Para cada regla es necesario seleccionar:

- la prioridad (de 0 a 19, siendo 0 la primera regla en aplicarse)
- una acción (`Denegar`{.action} o `Autorizar`{.action})
- el protocolo
- una IP de origen (opcional)
- el puerto de origen (TCP y UDP)
- el puerto de destino (TCP y UDP)
- las opciones TCP (solo TCP)

![Añadir una regla](images/ajoutregle4.png){.thumbnail}

> [!primary]
>
> - Prioridad 0: Se recomienda autorizar el protocolo TCP en todas las direcciones IP con la opción `ESTABLISHED`{.action}. Dicha opción permite comprobar que el paquete pertenece a una sesión abierta anteriormente (ya iniciada). Si no autoriza esta opción, el servidor no recibirá las respuestas para el protocolo TCP de las peticiones SYN/ACK.
> - Prioridad 19: Se recomienda bloquear todo el protocolo IPv4 si no se cumple ninguna de las reglas anteriores.
> 

### Ejemplo de configuración

Para dejar abiertos únicamente los puertos SSH (22), HTTP (80), HTTPS (443) y UDP (10000), autorizando el ICMP, utilice las reglas de la siguiente imagen:

![Ejemplo de configuración](images/exemple.png){.thumbnail}

Las reglas se ordenan cronológicamente de 0 (la primera regla leída) a 19 (la última regla leída). La cadena deja de recorrerse en el momento en el que pueda aplicarse una regla al paquete recibido.

Por ejemplo, para un paquete destinado al puerto 80/TCP, se aplicará la regla 2 y ya no se leerán las siguientes. Para un paquete destinado al puerto 25/TCP, no se aplicará ninguna regla hasta la última (la 19), que lo bloqueará, ya que las anteriores no autorizan ninguna comunicación en el puerto 25.

> [!warning]
> Como ya se ha indicado, la configuración anterior es solo un ejemplo y debe utilizarse como referencia si las reglas no se aplican a los servicios alojados en el servidor. Es absolutamente necesario configurar las reglas de su firewall en función de los servicios alojados en su servidor. Una mala configuración de sus reglas de firewall puede provocar el bloqueo del tráfico legítimo y la inaccesibilidad de los servicios del servidor.
>

### Mitigación

Nuestra solución anti-DDoS (VAC) incluye tres modos de mitigación: automática, permanente o forzada.

**Mitigación automática (detección permanente)**: por defecto, todas las IP de OVHcloud están sujetas a mitigación automática.  Con este modo, el tráfico pasa por el sistema de mitigación únicamente si se detecta que es "inusual" en relación con el tráfico normal recibido por el servidor.

**Mitigación permanente**: este modo puede activarse o desactivarse desde el área de cliente. Con la mitigación permanente (si está activada), aplica un primer nivel de filtrado constante a través de nuestro Shield hardware.<br>
Todo el tráfico pasa permanentemente por el sistema de mitigación antes de llegar al servidor. Recomendamos este modo para los servicios que sean objeto de ataques frecuentes.<br>
Tenga en cuenta que la mitigación permanente forma parte de nuestra solución anti-DDoS (VAC). Puede activarla en su IP sin activar el Network Firewall.

Para activarlo, haga clic en el menú `Bare Metal Cloud`{.action} y abra `IP`{.action}. A continuación, haga clic en los `...`{.action} a la derecha de la IPv4 correspondiente y seleccione `Mitigación: modo permanente`{.action}.

**Mitigación forzada**: este modo se activa automáticamente en cuanto se detecta un ataque en el servidor. Una vez activado en nuestra infraestructura anti-DDoS, este modo no puede desactivarse. Para proteger nuestra infraestructura, la protección se activará durante todo el ataque, hasta que sea totalmente mitigado.

> [!warning]
>
> Si nuestra solución anti-DDoS limita un ataque, las reglas configuradas de su Network Firewall se aplicarán finalmente, aunque haya desactivado el firewall. Si desea que no se aplique ninguna regla durante un ataque, debe eliminar toda regla previamente creada.
> 
> La mitigación está integrada en nuestra solución anti-DDoS (VAC), por lo que no puede desactivarse en un servicio. Todos los productos de OVHcloud se entregan con la protección anti-DDoS.

### Configurar el firewall de red Armor (Firewall Game)

> [!primary]
> Por defecto, el cortafuegos Armor está preconfigurado con algunas reglas que OVHcloud ha determinado que funcionan con los juegos más comunes. Sin embargo, para los clientes que dispongan de un servidor dedicado Game, le ofrecemos la posibilidad de ir más lejos y configurar también las reglas para los puertos.
>

Para configurar las reglas de sus puertos en Armor, debe conectarse primero al área de cliente de OVHcloud.<br>
A continuación, acceda al menú `Bare Metal Cloud`{.action} y abra la sección `IP`{.action}. Haga clic en `...`{.action} junto a la dirección IP del servidor de juego y, seguidamente, en `Configurar el firewall «Game»`{.action}".

![Game_wall](images/GAMEwall2021.png){.thumbnail}

En la siguiente pantalla, haga clic en el botón `Añadir una regla`{.action} para añadir una regla a Armor.

Es posible añadir hasta **20 reglas por IP**.

![Configure_Armor](images/ConfigureArmor2021.png){.thumbnail}

Active los puertos según sus necesidades en la siguiente pantalla y haga clic en el botón `Confirmar`{.action} cuando haya terminado de añadir las reglas. El firewall Armor se ha configurado correctamente.

## Más información

Interactúe con nuestra comunidad de usuarios en <https://community.ovh.com/en/>