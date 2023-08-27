---
title: Como configurar um IP alias
excerpt: Descubra como adicionar endereços Additional IP à configuração de rede
updated: 2023-06-15
---

> [!primary]
> Esta tradução foi automaticamente gerada pelo nosso parceiro SYSTRAN. Em certos casos, poderão ocorrer formulações imprecisas, como por exemplo nomes de botões ou detalhes técnicos. Recomendamos que consulte a versão inglesa ou francesa do manual, caso tenha alguma dúvida. Se nos quiser ajudar a melhorar esta tradução, clique em "Contribuir" nesta página.
>

> [!primary]
>
> A partir de 6 de outubro de 2022, a nossa solução "Failover IP" passou a designar-se [Additional IP](https://www.ovhcloud.com/pt/network/additional-ip/). Isto não afeta as suas funcionalidades.
>

## Objetivo

O IP aliasing é uma configuração de rede para servidores dedicados que permite associar vários endereços IP à mesma interface de rede.

**Este guia explica como realizar o IP aliasing**

## Requisitos

- Ter um servidor dedicado ([VPS](https://www.ovh.pt/vps/){.external}, [servidor dedicado](https://www.ovh.pt/servidores_dedicados/){.external} ou [instância Public Cloud](https://www.ovh.pt/public-cloud/instances/){.external}).
- Dispor de um ou vários endereços [Additional IP](https://www.ovhcloud.com/pt/bare-metal/ip/){.external}.
- Estar ligado ao servidor usando o protocolo SSH.

> [!warning]
> Esta funcionalidade pode estar indisponível ou limitada nos [servidores dedicados **Eco**](https://eco.ovhcloud.com/pt/about/).
>
> Para mais informações, consulte o nosso [comparativo](https://eco.ovhcloud.com/pt/compare/).

## Instruções

O presente guia inclui instruções paras sistemas Linux e para o Windows Server.

### Debian 10/11

#### 1 - Fazer cópia do ficheiro de configuração (*source file*)

Primeiro, faça uma cópia do ficheiro de configuração para, se necessário, poder reverter o sistema para o estado inicial.

```sh
cp /etc/network/interfaces.d/50-cloud-init /etc/network/interfaces.d/50-cloud-init.bak
```

#### 2 - Alterar o ficheiro de configuração

Agora altere o ficheiro de configuração usando o seguinte comando:

```sh
editor /etc/network/interfaces.d/50-cloud-init
```

De seguida, adicione uma interface secundária:

```bash
auto eth0:0
iface eth0:0 inet static
address ADDITIONAL_IP
netmask 255.255.255.255
```

Para garantir que a interface secundária é ativada ao mesmo tempo que a interface `eth0`, adicione esta instrução à configuração de eth0:

```bash
post-up /sbin/ifconfig eth0:0 ADDITIONAL_IP netmask 255.255.255.255 broadcast ADDITIONAL_IP
pre-down /sbin/ifconfig eth0:0 down
```

Se quiser adicionar dois Additional IP, o ficheiro `/etc/network/interfaces.d/50-cloud-init` deve ter um conteúdo semelhante a este:

```bash
auto eth0
iface eth0 inet dhcp

auto eth0:0
iface eth0:0 inet static
address ADDITIONAL_IP1
netmask 255.255.255.255

auto eth0:1
iface eth0:1 inet static
address ADDITIONAL_IP2
netmask 255.255.255.255
```
Ou assim:

```bash
auto eth0
iface eth0 inet dhcp

# IP 1
post-up /sbin/ifconfig eth0:0 ADDITIONAL_IP1 netmask 255.255.255.255 broadcast ADDITIONAL_IP1
pre-down /sbin/ifconfig eth0:0 down

# IP 2
post-up /sbin/ifconfig eth0:1 ADDITIONAL_IP2 netmask 255.255.255.255 broadcast ADDITIONAL_IP2
pre-down /sbin/ifconfig eth0:1 down
```

#### 3 - Reiniciar a interface de rede

Agora, execute este comando para reiniciar a interface:

```sh
/etc/init.d/networking restart
```

### Debian 6/7/8 e «derivações»

#### 1 - Fazer cópia do ficheiro de configuração (*source file*)

Primeiro, faça uma cópia do ficheiro de configuração para, se necessário, poder reverter o sistema para o estado inicial.

```sh
cp /etc/network/interfaces /etc/network/interfaces.bak
```

#### 2 - Alterar o ficheiro de configuração

Agora altere o ficheiro de configuração usando o seguinte comando:

```sh
editor /etc/network/interfaces
```

De seguida, adicione uma interface secundária: 

```bash
auto eth0:0
iface eth0:0 inet static
address ADDITIONAL_IP
netmask 255.255.255.255
```

Para garantir que a interface secundária é ativada ao mesmo tempo que a interface `eth0`, adicione esta instrução à configuração de eth0:

```bash
post-up /sbin/ifconfig eth0:0 ADDITIONAL_IP netmask 255.255.255.255 broadcast ADDITIONAL_IP
pre-down /sbin/ifconfig eth0:0 down
```

Se quiser adicionar dois Additional IP, o ficheiro `/etc/network/interfaces` deve ter um conteúdo semelhante a este:

```bash
auto eth0
iface eth0 inet static
address SERVER_IP
netmask 255.255.255.0
broadcast xxx.xxx.xxx.255
gateway xxx.xxx.xxx.254

auto eth0:0
iface eth0:0 inet static
address ADDITIONAL_IP1
netmask 255.255.255.255

auto eth0:1
iface eth0:1 inet static
address ADDITIONAL_IP2
netmask 255.255.255.255

Ou assim:

auto eth0
iface eth0 inet static
address SERVER_IP
netmask 255.255.255.0
broadcast xxx.xxx.xxx.255
gateway xxx.xxx.xxx.254

# IP 1
post-up /sbin/ifconfig eth0:0 ADDITIONAL_IP1 netmask 255.255.255.255 broadcast ADDITIONAL_IP1
pre-down /sbin/ifconfig eth0:0 down

# IP 2
post-up /sbin/ifconfig eth0:1 ADDITIONAL_IP2 netmask 255.255.255.255 broadcast ADDITIONAL_IP2
pre-down /sbin/ifconfig eth0:1 down
```

#### 3 - Reiniciar a interface de rede

Agora, execute este comando para reiniciar a interface:

```sh
/etc/init.d/networking restart
```

### Debian 9+, Ubuntu 17.04+ e Arch Linux

Estes sistemas não usam a terminologia eth0, eth1. Como tal, iremos usar o `systemd-network`.

#### 1 - Fazer cópia do ficheiro de configuração (*source file*)

Primeiro, faça uma cópia do ficheiro de configuração para, se necessário, poder reverter o sistema para o estado inicial.

```sh
cp /etc/systemd/network/50-default.network /etc/systemd/network/50-default.network.bak
```

#### 2 - Alterar o ficheiro de configuração

O Additional IP deve ser adicionado ao ficheiro da seguinte forma:

```sh
nano /etc/systemd/network/50-default.network
```

```sh
[Address]
Address=22.33.44.55/32
Label=failover1 # optional
```

O «label» é facultativo. Este serve apenas para ordenar os vários Additional IP.

#### 3 - Reiniciar a interface de rede

Agora, execute este comando para reiniciar a interface:

```sh
systemctl restart systemd-networkd
```

### Fedora 36 e versões posteriores

Fedora utiliza agora ficheiros chave (*keyfiles*).
Fedora utilizava anteriormente perfis de rede armazenados pela NetworkManager no formato ifcfg no diretório `/etc/sysconfig/network-scripts/`.<br>
Uma vez que o ifcfg se encontra agora em imparidade, NetworkManager não cria de forma padrão os novos perfis neste formato. O ficheiro de configuração encontra-se agora no `/etc/NetworkManager/system-connections/`.

#### 1 - Fazer cópia do ficheiro de configuração (*source file*)

Primeiro, faça uma cópia do ficheiro de configuração para poder reverter a situação a qualquer momento:

```sh
cp -r /etc/NetworkManager/system-connections/cloud-init-eno1.nmconnection /etc/NetworkManager/system-connections/cloud-init-eno1.nmconnection.bak
```

#### 2 - Editar o ficheiro de configuração

> [!primary]
>
> Tenha em conta que o nome do ficheiro de rede no nosso exemplo pode diferir do seu. Queira adaptar os comandos em função do nome do seu ficheiro. Para obter o nome da interface de rede para poder editar o ficheiro de rede adequado, pode executar o seguinte comando: `ip a`.
>
> Também pode verificar a interface ligada com o seguinte comando:
>
> `nmcli connection show`
>

O Additional IP deve ser adicionado ao ficheiro da seguinte forma:

```sh
editor /etc/NetworkManager/system-connections/cloud-init-eno1.nmconnection
```

```sh
[ipv4]
method=auto
may-fail=false
address1=ADDITIONAL_IP/32
```

Se tem dois endereços Additional IP a configurar, o ficheiro de configuração deverá ser o seguinte:

```sh
[connection]
id=cloud-init eno1
uuid=xxxxxxx-xxxx-xxxe-ba9c-6f62d69da711
type=ethernet

[user]
org.freedesktop.NetworkManager.origin=cloud-init

[ethernet]
mac-address=MA:CA:DD:RE:SS:XX

[ipv4]
method=auto
may-fail=false
address1=ADDITIONAL_IP1/32
address2=ADDITIONAL_IP2/32
```

#### 3 - Reiniciar a interface

Agora, reinicie a sua interface:

```sh
systemctl restart NetworkManager
```

### Ubuntu 17.10 e versões seguintes

Cada endereço Additional IP necessitará da sua própria linha no ficheiro de configuração. Este tem o nome `50-cloud-init.yaml` e encontra-se em `/etc/netplan`.

#### 1 - Determinar a interface

```sh
ifconfig
```

Tome nota do nome da interface e do endereço MAC.

#### 2 - Criar o ficheiro de configuração

Ligue-se ao seu servidor através de SSH e execute o seguinte comando:

```sh
editor /etc/netplan/50-cloud-init.yaml
```

De seguida, edite o ficheiro com o conteúdo em baixo, substituindo "INTERFACE_NAME", "MAC_ADDRESS" e "ADDITIONAL_IP":

```sh
network:
    version: 2
    ethernets:
        INTERFACE_NAME:
            dhcp4: true
            match:
                macaddress: MAC_ADDRESS
            set-name: INTERFACE_NAME
            addresses:
            - ADDITIONAL_IP/32
```

Registe e feche o ficheiro. Para testar a configuração introduza o seguinte comando:

```sh
# netplan try
```

#### 3 - Aplicar a alteração

De seguida, execute os seguintes comandos para aplicar a configuração:

```sh
# netplan apply
```

### CentOS, AlmaLinux (8 & 9), Rocky Linux (8 & 9), e Fedora (versão 25 e anteriores)

#### 1 - Fazer cópia do ficheiro de configuração (*source file*)

Primeiro, faça uma cópia do ficheiro de configuração para, se necessário, poder usá-lo como modelo (*template*):

```sh
cp /etc/sysconfig/network-scripts/ifcfg-eth0 /etc/sysconfig/network-scripts/ifcfg-eth0:0
```

#### 2 - Alterar o ficheiro de configuração

Altere o ficheiro eth0:0 para substituir o IP:

```sh
editor /etc/sysconfig/network-scripts/ifcfg-eth0:0
```

Substitua o nome do `Device` e, de seguida, o IP existente pelo Additional IP:

```bash
DEVICE="eth0:0"
ONBOOT="yes"
BOOTPROTO="none" # For CentOS use "static"
IPADDR="ADDITIONAL_IP"
NETMASK="255.255.255.255"
BROADCAST="ADDITIONAL_IP"
```

#### 3 - Reiniciar a interface de rede

Agora, execute este comando para reiniciar a interface:

```sh
ifup eth0:0
```

#### Para AlmaLinux e Rocky Linux

Execute este comando para reiniciar a interface:

```sh
systemctl restart NetworkManager
```

### Gentoo

#### 1 - Fazer cópia do ficheiro de configuração (*source file*)

Primeiro, faça uma cópia do ficheiro de configuração para, se necessário, poder reverter o sistema para o estado inicial.

```sh
cp /etc/conf.d/net /etc/conf.d/net.bak
```

#### 2 - Alterar o ficheiro de configuração

Agora, altere o ficheiro para adicionar o Additional IP. Com o Gentoo, o IP alias é adicionado diretamente à interface eth0. Neste caso, não é necessário criar a interface eth0:0 (como no caso do Red Hat ou do CentOS).

> [!warning]
>
> Para garantir o correto funcionamento de algumas configurações OVH, o IP original do servidor e a instrução config_eth0= devem ficar na mesma linha
> 

Depois tem que inserir o Additional IP na linha abaixo da netmask **255.255.255.0** (substitua SERVER_IP pelo IP principal do seu servidor).

```sh
editor /etc/conf.d/net
```

Agora, adicione a seguinte instrução:

```bash
config_eth0=( "SERVER_IP netmask 255.255.255.0" "ADDITIONAL_IP netmask 255.255.255.255 brd ADDITIONAL_IP" )
```

O ficheiro /etc/conf.d/net deve conter a instrução:

```bash
#This blank configuration will automatically use DHCP for any net.
# scripts in /etc/init.d. To create a more complete configuration,
# please review /etc/conf.d/net.example and save your configuration
# in /etc/conf.d/net (this file :]!).
config_eth0=( "SERVER_IP netmask 255.255.255.0"
"ADDITIONAL_IP netmask 255.255.255.255 brd ADDITIONAL_IP" )
routes_eth0=( "default gw SERVER_IP.254" )
```

Para fazer ping ao Additional IP, basta reiniciar a interface de rede.

#### 3 - Reiniciar a interface de rede

Agora, execute este comando para reiniciar a interface:

```sh
/etc/init.d/net.eth0 restart
```

### openSUSE

#### 1 - Fazer cópia do ficheiro de configuração (*source file*)

Primeiro, faça uma cópia do ficheiro de configuração para, se necessário, poder reverter o sistema para o estado inicial.

```sh
cp /etc/sysconfig/network/ifcfg-ens32 /etc/sysconfig/network/ifcfg-ens32.bak
```

#### 2 - Alterar o ficheiro de configuração

Agora, altere o ficheiro /etc/sysconfig/network/ifcfg-ens32 da seguinte forma:

```bash
IPADDR_1=FADDITIONAL_IP
NETMASK_1=255.255.255.255
LABEL_1=ens32:0
```

### cPanel (em CentOS 7)

#### 1: aceder à secção gestão IP da WHM

Na Área de Cliente WHM, clique em `IP Functions`{.action} e selecione `Add a New IP Address`{.action} no menu à esquerda.

![Adicionar um novo endereço IP](images/Cpanel-1.png){.thumbnail}

#### 2: adicionar as informações dos Adicionais IP

Insira o seu endereço Additional IP sob a forma "xxx.xxx.xxx.xxx" no campo "New IP or IP range to add".

Selecione `255.255.255.255` como máscara de sub-rede e clique em `Submit`{.action}.

![indicar novas informações sobre o novo endereço IP](images/Cpanel-2.png){.thumbnail}

> [!warning]
>
> Atenção: se tiver vários endereços IP a configurar num bloco e os adicionar ao mesmo tempo, o sistema WHM irá obrigar-lo a utilizar a máscara de sub-rede `255.255.255.0`.Não é recomendado que utilize esta configuração, deve adicionar cada IP individualmente para utilizar a máscara de sub-rede apropriada `255.255.255.255`.
>

#### 3: verificar a configuração IP atual

De volta para a secção `IP Functions`{.action}, clique em `Show or Delete Current IPs`{.action} para verificar que o endereço Additional IP foi corretamente adicionado.

![check configurgured IP](images/Cpanel-3.png){.thumbnail}

### Windows Server

Os servidores Windows costumam usar a configuração de rede DHCP (configuração predefinida). Caso tenha configurado um Additional IP ou alterado a configuração para usar um IP fixo, ignore esta etapa.

Se não, tem que alterar a configuração de rede para usar IP fixo em vez da configuração DHCP.

Abra a linha de comando `cmd`{.action} ou o `powershell`{.action} e introduza este comando:

```sh
ipconfig /all
```

A seguir, irá visualizar a seguinte informação:

![Result of "ipconfig /all" command](images/guides-network-ipaliasing-windows-2008-1.png){.thumbnail}

Guarde os dados relativos ao IPv4, à máscara de sub-rede, ao *gateway* predefinido e ao nome da placa de rede.

No nosso exemplo, o IP do servidor é: **94.23.229.151**

Os próximos passos pode ser efetuados através da linha de comandos ou da interface gráfica:

#### Através da linha de comandos (recomendado)

Nos comandos indicados abaixo, deve substituir:

|Comando|Valor|
|---|---|
|NETWORK_ADAPTER| Nome da placa de rede (no nosso exemplo: Local Area Connection)|
|IP_ADDRESS| Endereço IP do servidor (no nosso exemplo: 94.23.229.151)|
|SUBNET_MASK| Máscara de sub-rede (no nosso exemplo: 255.255.255.0)|
|GATEWAY| *Gateway* predefinido (no nosso exemplo: 94.23.229.254)|
|ADDITIONAL_IP| Endereço Additional IP que deseja adicionar|

> [!warning]
>
> Atenção: se introduzir informação incorreta, o servidor ficará inacessível. Neste caso, terá de usar o modo Winrescue ou o KVM para corrigir os dados.
> 

Execute as seguintes ações na linha de comandos:

- Passar para IP fixo

```sh
netsh interface ipv4 set address name="NETWORK_ADAPTER" static IP_ADDRESS SUBNET_MASK GATEWAY
```

- Definir servidor DNS

```sh
netsh interface ipv4 set dns name="NETWORK_ADAPTER" static 213.186.33.99
```
- Adicionar Additional IP

```sh
netsh interface ipv4 add address "NETWORK_ADAPTER" ADDITIONAL_IP 255.255.255.255
```

O Additional IP está a funcionar.

#### Através da interface gráfica

1. Aceda ao menu `Iniciar`{.action} > `Painel de Gestão`{.action} > `Rede e Internet`{.action} > `Centro de Rede e Partilha`{.action} > `Alterar as definições da placa`{.action} (no menu à esquerda).
2. Clique com o botão direito do rato em `Ligação à rede local`{.action}.
3. Clique em `Propriedades`{.action}.
4. Selecione o `Protocolo Internet Versão 4 (TCP/IPv4)`{.action}, e clique em `Propriedades`{.action}.
5. Clique em `Utilizar o seguinte endereço IP `{.action} e introduza o IP principal do servidor, a máscara de sub-rede e o *gateway* predefinido, apresentados após a execução do comando `ipconfig`{.action} (ver exemplo acima). Em servidor DNS preferido, introduza 213.186.33.99.

![Internet Protocol Version 4 (TCP/IPv4) Properties](images/guides-network-ipaliasing-windows-2008-2.png){.thumbnail}

> [!warning]
>
> Atenção: se introduzir informação incorreta, o servidor ficará inacessível. Neste caso, terá de usar o modo Winrescue ou o KVM para corrigir os dados.
> 

Depois, clique em `Avançado`{.action} (nas `Definições TCP/IP`{.action}).

![Internet Protocol Version 4 (TCP/IPv4) Properties](images/guides-network-ipaliasing-windows-2008-2.png){.thumbnail}

Na parte `Endereço IP`{.action}, clique em `Adicionar`{.action}:

![Advanced TCP/IPv4 Settings](images/guides-network-ipaliasing-windows-2008-3.png){.thumbnail}

Introduza o Additional IP e a máscara de sub-rede **255.255.255.255**.

![TCP/IP Address](images/guides-network-ipaliasing-windows-2008-4.png){.thumbnail}

Clique em `Adicionar`{.action}.

O Additional IP está a funcionar.

### Plesk

#### Etapa 1: aceder à gestão de IP do Plesk

No painel de configuração Plesk, selecione `Tools & Settings`{.action} na barra lateral esquerda.

![acesso à gestão dos endereços IP](images/pleskip1.png){.thumbnail}

Clique em `IP Endereço`{.action} em **Tools & Settings**.

#### Etapa 2: adicionar informações IP suplementares

Nesta secção, clique no botão `Add IP Address`{.action}.

![adicionar informações IP](images/pleskip2-2.png){.thumbnail}

Introduza o seu endereço Additional IP sob a forma `xxx.xxx.xxx.xxx/32` no campo "IP address and subnet mask", e clique em `OK`{.action}.

![adicionar informações IP](images/pleskip3-3.png){.thumbnail}

#### Etapa 3: verificar a configuração IP atual

Na secção "Endereços IP", verifique se o endereço Additional IP foi adicionado corretamente.

![configuração IP atual](images/pleskip4-4.png){.thumbnail}

### FreeBSD

#### 1 - Identificar a interface

Primeiro tem de identificar o nome da interface de rede principal. Execute o comando `ifconfig`{.action} para obter esta informação:

```sh
ifconfig
```

Resultados apresentados:

```sh
ifconfig
>>> nfe0: flags=8843 metric 0 mtu 1500
>>> options=10b
>>> ether 00:24:8c:d7:ba:11
>>> inet 94.23.196.18 netmask 0xffffff00 broadcast 94.23.196.255
>>> inet 87.98.129.74 netmask 0xffffffff broadcast 87.98.129.74
>>> media: Ethernet autoselect (100baseTX )
>>> status: active
>>> lo0: flags=8049 metric 0 mtu 16384
>>> options=3
>>> inet6 fe80::1%lo0 prefixlen 64 scopeid 0x2
>>> inet6 ::1 prefixlen 128
>>> inet 127.0.0.1 netmask 0xff000000 v comsdvt#
```

No nosso exemplo, o nome da interface é **nfe0**.

#### 2 - Fazer cópia do ficheiro de configuração (<i>source file</i>)

Primeiro, faça uma cópia do ficheiro de configuração para, se necessário, poder reverter o sistema para o estado inicial.

```sh
cp /etc/rc.conf /etc/rc.conf.bak
```

#### 3 - Alterar ficheiro de configuração

Altere o ficheiro /etc/rc.conf, usando o seguinte comando:

```sh
editor /etc/rc.conf
```

De seguida, adicione esta linha no final do ficheiro: ifconfig_INTERFACE_alias0=`inet ADDITIONAL_IP netmask 255.255.255.255 broadcast ADDITIONAL_IP`.

Substitua **INTERFACE** e **ADDITIONAL_IP** pelo nome da interface (indicado no passo 1) e pelo endereço Additional IP. Exemplo:

```bash
ifconfig_nfe0_alias0="inet 87.98.129.74 netmask 255.255.255.255 broadcast 87.98.129.74"
```

#### 4 - Reiniciar interface de rede

Agora, execute este comando para reiniciar a interface:

```sh
/etc/rc.d/netif restart && /etc/rc.d/routing restart
```

### Solaris

#### 1 - Identificar a interface

Primeiro tem de identificar o nome da interface de rede principal. Execute o comando `ifconfig`{.action} para obter esta informação:

```sh
ifconfig -a
```

Resultados apresentados:

```sh
ifconfig -a
>>> lo0: flags=2001000849 mtu 8232 index 1 inet 127.0.0.1 netmask ff000000 e1000g0: flags=1000843 mtu 1500 index 2 inet 94.23.41.167 netmask ffffff00 broadcast 94.23.41.255 ether 0:1c:c0:f2:be:42
```

No nosso exemplo, o nome da interface é **e1000g0**.

#### 2 - Fazer cópia do ficheiro de configuração (<i>source file</i>)

Primeiro, faça uma cópia do ficheiro de configuração para, se necessário, poder reverter o sistema para o estado inicial.

```sh
editor /etc/hostname.e1000g0:1
```

#### 3 - Alterar ficheiro de configuração

Adicione a seguinte informação ao ficheiro: **ADDITIONAL_IP/32 up**, em que **ADDITIONAL_IP** corresponde ao seu Additional IP. Por exemplo:

```bash
188.165.171.40/32 up
```

#### 4 -  Reiniciar a interface de rede

Agora, execute este comando para reiniciar a interface:

```sh
svcadm restart svc:/network/physical:default
```

#### Resolução das deficiências

Se não conseguir estabelecer uma ligação entre a rede pública e o seu alias IP e suspeitar de um problema de rede, reinicie o servidor em [modo rescue](/pages/bare_metal_cloud/dedicated_servers/rescue_mode) e configure o alias diretamente no servidor.

Para isso, execute o seguinte comando depois de reiniciar o servidor em modo rescue:

```bash
ifconfig eth0:0 ADDITIONAL_IP netmask 255.255.255.255 broadcast ADDITIONAL_IP up
```

Onde irá substituir "ADITIONAL_IP" pelo verdadeiro Adicional IP.

De seguida, basta efetuar um ping a partir do seu IP adicional para o exterior. Se isto funcionar, isto provavelmente significa que existe um erro de configuração que precisa de ser corrigido. Se, pelo contrário, o IP ainda não funcionar, abra um ticket à equipa de assistência através da sua [Área de Cliente OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.pt/&ovhSubsidiary=pt){.external} para uma investigação complementar.

## Quer saber mais?

[Modo bridge IP](/pages/bare_metal_cloud/dedicated_servers/network_bridging)

Fale com a nossa comunidade de utilizadores em <https://community.ovh.com/en/>.