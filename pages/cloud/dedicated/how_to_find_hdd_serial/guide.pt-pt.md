---
title: 'Obter o número de série de um disco rígido'
slug: obter-numero-serie-discofind-disk-serial-number
excerpt: 'Saiba como obter o número de série de um disco rígido para proceder à sua substituição'
section: 'RAID e discos'
---

**Última atualização: 12/09/2018**

## Sumário

Para minimizar os riscos de erro durante a substituição de um disco rígido, pedimos aos nossos clientes que nos forneçam o número de série do disco que pretendem substituir. Se ainda não o fez, não hesite em consultar o nosso manual sobre a [substituição de um disco rígido](https://docs.ovh.com/pt/dedicated/substituicao-disco/){.external} para esclarecer dúvidas acerca do procedimento.

**Este manual explica como obter o número de série de um disco. Na maioria dos casos, pode encontrá-lo ao testar os discos rígidos individualmente com a ferramenta Smartmontools.**


## Requisitos

- Ter acesso root ao servidor \[Linux] ou à conta de administrador \[Windows] (via SSH).
- Ter instalado o utilitário sas2ircu no servidor Windows (disponível através do motor de busca [broadcom](https://www.broadcom.com/support/download-search/?dk=sas2ircu){.external}).


## Instruções

> [!primary]
>
> No caso de um disco NVMe, será preciso colocar o servidor em modo [Rescue64](https://docs.ovh.com/pt/dedicated/rescue_mode/){.external} e utilizar a ferramenta nvme-cli, instalada por predefinição.
> 

### Obter o número de série de um disco rígido com um RAID de software

Para obter o número de série de um disco rígido com uma configuração RAID de software, pode simplesmente utilizar o `smartctl`:

```sh
smartctl -a /dev/sdX | grep Serial Serial Number:    XXXXXXX
```

O periférico é detetado pelo sistema operativo (ex.: /dev/sda, /dev/sdb, etc.).


### Obter o número de série de um disco NVMe

Para os discos NVMe, será necessário utilizar o comando `nvme list`:

```sh
nvme list

Node          SN                  Model                Namespace  Usage                      Format   FW Rev
/dev/nvme0n1  CVPF636600YC450RGN  INTEL SSDPE2MX450G7  1          450.10 GB / 450.10 GB 512  B + 0 B  MDV10253
/dev/nvme1n1  CVPF6333002Y450RGN  INTEL SSDPE2MX450G7  1          450.10 GB / 450.10 GB 512  B + 0 B  MDV10253
```

Poderá então ver os números de série dos diferentes discos NVMe (“nvme0” e “nvme1”).


### Obter o número de série de um disco em Windows

O guia para Windows é praticamente igual ao guia para Linux. Vamos utilizar o utilitário sas2ircu, com os mesmos comandos a que se recorre em Linux.

> [!primary]
>
> Deverá executar o terminal de comando com direitos de administração para evitar qualquer erro.
> 

Para obter o número de série de uma configuração RAID de software, deve usar o comando seguinte:

```sh
.\smartctl -a /dev/sdX Serial Number: 1234567890
```

O periférico é detetado pelo sistema operativo e indicado como se segue: `/dev/sda`, `/dev/sdb`, etc.

![smart_sdb_windows](images/smart_sdb_windows.png){.thumbnail}


### Obter o número de série de um disco com um RAID de hardware

Para informações pormenorizadas sobre estes comandos e a forma de testar os discos rígidos, consulte este [manual](https://docs.ovh.com/gb/en/dedicated/raid-hard/){.external} (versão em inglês).


#### Controlador MegaRaid

##### 1 - Obter os conjuntos RAID

Poderá encontrar os números de série dos discos utilizando o comando `smartctl`. No entanto, antes de executar este comando, terá de descobrir quantos conjuntos RAID (ou discos virtuais) se encontram no servidor.

Para obter esta informação, utilize o seguinte comando:

```sh
MegaCli -LDInfo -Lall -aALL | egrep 'Adapter|Size' | grep -v Strip

Adapter 0

Virtual Drive Information: Size: 36.321 GB

Adapter 1

Virtual Drive Information: Size: 2.727 TB
```

Neste exemplo, existem dois RAID configurados no servidor (“Adapter 0” e “Adapter 1”). Ambos devem estar associados a `/dev/sda` e `/dev/sdb`.


##### 2 - Obter as informações dos discos

A seguir, deve reunir as informações sobre o disco físico utilizando o seguinte comando:

```sh
 MegaCli -PDList -aAll | egrep 'Slot\ Number|Device\ Id|Inquiry\ Data|Raw|Firmware\ state' | sed 's/Slot/\nSlot/g'

Slot Number: 0
Device Id: 4
Raw Size: 279.460 GB [0x22eec130 Sectors]
Firmware state: Online, Spun Up
Inquiry Data: BTWL3450062J300PGN  INTEL SSDSC2BB300G4                     D2010355

Slot Number: 1
Device Id: 5
Raw Size: 279.460 GB [0x22eec130 Sectors] 
Firmware state: Online, Spun Up 
Inquiry Data: BTWL345003X6300PGN  INTEL SSDSC2BB300G4                     D2010355

Slot Number: 2
Device Id: 7
Raw Size: 2.728 TB [0x15d50a3b0 Sectors] 
Firmware state: Online, Spun Up 
Inquiry Data:       PN2234P8K2PKDYHGST HUS724030ALA640                    MF8OAA70

Slot Number: 3 
Device Id: 6 
Raw Size: 2.728 TB [0x15d50a3b0 Sectors] 
Firmware state: Online, Spun Up 
Inquiry Data:       PN2234P8JYP59YHGST HUS724030ALA640                    MF8OAA70
```

##### 3 - Obter o número de série

Os ID do periférico e do adaptador serão utilizados para indicar ao `smartctl` qual o disco a procurar em determinado conjunto RAID.

Assim, o comando deve ter o seguinte formato:

```sh
smartctl -d megaraid,N -a /dev/sdX | grep Serial Serial Number: 1234567890
```

O ID do periférico RAID será apresentado como se segue: `/dev/sda` = 1.º RAID, `/dev/sdb` = 2.º RAID, etc.


> [!primary]
>
> Em certas situações, poderá receber este resultado:
> 
> ```
> /dev/sda [megaraid_disk_00] [SAT]: Device open changed type from 'megaraid' to 'sat'
> ```
> 
> Deve substituir `megaraid` por `sat+megaraid`:
>
> ```
> smartctl -d sat+megaraid,N -a /dev/sdX | grep Serial Serial Number:    1234567890
> ```
>

#### Obter o número de série de um disco (controlador RAID LSI)

O controlador RAID LSI utiliza um módulo chamado `sg-map`, que associa os periféricos a `/dev/sgX` (sendo **X** o número que define o periférico).

Pode recorrer a [este manual](https://docs.ovh.com/gb/en/dedicated/raid-hard/){.external} (versão em inglês) para determinar que disco rígido corresponde a que periférico sg.

Quando tiver encontrado o periférico sg associado ao disco rígido que deseja analisar, utilize o comando a seguir:

```sh
smartctl -a /dev/sgX | grep Serial Serial Number:    1234567890
```

O número do periférico sg será apresentado como se segue: `/dev/sg0`, `/dev/sg1`, etc.


## Quer saber mais?

[Substituir um disco com defeito](https://docs.ovh.com/pt/dedicated/substituicao-disco/){.external}

[Configurar um RAID de hardware](https://docs.ovh.com/gb/en/dedicated/raid-hard/){.external} (versão em inglês)

[Configurar um RAID de software](https://docs.ovh.com/es/dedicated/raid-software/){.external} (versão em espanhol)

Fale com a nossa comunidade de utilizadores: [Comunidade OVH](https://community.ovh.com/en/){.external}