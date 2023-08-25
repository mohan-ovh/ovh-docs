---
title: Capacidad técnica
excerpt: 'Encuentre las capacidades y limitaciones técnicas de las soluciones Hosted Private Cloud que ofrece OVHcloud'
updated: 2023-03-23
---

> [!primary]
> Esta traducción ha sido generada de forma automática por nuestro partner SYSTRAN. En algunos casos puede contener términos imprecisos, como en las etiquetas de los botones o los detalles técnicos. En caso de duda, le recomendamos que consulte la versión inglesa o francesa de la guía. Si quiere ayudarnos a mejorar esta traducción, por favor, utilice el botón «Contribuir» de esta página.
>


## Objetivo

**Esta página ofrece una visión general de las funcionalidades y limitaciones técnicas de los servicios Hosted Private Cloud de OVHcloud.**

## Capacidades y limitaciones conocidas

| Elemento | Descripción | Valor |
|:-----:|:-----:|:----------:|
| Número máx. PCC por ID de cliente | Número de vCenter o packs por organización | Sin límite |
| Número de PCC asociados | Conexión de vCenters (Enhanced Link Mode) | 0 (no autorizado) |
| Número mín. de datastores por PCC (SLA) | Número de datastores por vCenter para el mantenimiento del contrato de nivel de servicio | 2 |
| Número mín. de hosts por PCC (SLA) | Número de hosts por vCenter para el mantenimiento del contrato de nivel de servicio | 2 |
| Número mín. de hosts por PCC (sin SLA) | Número mínimo de hosts que se deben utilizar con vCenter sin contrato de nivel de servicio | 0 |
| Número máx. de hosts por cluster | Hosts por cluster | 64 |
| Número máx. de clusters por vDC | Número de clusters en el mismo datacenter virtual | Sin límite |
| Número máx. de vDC por PCC | Número de datacenters virtuales (vDC) que los clientes pueden añadir por vCenter | 400 |
| Número máx. de hosts por PCC | Límites de hosts por vCenter | 231 |
| Número máx. de datastores por PCC | Límites de datastores por vCenter | 110 |
| Número máx. máquinas virtuales por SDDC | MV gestionadas por el mismo vCenter | 25 000 |
| Número máx. máquinas virtuales por host | MV alojadas en el mismo host físico | 1024 |
| Número máx. de direcciones IP por PCC | Número máx. direcciones IP públicas que puedan asignarse y utilizarse por vCenter | 1 x /23 |
| vCPU, memoria RAM y disco utilizados por vCenter standard | Recursos asignados a vCenter (VCSA) | 4 procesadores virtuales, 16 GB de RAM, 290 GB de espacio en disco |
| vCPU, memoria RAM y disco utilizados por NSX Standard | Recursos asignados al Manager y al Controller NSX | 4 CPU virtuales, 4 GB de RAM, 60 GB de espacio en disco<br>4 CPU virtuales, 2 GB de RAM, 28 GB de espacio en disco |
| vCPU, memoria RAM y disco utilizados por vROPS | Recursos asignados a vROPS | 4 procesadores virtuales, 16 GB de RAM |
| Número máx. de edge nodes | Número máx. de dispositivos edge a desplegar por NSX | 2000 |
| Número máx. túneles VPN IPSec | Número máx. túneles VPN por extensión | 512 compact edge<br>1600 large de edge<br>4096 quad large edge<br>6000 extra large edge |
| Número máx. de vRack por vDC | Número máx. redes privadas por Virtual Data Center (VDC) | 1 |
| Número máx. de clientes VPN L2 | Número de clientes VPN a conectar | 5 |
| Número máx. de direcciones IP autorizadas | Número de direcciones IP autorizadas a conectarse a la infraestructura VMware | 2048 |

## Más información

Únase a nuestra comunidad de usuarios en <https://community.ovh.com/en/>.
