---
title: 'Configurar IPv6 em servidores dedicados'
excerpt: 'Saiba como configurar endereços IPv6 na nossa infraestrutura'
updated: 2023-07-04
---

> [!primary]
> Esta tradução foi automaticamente gerada pelo nosso parceiro SYSTRAN. Em certos casos, poderão ocorrer formulações imprecisas, como por exemplo nomes de botões ou detalhes técnicos. Recomendamos que consulte a versão inglesa ou francesa do manual, caso tenha alguma dúvida. Se nos quiser ajudar a melhorar esta tradução, clique em "Contribuir" nesta página.
>

## Objetivo

O IPv6 é a versão mais recente do Internet Protocol (IP). Foi concebido para solucionar a já esperada exaustão do seu antecessor, o IPv4, através do recurso a endereços de 128 bits em vez de endereços de 32 bits. A maior parte dos servidores dedicados OVHcloud são entregues com um bloco IPv6 /64, à exceção dos servidores High Grade e Scale que são entregues com um bloco IPv6 /56. Isto representa mais de 18 quintiliões de endereços IP ao seu dispor.

**Este guia explica como configurar endereços IPv6 no seu servidor por meio de vários exemplos.**

> [!warning]
>A OVHcloud presta-lhe serviços cuja configuração e gestão é da sua inteira responsabilidade, cabendo-lhe a si assegurar o seu correto funcionamento. 
>
>Este guia foi concebido para o ajudar, tanto quanto possível, nas tarefas mais comuns. No entanto, caso tenha alguma dificuldade, recomendamos que contacte um fornecedor especializado e/ou o editor do software do serviço, uma vez que não poderemos assisti-lo pessoalmente. Para mais informações, consulte a secção «Saiba mais» neste guia.
>

## Requisitos

- Um [servidor dedicado](https://www.ovhcloud.com/pt/bare-metal/) na sua conta OVHcloud.
- Todos os seus dados IPv6 (prefixo, gateway, etc.).
- Ter conhecimentos básicos de [SSH](/pages/bare_metal_cloud/dedicated_servers/ssh_introduction) e redes.

> [!warning]
> Tenha em conta que os servidores Kimsufi são fornecidos com um único bloco IPv6 (/128). O IPv6 será configurado automaticamente aquando da instalação do sistema operativo.
>

## Instruções

Se está a usar um template Linux fornecido pela OVHcloud para instalar o servidor, deverá configurar o primeiro IPv6 (principal) no servidor. 

Por exemplo, se atribuimos ao seu servidor o intervalo IPv6: `2607:5300:xxxx:xxxx:/64` pode utilizar o IPv6 principal do seu servidor como IPv6: `2607:5300:xxxx:xxxx::1/64`.

### Gateway predefinido (exceto os servidores High Grade e Scale)

O gateway pré-definido para o seu bloco IPv6 (IPV6_GATEWAY) é xxxx.xxxx.xxxx.xxFF:FF:FF:FF:FF. Tenha em conta que os "0" de cabeça podem ser eliminados num IPv6 para evitar erros aquando da determinação da gateway.

por exemplo,

- O intervalo IPv6 do servidor é `2607:5300:60:62ac::/64` ou `2607:5300:60:62ac:0000:0000:0000:0000/64`. Logo, o IPv6_GATEWAY vai ser `2607:5300:60:62FF:FF:FF:FF:FF`.
- O intervalo IPv6 do servidor é `2001:41D0:1:46e::/64` ou `2001:41D0:0001:046e:0000:0000:0000:0000/64`. Logo, o IPv6_GATEWAY vai ser `2001:41D0:1:4FF:FF:FF:FF:FF`.

A forma mais segura de recuperar as informações de rede do seu servidor é [utilizar a API OVHcloud](/pages/manage_and_operate/api/first-steps)(EN). Execute a seguinte chamada API, indicando o nome interno do servidor (exemplo: `ns3956771.ip-169-254-10.eu`):
>

> [!api]
>
> @api {GET} /dedicated/server/{serviceName}/specifications/network

> [!warning]
> 
> Antes de alterar um ficheiro de configuração, crie sempre uma cópia de segurança do original para que possa voltar a ela em caso de problema. 
> 

### Gateway predefinido para os servidores High Grade e Scale

A gateway predefinida do bloco IPv6 (IPv6_GATEWAY) permanece `fe80:0000:0000:0000:0000:0000:0000:0001`. Tenha em conta que os "0" de cabeça podem ser eliminados num IPv6 para evitar erros.

Neste caso, a gateway IPv6 predefinida pode ser escrita do seguinte modo: `fe80::1`.

### Distribuições Debian e baseadas em Debian

> [!warning]
>
> Antes de seguir os próximos passos, recomendamos que desative a autoconfiguração de IPv6 e o router advertising para evitar certos problemas. Pode fazê-lo acrescentando as seguintes linhas ao ficheiro `sysctl.conf`, localizado em /etc/sysctl.conf:
> 
> `net.ipv6.conf.all.autoconf=0`
> 
> `net.ipv6.conf.all.accept_ra=0`
> 
> Uma vez realizada esta ação, pode aplicar estas regras executando o comando: `sh sysctl -p`.
> 

#### Passo 1: Usar o SSH para se conectar ao servidor

[Encontre mais informações neste guia.](/pages/cloud/dedicated/getting-started-with-dedicated-server#ligar-se-ao-servidor/)

#### Passo 2: Abrir o ficheiro de configuração da rede do servidor

O ficheiro de configuração da rede do seu servidor encontra-se em `/etc/network/interfaces` ou `/etc/network/interfaces.d`. Use a linha de comandos para localizar o ficheiro, abri-lo e editá-lo. Antes disso, pense em fazer um backup.

#### Passo 3: Corrigir o ficheiro de configuração de rede

Corrija o ficheiro de modo a ficar como o exemplo abaixo. Neste exemplo, o nome da interface de rede é `eth0`. A interface do seu servidor pode ser diferente.

```console
iface eth0 inet6 static 
    address YOUR_IPv6 
    netmask 128

post-up /sbin/ip -f inet6 route add IPv6_GATEWAY dev eth0 
post-up /sbin/ip -f inet6 route add default via IPv6_GATEWAY 
pre-down /sbin/ip -f inet6 route del IPv6_GATEWAY dev eth0
pre-down /sbin/ip -f inet6 route del default via IPv6_GATEWAY
```
Pode adicionar mais endereços IPv6 acrescentando ao ficheiro esta linha: `up /sbin/ifconfig eth0 inet6 add YOUR_2nd_IPv6/64`.

#### Passo 4: Guardar o ficheiro e aplicar as alterações

Guarde as alterações feitas ao ficheiro e reinicie a rede ou o servidor de modo a aplicar as alterações.

#### Passo 5: Testar a conetividade IPv6

Pode testar a conetividade IPv6 introduzindo os comandos seguintes:

```bash
ping6 -c 4 2001:4860:4860::8888

>>> PING 2001:4860:4860::8888(2001:4860:4860::8888) 56 data bytes
>>> 64 bytes from 2001:4860:4860::8888: icmp_seq=1 ttl=55 time=23.6 ms
>>> 64 bytes from 2001:4860:4860::8888: icmp_seq=2 ttl=55 time=23.8 ms
>>> 64 bytes from 2001:4860:4860::8888: icmp_seq=3 ttl=55 time=23.9 ms
>>> 64 bytes from 2001:4860:4860::8888: icmp_seq=4 ttl=55 time=23.8 ms

>>> --- 2001:4860:4860::8888 ping statistics ---
>>> 1 packets transmitted, 1 received, 0% packet loss, time 0ms
>>> rtt min/avg/max/mdev = 23.670/23.670/23.670/0.000 ms
```

Se não conseguir que este endereço IPv6 faça ping, verifique a configuração e tente novamente. Além disso, assegure-se de que a máquina a partir da qual está a fazer o teste está conectada por IPv6. Se mesmo assim não for bem-sucedido, teste a configuração em [modo Rescue](/pages/bare_metal_cloud/dedicated_servers/rescue_mode).

### Fedora 26 e superiores

> [!warning]
>
> Este exemplo baseia-se em CentOS 7.0. Os resultados podem diferir em caso de uso de outros derivados Red Hat.
>

#### Passo 1: Usar o SSH para se conectar ao servidor

[Encontre mais informações neste guia.](/pages/cloud/dedicated/getting-started-with-dedicated-server#ligar-se-ao-servidor)

#### Passo 2: Abrir o ficheiro de configuração da rede do servidor

O ficheiro de configuração da rede do seu servidor encontra-se em `/etc/sysconfig/network-scripts/ifcfg-eth0`. Use a linha de comandos para localizar o ficheiro, abri-lo e editá-lo.

#### Passo 3: Corrigir o ficheiro de configuração de rede

Corrija o ficheiro de modo a ficar como o exemplo abaixo. Neste exemplo, o nome da interface de rede é eth0. A interface do seu servidor pode ser diferente. Além disso, omitimos a configuração do IPv4 Failover de modo a evitar confusão, mas o IPv6 é configurado no mesmo ficheiro.

```console
IPV6INIT=yes
IPV6_AUTOCONF=no
IPV6_DEFROUTE=yes
IPV6_FAILURE_FATAL=no
IPV6ADDR=YOUR_IPv6/64
IPV6ADDR_SECONDARIES=YOUR_2nd_IPv6/64 YOUR_3rd_IPv6/64
IPV6_DEFAULTGW=IPv6_GATEWAY
```
Se precisar de mais endereços IPv6 na máquina, adicione-os na linha `IPV6ADDR_SECONDARIES`, separados por um espaço em branco. 

#### Passo 4: Guardar o ficheiro e aplicar as alterações

Guarde as alterações feitas ao ficheiro e reinicie a rede ou o servidor de modo a aplicar as alterações.

#### Passo 5: Testar a conetividade IPv6

Pode testar a conetividade IPv6 introduzindo os comandos seguintes:

```bash
ping6 -c 4 2001:4860:4860::8888

>>> PING 2001:4860:4860::8888(2001:4860:4860::8888) 56 data bytes
>>> 64 bytes from 2001:4860:4860::8888: icmp_seq=1 ttl=55 time=23.6 ms
>>> 64 bytes from 2001:4860:4860::8888: icmp_seq=2 ttl=55 time=23.8 ms
>>> 64 bytes from 2001:4860:4860::8888: icmp_seq=3 ttl=55 time=23.9 ms
>>> 64 bytes from 2001:4860:4860::8888: icmp_seq=4 ttl=55 time=23.8 ms

>>> --- 2001:4860:4860::8888 ping statistics ---
>>> 1 packets transmitted, 1 received, 0% packet loss, time 0ms
>>> rtt min/avg/max/mdev = 23.670/23.670/23.670/0.000 ms
```

Se não conseguir que este endereço IPv6 faça ping, verifique a configuração e tente novamente. Além disso, assegure-se de que a máquina a partir da qual está a fazer o teste está conectada por IPv6. Se mesmo assim não for bem-sucedido, teste a configuração em [modo Rescue](/pages/bare_metal_cloud/dedicated_servers/rescue_mode).

### FreeBSD

#### Passo 1: Usar o SSH para se conectar ao servidor

[Encontre mais informações neste guia.](/pages/cloud/dedicated/getting-started-with-dedicated-server#ligar-se-ao-servidor)

#### Passo 2: Abrir o ficheiro de configuração da rede do servidor

O ficheiro de configuração da rede do seu servidor encontra-se em `/etc/rc.conf`. Use a linha de comandos para localizar o ficheiro, abri-lo e editá-lo.

#### Passo 3: Corrigir o ficheiro de configuração de rede

Corrija o ficheiro de modo a ficar como o exemplo abaixo. Neste exemplo, o nome da interface de rede é em0. A interface do seu servidor pode ser diferente.

```console
IPv6_activate_all_interfaces="YES" 
IPv6_defaultrouter="IPv6_GATEWAY" 
ifconfig_em0_IPv6="inet6 IPv6_Address prefixlen 64"
ifconfig_em0_alias0="inet6 IPv6_Address_2 prefixlen 64"
ifconfig_em0_alias1="inet6 IPv6_Address_3 prefixlen 64"
```

#### Passo 4: Guardar o ficheiro e reiniciar o servidor

Guarde as alterações feitas ao ficheiro e reinicie a rede ou o servidor de modo a aplicar as alterações.

#### Passo 5: Testar a conetividade IPv6

Pode testar a conetividade IPv6 introduzindo os comandos seguintes:

```bash
ping6 -c 4 2001:4860:4860::8888

>>> PING 2001:4860:4860::8888(2001:4860:4860::8888) 56 data bytes
>>> 64 bytes from 2001:4860:4860::8888: icmp_seq=1 ttl=55 time=23.6 ms
>>> 64 bytes from 2001:4860:4860::8888: icmp_seq=2 ttl=55 time=23.8 ms
>>> 64 bytes from 2001:4860:4860::8888: icmp_seq=3 ttl=55 time=23.9 ms
>>> 64 bytes from 2001:4860:4860::8888: icmp_seq=4 ttl=55 time=23.8 ms

>>> --- 2001:4860:4860::8888 ping statistics ---
>>> 1 packets transmitted, 1 received, 0% packet loss, time 0ms
>>> rtt min/avg/max/mdev = 23.670/23.670/23.670/0.000 ms
```

Se não conseguir que este endereço IPv6 faça ping, verifique a configuração e tente novamente. Além disso, assegure-se de que a máquina a partir da qual está a fazer o teste está conectada por IPv6. Se mesmo assim não for bem-sucedido, teste a configuração em [modo Rescue](/pages/bare_metal_cloud/dedicated_servers/rescue_mode).

### Ubuntu 18.04 e 20.04

#### Passo 1: Usar o SSH para se conectar ao servidor

[Encontre mais informações neste guia.](/pages/cloud/dedicated/getting-started-with-dedicated-server#ligar-se-ao-servidor)

#### Passo 2: Abrir o ficheiro de configuração da rede do servidor

Abra o ficheiro de configuração da rede, o ficheiro que se encontra em `/etc/netplan`. Para efeitos de demonstração, o nosso ficheiro chama-se '50-cloud-init.yaml'.

#### Passo 3: Corrigir o ficheiro de configuração de rede

Usando um editor de texto, altere o ficheiro '50-cloud-init.yaml' adicionando as seguintes linhas às secções em causa, como indicado no exemplo abaixo.

Substitua os elementos genéricos (YOUR_IPV6, IPV6_PREFIX e IPV6_GATEWAY) e a interface de rede (se o seu servidor não utilizar enp1s0) pelos seus valores específicos.

```yaml
network:
    version: 2
    ethernets:
        enp1s0:
            dhcp4: true
            match:
                macaddress: 00:04:0p:8b:c6:30
            set-name: enp1s0
            addresses:
              - YOUR_IPV6/IPv6_PREFIX
            gateway6: IPv6_GATEWAY
            routes:
                - to: IPv6_GATEWAY
                  scope: link
```

### Ubuntu 21.10 e 22.04

O ficheiro de configuração deve ter o seguinte exemplo:

```yaml
network:
    version: 2
    ethernets:
        enp1s0:
            dhcp4: true
            match:
                macaddress: 00:04:0p:8b:c6:30
            set-name: enp1s0
            addresses:
              - YOUR_IPV6/IPv6_PREFIX
            routes:
                - to: ::/0
                  via: IPv6_GATEWAY
                - to: IPv6_GATEWAY
                  scope: link
```

> [!warning]
>
> É importante respeitar o alinhamento de cada elemento deste ficheiro tal como representado no exemplo acima. Não utilize a tecla de tabulação para criar o seu espaçamento. Apenas a tecla de espaço é necessária. 
>

#### Passo 4: Testar e aplicar a configuração

Pode testar a sua configuração através do seguinte comando:

```bash
netplan try
```

Se a configuração estiver correta, execute-a através do seguinte comando:

```bash
netplan apply
```

#### Passo 5: Testar a conetividade IPv6

Pode testar a conetividade IPv6 introduzindo os comandos seguintes:

```bash
ping6 -c 4 2001:4860:4860::8888

PING 2001:4860:4860::8888(2001:4860:4860::8888) 56 data bytes
64 bytes from 2001:4860:4860::8888: icmp_seq=1 ttl=57 time=4.07 ms
64 bytes from 2001:4860:4860::8888: icmp_seq=2 ttl=57 time=4.08 ms
64 bytes from 2001:4860:4860::8888: icmp_seq=3 ttl=57 time=4.08 ms
64 bytes from 2001:4860:4860::8888: icmp_seq=4 ttl=57 time=4.07 ms

>>> --- 2001:4860:4860::8888 ping statistics ---
>>> 4 packets transmitted, 4 received, 0% packet loss, time 3003ms
>>> rtt min/avg/max/mdev = 4.075/4.079/4.083/0.045 ms
```

### Windows Server 2012

#### Passo 1: Usar o RDP para se conectar ao servidor

[Encontre mais informações neste guia.](/pages/cloud/dedicated/getting-started-with-dedicated-server#ligar-se-ao-servidor)

#### Passo 2: Abrir a configuração da rede do servidor

Em primeiro lugar, faça clique com o botão direito no ícone de rede situado na área de notificações. Aceda ao `Network and Sharing Center`{.action}.

![Network and Sharing Center](images/ipv6_network_sharing_center.png){.thumbnail}

Clique em `Change adapter settings`{.action}.

![Change adapter settings](images/ipv6_change_adapter_settings.png){.thumbnail}

Faça clique com o botão direito sobre o seu adaptador de rede e, de seguida, clique em `Properties`{.action}.

![Network Adapter Properties](images/ipv6_network_adapter_properties.png){.thumbnail}

Selecione `Internet Protocol Version 6`{.action} e clique em `Properties`{.action}.

![Properties](images/ipv6_properties.png){.thumbnail}
#### Passo 3: Corrigir a configuração de rede 

Introduza a sua configuração IPv6 (` IPv6 address` e `Default Gateway`) e clique em `OK`{.action}.

![Properties](images/ipv6_configuration.png){.thumbnail}

### Resolução de problemas

Se depois de testar a sua ligação continuar a experienciar problemas, crie um pedido de apoio a fim de rever as suas configurações. Será necessário fornecer:

- O nome do sistema operativo e a versão em uso no servidor.
- O nome e o diretório do ficheiro de configuração de rede.
- O conteúdo desse ficheiro. 

## Quer saber mais?

Junte-se à nossa comunidade de utilizadores em <https://community.ovh.com/en/>.
