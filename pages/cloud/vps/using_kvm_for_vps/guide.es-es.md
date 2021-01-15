---
title: Utilizar el KVM en un VPS
excerpt: Cómo acceder a su VPS con la funcionalidad KVM
slug: utilizar_el_kvm_para_los_vps
section: Primeros pasos
---

**Última actualización: 7 de septiembre de 2020**

## Objetivo

La consola KVM permite establecer una conexión directa con un VPS sin necesidad de utilizar software externo (terminal o Putty, por ejemplo). Puede acceder a esta consola desde el área de cliente de OVHcloud o a las API de OVHcloud.  

**Esta guía explica los dos métodos de acceso al KVM.**

## Requisitos

- Un [VPS](https://www.ovhcloud.com/es-es/vps/) en su cuenta de OVHcloud.
- Estar conectado al [área de cliente de OVHcloud](https://www.ovh.com/auth/?action=gotomanager).

## Procedimiento

### Conexión al KVM desde el área de cliente de OVHcloud

#### Gama VPS actual

Conéctese al área [de cliente de OVHcloud](https://www.ovh.com/auth/?action=gotomanager), acceda a la sección `Bare Metal Cloud`{.action} y seleccione el servidor en el menú izquierdo del `VPS`{.action}. En esta sección, haga clic en `...`{.action} a la derecha del nombre de su VPS en la zona "Su VPS".

![Abrir KVM](images/kvm-new1.png){.thumbnail}

#### Antigua gama de VPS

Conéctese al área [de cliente de OVHcloud](https://www.ovh.com/auth/?action=gotomanager), acceda a la sección `Bare Metal Cloud`{.action} y seleccione el servidor en el menú izquierdo del `VPS`{.action}. En esta sección, haga clic en el acceso rápido titulado `KVM`{.action}.

![Haga clic en el botón KVM](images/kvm-new2.png){.thumbnail}

### Uso de la consola KVM

Se abre la pantalla KVM. Se trata de una pequeña ventana que indica la conexión al servidor. Dado que la ventana es bastante pequeña, puede ser muy difícil navegar por la interfaz del servidor utilizando las barras de desplazamiento. Por lo tanto, le recomendamos que abra el KVM en una nueva ventana de pantalla completa utilizando el botón "Abrir en una nueva ventana" situado en el ángulo inferior derecho de la ventana emergente.

> [!primary]
>
> Si experimenta problemas de doble entrada, puede deberse a la configuración automática de la pantalla. Le recomendamos que abra el KVM en una nueva ventana haciendo clic en el botón "Abrir en una nueva ventana".
>
> Si todavía tiene problemas con la pantalla, le recomendamos que elimine de la URL la parte "auto". Si la URL es https://compute.sbg1.cloud.ovh.net:6080/vnc_auto.html?token=xxxxxxxxxxxx, debe ser https://compute.sbg1.cloud.ovh.net:6080/vnc.html?token=xxxxxxxxxxxx (el enlace para usted puede ser diferente, el ejemplo dado sólo muestra la parte de la URL a borrar)
>

![Conexión al KVM](images/kvm_screen.png){.thumbnail}

> [!primary]
>
> El teclado puede tener una disposición diferente a la suya. Asegúrese de comprobarlo, ya que el teclado puede ser AZERTY en lugar de QWERTY, por ejemplo.
>

### Conexión al KVM a través de la API

Puede ocurrir que experimente problemas de conexión al KVM a través del panel de configuración de OVHcloud, especialmente con las versiones anteriores. En este caso, puede utilizar la solución API. Para ello, conéctese a través de la API de [OVHcloud](https://api.ovh.com/).

#### VPS 2014

Si tiene un VPS 2014, puede ver un *error 1006*. Revisar la API con la siguiente llamada podría resolver este problema.

> [!api]
>
> @api {POST} /vps/{serviceName}/openConsoleAccess
>
> Parámetros de llamadas a la API:
>
>> serviceName \*
>>> ID de su VPS similar a vpsxxxx.ovh.net
>> protocolo
>>> VNC

Aunque la respuesta de la API sea positiva, puede que la conexión tarde un par de minutos en establecerse, hasta que el puerto esté abierto.

Le recomendamos utilizar uno de los siguientes clientes:

- [UltraVnc](https://www.uvnc.com/downloads/ultravnc.html){.external}
- [VNC Viewer](https://www.realvnc.com/en/connect/download/viewer/){.external}

Utilice los detalles proporcionados por la llamada a la API para conectarse a distancia al VPS con ayuda de uno de los clientes de software antes mencionados.

#### VPS 2016

Si tiene problemas con el KVM, le recomendamos la siguiente llamada a la API:

> [!api]
>
> @api {POST} /vps/{serviceName}/getConsoleUrl
>
> Parámetros de llamadas a la API:
>
>> serviceName \*
>>> ID de su VPS similar a vpsxxxx.ovh.net
>

> [!primary]
>
> Si todavía tiene problemas con la pantalla, le recomendamos que elimine de la URL la parte "auto". Si la URL es (el enlace para usted puede ser diferente, este ejemplo sólo muestra la parte de la URL a borrar) https://compute.sbg1.cloud.ovh.net:6080/vnc_auto.html?token=xxxxxxxxxxxx entonces debe ser https://compute.sbg1.cloud.ovh.net:6080/vnc.html?token=xxxxxxxxxxxx.
>

## Más información

Interactúe con nuestra comunidad de usuarios en <https://community.ovh.com>.

