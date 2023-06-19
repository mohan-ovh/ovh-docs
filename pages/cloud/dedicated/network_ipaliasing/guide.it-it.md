---
title: Configurare un Alias IP
excerpt: 'Scopri come aggiungere uno o più Additional IP alla tua configurazione'
updated: 2023-06-15
---

> [!primary]
> Questa traduzione è stata generata automaticamente dal nostro partner SYSTRAN. I contenuti potrebbero presentare imprecisioni, ad esempio la nomenclatura dei pulsanti o alcuni dettagli tecnici. In caso di dubbi consigliamo di fare riferimento alla versione inglese o francese della guida. Per aiutarci a migliorare questa traduzione, utilizza il pulsante "Contribuisci" di questa pagina.
>


> [!primary]
>
> Dal 6 ottobre 2022, la nostra soluzione "Failover IP" si chiama [Additional IP](https://www.ovhcloud.com/it/network/additional-ip/). Questo non ha alcun impatto sulla sua funzionalità.
>

## Obiettivo

L'alias IP (o IP aliasing) è un tipo di configurazione del tuo server dedicato che permette di associare più indirizzi IP a un'interfaccia di rete. 

**Questa guida ti mostra la procedura da seguire per effettuare l’operazione.**

## Prerequisiti

- Disporre di un server dedicato ([server dedicati](https://www.ovh.it/server_dedicati/){.external}, [VPS](https://www.ovh.it/vps/){.external} o [istanze Public Cloud]( https://www.ovh.it/public-cloud/istanze/){.external})
- Disporre di uno o più [Additional IP](https://www.ovhcloud.com/it/bare-metal/ip/){.external}
- Essere connesso al server in SSH (accesso root)

> [!warning]
> Questa funzionalità può non essere disponibile o limitata sui [server dedicati **Eco**](https://eco.ovhcloud.com/it/about/).
>
> Per maggiori informazioni, consulta la nostra [a confronto](https://eco.ovhcloud.com/it/compare/).

## Procedura

Di seguito le procedure di configurazione per le principali distribuzioni.

### Debian 10/11

#### Step 1: crea il file sorgente

Per prima cosa, ti consigliamo di effettuare una copia del file sorgente per poter ripristinare la versione precedente se necessario:

```sh
cp /etc/network/interfaces.d/50-cloud-init /etc/network/interfaces.d/50-cloud-init.bak
```

#### Step 2: modifica il file sorgente

Ora è possibile modificare il file sorgente:

```sh
editor /etc/network/interfaces.d/50-cloud-init
```

e aggiungere un’interfaccia secondaria:

```bash
auto eth0:0
iface eth0:0 inet static
address ADDITIONAL_IP
netmask 255.255.255.255
```

Per assicurarti che l’interfaccia secondaria venga attivata insieme all'interfaccia `eth0`, aggiungi questa riga alla configurazione di eth0:

```bash
post-up /sbin/ifconfig eth0:0 ADDITIONAL_IP netmask 255.255.255.255 broadcast ADDITIONAL_IP
pre-down /sbin/ifconfig eth0:0 down
```

Per configurare due Additional IP, il file `/etc/network/interfaces.d/50-cloud-init` deve essere di questo tipo:

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
O così:

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


#### Step 3: riavvia l’interfaccia

Per riavviare l’interfaccia esegui il comando:

```sh
/etc/init.d/networking restart
```

### Debian 6/7/8 e derivati

#### Step 1: crea il file sorgente

Per prima cosa, ti consigliamo di effettuare una copia del file sorgente per poter ripristinare la versione precedente se necessario:

```sh
cp /etc/network/interfaces /etc/network/interfaces.bak
```

#### Step 2: modifica il file sorgente

Ora è possibile modificare il file sorgente:

```sh
editor /etc/network/interfaces
```

e aggiungere un’interfaccia secondaria:

```bash
auto eth0:0
iface eth0:0 inet static
address ADDITIONAL_IP
netmask 255.255.255.255
```

Per assicurarti che l’interfaccia secondaria venga attivata insieme all'interfaccia `eth0`, aggiungi questa riga alla configurazione di eth0:

```bash
post-up /sbin/ifconfig eth0:0 ADDITIONAL_IP netmask 255.255.255.255 broadcast ADDITIONAL_IP
pre-down /sbin/ifconfig eth0:0 down
```

Per configurare due Additional IP, il file `/etc/network/interfaces` deve essere di questo tipo:

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

O così:

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


#### Step 3: riavvia l’interfaccia

Per riavviare l’interfaccia esegui il comando:

```sh
/etc/init.d/networking restart
```

### Debian 9+, Ubuntu 17.04+ e Arch Linux

Queste distribuzioni non utilizzano più la nomenclatura eth0, eth1... per le interfacce. Utilizzeremo quindi, in modo più generico, il servizio `systemd-network`.

#### Step 1: crea il file sorgente

Per prima cosa, ti consigliamo di effettuare una copia del file sorgente per poter ripristinare la versione precedente se necessario:

```sh
cp /etc/systemd/network/50-default.network /etc/systemd/network/50-default.network.bak
```

#### Step 2: modifica il file sorgente

Ora è possibile aggiungere il tuo Additional IP nel file sorgente, utilizzando il comando:

```sh
nano /etc/systemd/network/50-default.network
```

```sh
[Address]
Address=22.33.44.55/32
Label=failover1 # optional
```

Il label è opzionale e serve a distinguere i diversi Additional IP.

#### Step 3: riavvia l’interfaccia

Per riavviare l’interfaccia esegui il comando:

```sh
systemctl restart systemd-networkd
```

### Fedora 36 e versioni successive

Da questo momento, Fedora utilizza file chiave (*keyfiles*).
In precedenza Fedora utilizzava profili di rete memorizzati da NetworkManager in formato ifcfg nella directory `/etc/sysconfig/network-scripts/`.<br>
Poiché l'ifcfg ha subito una riduzione di valore, NetworkManager non crea di default i nuovi profili in questo formato. Il file di configurazione è disponibile in `/etc/NetworkManager/system-connections/`.

#### Step 1: crea il file sorgente

Per prima cosa, esegui una copia del file sorgente per poter tornare indietro in qualsiasi momento:

```sh
cp -r /etc/NetworkManager/system-connections/cloud-init-eno1.nmconnection /etc/NetworkManager/system-connections/cloud-init-eno1.nmconnection.bak
```

#### Step 2: modifica il file sorgente

> [!primary]
>
> Ti ricordiamo che il nome del file di rete nel nostro esempio può differire dal tuo. Adatta i comandi in base al nome del tuo file. Per generare il nome della tua interfaccia di rete per poter modificare il file di rete corrispondente, esegui il comando: `ip a`
>
> Verifica anche l'interfaccia connessa con questo comando:
>
> `nmcli connection show`
>

Aggiungi il tuo Additional IP al file di configurazione come segue:

```sh
editor /etc/NetworkManager/system-connections/cloud-init-eno1.nmconnection
```

```sh
[ipv4]
method=auto
may-fail=false
address1=ADDITIONAL_IP/32
```

Se hai due indirizzi Additional IP da configurare, il file di configurazione dovrebbe essere di questo tipo:

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

#### Step 3: riavvia l’interfaccia

Per riavviare l’interfaccia esegui il comando:

```sh
systemctl restart NetworkManager
```

### Ubuntu 17.10 e versioni successive

Ogni indirizzo Additional IP avrà bisogno della sua linea nel file di configurazione. `50-cloud-init.yaml` ed è situata nella `/etc/netplan`.


#### Step 1: determinare l'interfaccia

```sh
ifconfig
```

Annota il nome dell'interfaccia e il suo indirizzo MAC.

#### Step 2: crea il file di configurazione

Accedi al tuo server via SSH ed esegui questo comando:

```sh
editor /etc/netplan/50-cloud-init.yaml
```

Successivamente, modifica il file con il contenuto qui sotto, sostituendo "INTERFACE_NAME", "MAC_ADDRESS" e "ADDITIONAL_IP":

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

Salva e chiudi il file. Per testare la configurazione, inserisci questo comando:

```sh
# netplan try
```

#### Step 3: applicare la modifica

Per applicare la configurazione, esegui questi comandi:

```sh
# netplan apply
```

### CentOS, AlmaLinux (8 & 9), Rocky Linux (8 & 9), e Fedora (25 e precedenti)

#### Step 1: crea il file sorgente

Per prima cosa, ti consigliamo di effettuare una copia del file sorgente per poterlo utilizzare come template:

```sh
cp /etc/sysconfig/network-scripts/ifcfg-eth0 /etc/sysconfig/network-scripts/ifcfg-eth0:0
```

#### Step 2: modifica il file sorgente

Ora è possibile modificare il file eth0:0 per sostituire l’IP:

```sh
editor /etc/sysconfig/network-scripts/ifcfg-eth0:0
```

Sostituisci prima il nome del `Device` e poi l'IP esistente con l'Additional IP assegnato:

```bash
DEVICE="eth0:0"
ONBOOT="yes"
BOOTPROTO="none" # For CentOS use "static"
IPADDR="ADDITIONAL_IP"
NETMASK="255.255.255.255"
BROADCAST="ADDITIONAL_IP"
```

#### Step 3: riavvia l’interfaccia

Per riavviare l’interfaccia esegui il comando:

```sh
ifup eth0:0
```

#### Per AlmaLinux e Rocky Linux

È necessario riavviare il sistema :

```sh
systemctl restart NetworkManager
```

### Gentoo

#### Step 1: crea il file sorgente

Per prima cosa, ti consigliamo di effettuare una copia del file sorgente per poter ripristinare la versione precedente se necessario:

```sh
cp /etc/conf.d/net /etc/conf.d/net.bak
```

#### Step 2: modifica il file sorgente

Ora è possibile modificare il file per aggiungervi l’Additional IP. Su Gentoo, viene aggiunto direttamente un alias all’interfaccia eth0. Non sarà quindi necessario creare l’interfaccia eth0:0 come per Red Hat o CentOS.

> [!warning]
>
> Per assicurare il corretto funzionamento di alcune operazioni specifiche di OVH, l'IP di default del server e config\_eth0= devono essere sulla stessa riga. 
> 

È sufficiente inserire il tuo Additional IP nella linea successiva alla netmask **255.255.255.0** (sostituisci SERVER\_IP con l'IP principale del tuo server).

```sh
editor /etc/conf.d/net
```

Dovrai quindi aggiungere:

```bash
config_eth0=( "SERVER_IP netmask 255.255.255.0" "ADDITIONAL_IP netmask 255.255.255.255 brd ADDITIONAL_IP" )
```

Il file /etc/conf.d/net deve contenere:


```bash
#This blank configuration will automatically use DHCP for any net.
# scripts in /etc/init.d. To create a more complete configuration,
# please review /etc/conf.d/net.example and save your configuration
# in /etc/conf.d/net (this file :]!).
config_eth0=( "SERVER_IP netmask 255.255.255.0"
"ADDITIONAL_IP netmask 255.255.255.255 brd ADDITIONAL_IP" )
routes_eth0=( "default gw SERVER_IP.254" )
```

Per effettuare un ping sul tuo Additional IP, sarà sufficiente riavviare l’interfaccia di rete.


#### Step 3: riavvia l’interfaccia

Per riavviare l’interfaccia esegui il comando:

```sh
/etc/init.d/net.eth0 restart
```


### openSUSE

#### Step 1: crea il file sorgente

Per prima cosa, ti consigliamo di effettuare una copia del file sorgente per poter ripristinare la versione precedente se necessario:

```sh
cp /etc/sysconfig/network/ifcfg-ens32 /etc/sysconfig/network/ifcfg-ens32.bak
```

#### Step 2: modifica il file sorgente

Ora è possibile modificare il file `/etc/sysconfig/network/ifcfg-ens32` in questo modo:

```bash
IPADDR_1=ADDITIONAL_IP
NETMASK_1=255.255.255.255
LABEL_1=ens32:0 
```


### cPanel (su CentOS 7)

#### Step 1: accedi alla gestione IP di WHM

Nello Spazio Cliente WHM, clicca su `IP Functions`{.action} e seleziona `Add a New IP Address`{.action} nel menu a sinistra.

![Aggiungere un nuovo indirizzo IP](images/Cpanel-1.png){.thumbnail}

#### Step 2: aggiungi le informazioni degli Additional IP

Inserisci il tuo indirizzo Additional IP nella forma `xxx.xxx.xxx.xxx` nel campo "New IP or IP range to add".

Seleziona `255.255.255.255` come subnet mask e clicca su `Submit`{.action}.

![inserire nuove informazioni sul nuovo indirizzo IP](images/Cpanel-2.png){.thumbnail}

> [!warning]
>
> Attenzione: se si hanno più IP da configurare sullo stesso blocco e li si aggiunge tutti insieme, il sistema WHM obbliga a utilizzare la subnet mask `255.255.255.0`. Non si consiglia di utilizzare questa configurazione; è necessario aggiungere ogni IP singolarmente per utilizzare la subnet mask `255.255.255.255` appropriata.
>

#### Step 3: verifica la configurazione IP corrente

Di ritorno alla sezione `IP Functions`{.action}, clicca su `Show or Delete Current IP Addresses`{.action} per verificare che l'indirizzo Additional IP sia stato aggiunto correttamente.

![check configured IP](images/Cpanel-3.png){.thumbnail}

### Windows Server

I server Windows vengono forniti solitamente con una configurazione di rete con DHCP abilitato di default. Se hai già aggiunto un Additional IP o modificato la tua configurazione per utilizzare un IP statico, passa direttamente allo step successivo.

In caso contrario sarà necessario modificare la configurazione di rete per impostare IP statico al posto del DHCP.

Apri il prompt dei comandi `cmd`{.action} o `powershell`{.action} e digita il comando:

```sh
ipconfig /all
```

Il risultato restituito sarà, ad esempio:

![Result of "ipconfig /all" command](images/guides-network-ipaliasing-windows-2008-1.png){.thumbnail}

Recupera il tuo IPv4, la subnet mask, il gateway predefinito e il nome della scheda di rete.

Nel nostro esempio, l’IP del server è: **94.23.229.151**


Per continuare, è possibile effettuare le operazioni sia da riga di comando che tramite interfaccia grafica:

#### Da riga di comando (consigliato)

Nei comandi seguenti, è necessario sostituire:

|Comando|Valore|
|---|---|
|NETWORK_ADAPTER|Nome della scheda di rete (nel nostro esempio, Local Area Connection)|
|IP_ADDRESS|Indirizzo IP del server (nel nostro esempio, 94.23.229.151)|
|SUBNET_MASK| Maschera di sottorete (nel nostro esempio, 255.255.255.0)|
|GATEWAY| Gateway predefinito (nel nostro esempio, 94.23.229.254)|
|ADDITIONAL_IP|Indirizzo Additional IP da aggiungere|

> [!warning]
>
> Attenzione: se le informazioni inserite non sono corrette, il server non sarà più raggiungibile e sarà necessario effettuare le correzioni accedendo in modalità Winrescue o tramite KVM. 
> 

Nel prompt dei comandi:

* Passare a un IP statico

```sh
netsh interface ipv4 set address name="NETWORK_ADAPTER" static IP_ADDRESS SUBNET_MASK GATEWAY
```
 
* Definire il server DNS

```sh
netsh interface ipv4 set dns name="NETWORK_ADAPTER" static 213.186.33.99
``` 

* Aggiungere un Additional IP

```sh
netsh interface ipv4 add address "NETWORK_ADAPTER" ADDITIONAL_IP 255.255.255.255
```

Da questo momento, il tuo Additional IP è attivo.


#### Da interfaccia grafica

1. Accedi al menu `Start`{.action} > `Pannello di controllo`{.action} > `Rete e Internet`{.action} > `Centro connessioni di rete e condivisione`{.action} > `Modifica impostazioni scheda`{.action} (nel menu a sinistra)
2. Clicca con il tasto destro su `Connessione alla rete locale`{.action}
3. Clicca su `Proprietà`{.action}
4. Seleziona `Protocollo Internet Version 4 (TCP/IPv4)`{.action} e clicca su `Proprietà`{.action}
5. Clicca su `Utilizza il seguente indirizzo IP`{.action} e inserisci l'IP principale del tuo server, la subnet mask e il gateway predefinito ottenuto precedentemente con il comando `ipconfig`{.action} . In `Server DNS preferito`, inserisci 213.186.33.99.

![Internet Protocol Version 4 (TCP/IPv4) Properties](images/guides-network-ipaliasing-windows-2008-2.png){.thumbnail}


> [!warning]
>
> Attenzione: se le informazioni inserite non sono corrette, il server non sarà più raggiungibile e sarà necessario effettuare le correzioni accedendo in modalità Winrescue o tramite KVM. 
> 

In seguito, clicca su `Avanzate`{.action} (sempre nelle `Impostazioni TCP/IP`{.action}).

![Internet Protocol Version 4 (TCP/IPv4) Properties](images/guides-network-ipaliasing-windows-2008-2.png){.thumbnail}

Nella parte `indirizzo IP`{.action}, clicca su `Aggiungi...`{.action}:

![Advanced TCP/IPv4 Settings](images/guides-network-ipaliasing-windows-2008-3.png){.thumbnail}

Inserisci il tuo Additional IP e la subnet mask **255.255.255.255**.

![TCP/IP Address](images/guides-network-ipaliasing-windows-2008-4.png){.thumbnail}

Clicca su `Aggiungi`{.action}.

Da questo momento, il tuo Additional IP è attivo.

### Plesk

#### Step 1: accedere alla gestione IP di Plesk

Nel pannello di configurazione Plesk, seleziona `Tools & Settings`{.action} nella barra laterale sinistra.

![accesso alla gestione degli indirizzi IP](images/pleskip1.png){.thumbnail}

Clicca su `IP Indirizzi`{.action} con **Tools & Settings**.

#### Step 2: aggiungi le informazioni IP supplementari

In questa sezione, clicca sul pulsante `Add IP Address`{.action}.

![aggiungi informazioni IP](images/pleskip2-2.png){.thumbnail}

Inserisci il tuo indirizzo Additional IP nella forma `xxx.xxx.xxx.xxx/32` nel campo "IP address and subnet mask" e clicca su `OK`{.action}.

![aggiungi informazioni IP](images/pleskip3-3.png){.thumbnail}

#### Step 3: verifica la configurazione IP corrente

Per verificare che l'indirizzo Additional IP sia stato aggiunto correttamente, accedi alla sezione "Indirizzi IP".

![configurazione IP attuale](images/pleskip4-4.png){.thumbnail}

### FreeBSD

#### Step 1: identifica l'interfaccia

Recupera il nome della tua interfaccia di rete principale utilizzando il comando `ifconfig`{.action}:

```sh
ifconfig
```

Otterrai questo risultato:

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

Nel nostro esempio, il nome dell’interfaccia è **nfe0**.


#### Step 2: crea il file sorgente

Ti consigliamo di effettuare una copia del file sorgente per poter ripristinare la versione precedente se necessario:

```sh
cp /etc/rc.conf /etc/rc.conf.bak
```

#### Step 3: modifica il file sorgente

Ora è possibile modificare il file /etc/rc.conf:

```sh
editor /etc/rc.conf
```

Alla fine del file, aggiungi la riga `ifconfig_INTERFACE_alias0=”inet ADDITIONAL_IP netmask 255.255.255.255 broadcast ADDITIONAL_IP”`.

Sostituisci **INTERFACE** e **ADDITIONAL_IP** rispettivamente con il nome della tua interfaccia (identificata nel primo step) e con il tuo Additional IP. Per esempio:


```bash
ifconfig_nfe0_alias0="inet 87.98.129.74 netmask 255.255.255.255 broadcast 87.98.129.74"
```

#### Step 4: riavvia l’interfaccia

Per riavviare l’interfaccia esegui il comando:

```sh
/etc/rc.d/netif restart && /etc/rc.d/routing restart
```

### Solaris

#### Step 1: identifica l'interfaccia

Recupera il nome della tua interfaccia di rete principale utilizzando il comando `ifconfig`{.action}:

```sh
ifconfig -a
```

Otterrai questo risultato:

```sh
ifconfig -a
>>> lo0: flags=2001000849 mtu 8232 index 1 inet 127.0.0.1 netmask ff000000 e1000g0: flags=1000843 mtu 1500 index 2 inet 94.23.41.167 netmask ffffff00 broadcast 94.23.41.255 ether 0:1c:c0:f2:be:42
```

Nel nostro esempio, il nome dell’interfaccia è **e1000g0**.


#### Step 2: crea il file sorgente

Ti consigliamo di effettuare una copia del file sorgente per poter ripristinare la versione precedente se necessario:

```sh
editor /etc/hostname.e1000g0:1
```

#### Step 3: modifica il file sorgente

In questo file, inserisci: **ADDITIONAL_IP/32 up**, dove **ADDITIONAL_IP** corrisponde al tuo Additional IP. Per esempio:

```bash
188.165.171.40/32 up
```

#### Step 4: riavvia l’interfaccia

Per riavviare l’interfaccia esegui il comando:

```sh
svcadm restart svc:/network/physical:default
```


#### Risoluzione dei difetti

Se non riesci a stabilire una connessione tra la rete pubblica e il tuo alias IP e riscontri un problema di rete, riavvia il server in [modalità Rescue](/pages/cloud/dedicated/rescue_mode) e configura l'alias direttamente sul server.

Una volta riavviato il server in Rescue mode, esegui questo comando:

```bash
ifconfig eth0:0 ADDITIONAL_IP netmask 255.255.255.255 broadcast ADDITIONAL_IP up
```

dove sostituisci "ADDIZIONALE_IP" con l'IP autentico.

In seguito, ti basta effettuare un ping dal tuo Additional IP verso l'esterno. Se funziona, significa probabilmente che è necessario correggere un errore di configurazione. Se invece l'IP non funziona ancora, apri un ticket al team di assistenza tramite il tuo [Spazio Cliente OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.it/&ovhSubsidiary=it){.external} per ulteriori indagini.

## Per saperne di più

[Modalità bridge IP](/pages/cloud/dedicated/network_bridging)

Contatta la nostra Community di utenti all’indirizzo <https://community.ovh.com/en/>.