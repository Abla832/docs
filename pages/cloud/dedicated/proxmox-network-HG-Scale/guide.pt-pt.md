---
title: 'Configurar a rede em Proxmox VE nas gamas High Grade & SCALE'
slug: proxmox-network-hg-scale
excerpt: 'Saiba como configurar a rede em Proxmox VE nas gamas High Grade & SCALE.'
section: 'Utilização avançada'
order: 5
---

> [!primary]
> Esta tradução foi automaticamente gerada pelo nosso parceiro SYSTRAN. Em certos casos, poderão ocorrer formulações imprecisas, como por exemplo nomes de botões ou detalhes técnicos. Recomendamos que consulte a versão inglesa ou francesa do manual, caso tenha alguma dúvida. Se nos quiser ajudar a melhorar esta tradução, clique em "Contribuir" nesta página.
>

**Última atualização: 04/10/2021**

## Objetivo

Nas gamas High Grade & SCALE, o funcionamento dos IP Failover em modo bridged (através de MAC virtuais) não é possível. Por isso, é necessário configurar os IP Failover em modo roteado ou através do vRack.

**Saiba como configurar a rede em Proxmox VE.**

## Requisitos

- Dispor de um [servidor dedicado OVHcloud](https://www.ovhcloud.com/pt/bare-metal/)
- Dispor de [IP Failover](https://www.ovhcloud.com/pt/bare-metal/ip/)
* Estar ligado à [Área de Cliente OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pt/&ovhSubsidiary=pt).

> [!warning]
>
> Nenhum MAC virtual deve ser aplicado aos IP Failover na Área de Cliente OVHcloud.
>

## Instruções

> [!primary]
>
> Nessas gamas de servidores, há 4 placas de rede. As duas primeiras para o público, as duas últimas para o privado. Para beneficiar do conjunto da largura de banda, devem ser criados agregados.
>

### IP Failover em modo roteado nas interfaces de rede públicas

#### Esquema da configuração alvo

![esquema rodoviário](images/schema_route2022.png){.thumbnail}

#### Explicações

É preciso:

* criar um agregado;
* criar bridge;
* autorizar o forwarding e adicionar as estradas.

#### Configurar o hypervisor

Tudo se passa no ficheiro `/etc/network/interfaces`:

```bash
vi /etc/network/interfaces
```

```bash
auto lo
iface lo inet loopback

# public interface 1
auto ens33f0
iface ens33f0 inet manual

# public interface 2
auto ens33f1
iface ens33f1 inet manual

# private interface 1
auto ens35f0
iface ens35f0 inet manual

# private interface 2
auto ens35f1
iface ens35f1 inet manual

auto bond0
# LACP aggregate on public interfaces
# configured in DHCP mode on this example
# Has the server's public IP
iface bond0 inet dhcp
	bond-slaves ens33f0 ens33f1
        bond-miimon 100
	bond-mode 802.3ad
        post-up echo 1 > /proc/sys/net/ipv4/conf/bond0/proxy_arp
        post-up echo 1 > /proc/sys/net/ipv4/ip_forward

#Private

auto vmbr0
# Configure the bridge with a private address and add route(s) to send the failover IPs to it
# A.B.C.D/X => Subnet of failover IPs assigned to the server, this can be a host with /32
iface vmbr0 inet static
	address 192.168.0.1
        netmask 255.255.255.255
	bridge-ports none
	bridge-stp off
	bridge-fd 0
        post-up ip route add A.B.C.D/X dev vmbr0
```

Agora, execute os serviços de rede ou reinicie o servidor.

#### Exemplo de configuração VM cliente Debian

Conteúdo do ficheiro `/etc/network/interfaces`:

```bash
auto lo ens18
iface lo inet loopback
iface ens18 inet static
    address IP_FO
    netmask 255.255.255.255
    gateway 192.168.0.1
```

### IP Failover através do vRack

#### Requisitos

* Ter reservado um bloco público de endereços IP na sua conta, com um mínimo de quatro endereços.
* Ter acesso ao intervalo de endereços de IP privados escolhidos.
* Dispor de um [servidor compatível com o vRack](https://www.ovhcloud.com/pt/bare-metal/){.external}.
* Ter ativado um serviço [vRack](https://www.ovh.pt/solucoes/vrack/){.external}.
* Ter acesso à [Área de Cliente OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pt/&ovhSubsidiary=pt).

#### Esquema da configuração alvo

![schema vrack](images/schema_vrack2022.png){.thumbnail}

#### Explicações

Tem de:

* criar um agregado;
* criar um bridge ligado ao agregado;

#### Configurar um endereço IP utilizável

No caso do vRack, o primeiro, o penúltimo e o último endereço de um determinado bloco de IP são sempre reservados, respetivamente, ao endereço de rede, ao gateway de rede e ao *broadcast* da rede. Isto significa que o primeiro endereço utilizável é o segundo endereço do bloco, como indicado a seguir:

```sh
46.105.135.96 # Reserved: network address
46.105.135.97 # First usable IP
46.105.135.98
46.105.135.99
46.105.135.100
46.105.135.101
46.105.135.102
46.105.135.103
46.105.135.104
46.105.135.105
46.105.135.106
46.105.135.107
46.105.135.108
46.105.135.109 # Last usable IP
46.105.135.110 # Reserved: network gateway
46.105.135.111 # Reserved: network broadcast
```

Para configurar o primeiro endereço IP utilizável, é preciso editar o ficheiro de configuração de rede, como indicado abaixo. Neste exemplo, utilize uma máscara de sub-rede **255.255.255.240**.

> [!primary]
>
> A máscara de sub-rede utilizada neste exemplo adequa-se ao nosso bloco de endereços IP. A sua máscara de sub-rede pode diferir em função da dimensão do bloco. Quando comprar o seu bloco de endereços IP, receberá um e-mail com a máscara de sub-rede que deve utilizar.
>

#### Configurar o hypervisor

Tudo se passa no ficheiro `/etc/network/interfaces`:

```bash
vi /etc/network/interfaces
```

O que conta aqui é a configuração `bond1` e `vmbr1`:

```bash
auto lo
iface lo inet loopback

# public interface 1
auto ens33f0
iface ens33f0 inet manual

# public interface 2
auto ens33f1
iface ens33f1 inet manual

# private interface 1
auto ens35f0
iface ens35f0 inet manual

# private interface 2
auto ens35f1
iface ens35f1 inet manual

auto bond0
iface bond0 inet dhcp
	bond-slaves ens33f0 ens33f1
        bond-miimon 100
	bond-mode 802.3ad
        post-up echo 1 > /proc/sys/net/ipv4/conf/bond0/proxy_arp
        post-up echo 1 > /proc/sys/net/ipv4/ip_forward

auto bond1
# LACP Aggregate on private interfaces
# No IPs on it
iface bond1 inet manual
	bond-slaves ens35f0 ens35f1
        bond-miimon 100
	bond-mode 802.3ad


#Private

auto vmbr1
# Bridge connected to bond1 aggregate
# No need for IP
iface vmbr1 inet manual
	bridge-ports bond1
	bridge-stp off
	bridge-fd 0

```

Agora, execute os serviços de rede ou reinicie o servidor.

#### Exemplo de configuração VM cliente Debian

Conteúdo do ficheiro `/etc/network/interfaces`:

```bash
auto lo ens18
iface lo inet loopback
iface ens18 inet static
    address 46.105.135.97
    netmask 255.255.255.240
    gateway 46.105.135.110
```

## Quer saber mais?

Junte-se à nossa comunidade de utilizadores em <https://community.ovh.com/en/>.
