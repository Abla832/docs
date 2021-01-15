---
title: Autorizar direcciones IP a conectarse al vCenter
slug: autorizar-direcciones-ip-a-conectarse-al-vcenter
legacy_guide_number: '1442255'
space_key: VS
space_name: vSphere as a Service
section: Funcionalidades de OVHcloud
---

**Última actualización: 25/06/2020**

## Objetivo

Es posible limitar el acceso al vCenter autorizando solo la conexión de determinadas direcciones IP. 

**Esta guía explica cómo autorizar direcciones IP a conectarse al vCenter.**

## Requisitos

* Haber iniciado sesión en el [área de cliente de OVHcloud](https://www.ovh.com/auth/?action=gotomanager){.external}.
* Disponer de una [infraestructura Private Cloud](https://www.ovhcloud.com/es-es/enterprise/products/hosted-private-cloud/){.external} en su cuenta de OVHcloud.

## Procedimiento

Cuando [la política de acceso al vCenter está restringida](../modificar-politica-acceso-al-vcenter/), es necesario añadir las direcciones IP autorizadas a conectarse al servicio.

Esta operación se realiza desde el [área de cliente de OVHcloud](https://www.ovh.com/auth/?action=gotomanager){.external-link}. En el menú `Servidores`, acceda a la sección `Private Cloud`. Seleccione la infraestructura y, a continuación, abra la pestaña `Seguridad`. Por último, haga clic en `Añadir un nuevo rango de direcciones IP`{.action}.

![vCenter](images/restrictIP.JPG){.thumbnail}

Añada la dirección IP y, si lo desea, una descripción para poder identificarla fácilmente.

Por último, haga clic en `Siguiente`{.action} y, una vez que la IP esté marcada como autorizada e instalada, podrá conectarse al vSphere desde esa dirección IP.

![vCenter](images/restrictIP2.JPG){.thumbnail}

## Más información

Interactúe con nuestra comunidad de usuarios en <https://community.ovh.com/en/>.
