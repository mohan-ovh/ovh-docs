---
title: 'Configurare IPv6 su server dedicati'
excerpt: 'Scopri come configurare indirizzi IPv6 sulla nostra infrastruttura'
updated: 2023-07-04
---

> [!primary]
> Questa traduzione è stata generata automaticamente dal nostro partner SYSTRAN. I contenuti potrebbero presentare imprecisioni, ad esempio la nomenclatura dei pulsanti o alcuni dettagli tecnici. In caso di dubbi consigliamo di fare riferimento alla versione inglese o francese della guida. Per aiutarci a migliorare questa traduzione, utilizza il pulsante "Contribuisci" di questa pagina.
>

## Obiettivo

La versione 6 del Protocollo Internet (IPv6) è l’ultima versione del Protocollo Internet (IP). È stata studiata per sopperire alla prevista saturazione degli indirizzi del suo predecessore, IPv4, utilizzando indirizzi a 128-bit invece che a 32-bit. La maggior parte dei server dedicati OVHcloud vengono consegnati con un blocco /64 IPv6, ad eccezione dei server High Grade e Scale che vengono consegnati con un blocco /56 IPv6. Si tratta di più di 18 quintiplici di indirizzi IP di cui puoi disporre a tua scelta. Ciò equivale a oltre 18 quintilioni di indirizzi IP che puoi utilizzare a tuo piacimento.

**Questa guida spiega con vari esempi come configurare indirizzi IPv6 sul tuo server.**

> [!warning]
>OVHcloud fornisce servizi la cui gestione e configurazione sono sotto la tua completa supervisione. Pertanto spetta a te garantire che tali servizi funzionino correttamente.
>
>Questa guida ti mostra come effettuare le operazioni più comuni. Tuttavia, in caso di difficoltà o dubbi, ti consigliamo di contattare un esperto del settore e/o il fornitore del servizio. OVHcloud non potrà fornirti alcuna assistenza. Per maggiori informazioni, consulta la sezione “Per saperne di più” della guida.
>

## Prerequisiti

- Un [server dedicato](https://www.ovhcloud.com/it/bare-metal/) nel tuo account OVHcloud.
- Tutti i dati del tuo IPv6 (prefisso, gateway, etc.).
- Una conoscenza basilare di reti e [SSH](/pages/bare_metal_cloud/dedicated_servers/ssh_introduction).

> [!warning]
> Ti ricordiamo che i server Kimsufi sono forniti con un solo blocco IPv6 (/128). L'IPv6 sarà configurato automaticamente al momento dell'installazione del sistema operativo.
>

## Procedura

Se per installare il tuo server utilizzi un template per il sistema operativo Linux fornito da OVHcloud, dovrai configurare il primo indirizzo IPv6 (l'indirizzo principale) sul server.

Ad esempio, se abbiamo assegnato al tuo server l'intervallo IPv6: `2607:5300:xxxx:xxxx::/64` è possibile utilizzare come IPv6 principale del tuo server l'IPv6: `2607:5300:xxxx:xxx::1/64`.

### Gateway predefinito (esclusi i server High Grade e Scale)

Il gateway predefinito per il tuo blocco IPv6 (IPv6_GATEWAY) è sempre xxxx.xxxx.xxxx.xxFF:FF:FF:FF:FF. Ti ricordiamo che gli "0" di testa possono essere eliminati in un IPv6 per evitare errori nella determinazione del gateway.

- L'intervallo IPv6 del server è `2607:5300:60:62ac::/64` o `2607:5300:60:62ac:0000:000:000:0000/64`. L’IPv6_GATEWAY sarà perciò `2607:5300:60:62FF:FF:FF:FF:FF`.
- L'intervallo IPv6 del server è `2001:41D0:1:46e::/64` o `2001:41D0:0001:046e:0000:000:000:0000/64`. L’IPv6_GATEWAY sarà perciò `2001:41D0:1:4FF:FF:FF:FF:FF`.

Il modo più sicuro per recuperare le informazioni di rete del tuo server è [utilizzare l'API OVHcloud](/pages/manage_and_operate/api/first-steps). 

Eseguite la chiamata API che segue, indicando il nome interno del server (esempio: `ns3956771.ip-169-254-10.eu`):

> [!api]
>
> @api {GET} /dedicated/server/{serviceName}/specifications/network

> [!warning]
> 
> Prima di modificare un file di configurazione, crea sempre un backup dell'originale per poterlo ripristinare in caso di problemi. 
> 

## Gateway predefinito per i server High Grade e Scale

Il gateway predefinito del blocco IPv6 (IPv6_GATEWAY) resta `fe80:0000:0000:0000:000:000:0000:0001`. Ti ricordiamo che gli "0" di testa possono essere eliminati in un IPv6 per evitare errori.

In questo caso, il gateway IPv6 predefinito può essere scritto come segue: `fe80::1`.

### Sistemi operativi Debian e basati su Debian

> [!warning]
>
> Prima di seguire i passaggi qui indicati, consigliamo vivamente di disabilitare l’auto-configurazione dell’IPv6 e gli annunci del router per non incorrere in problemi noti. Puoi farlo aggiungendo le righe che seguono al tuo file `sysctl.conf`, che trovi in /etc/sysctl.conf:
> 
> `net.ipv6.conf.all.autoconf=0`
> 
> `net.ipv6.conf.all.accept_ra=0`
> 
> Dopodiché, puoi applicare queste regole con il comando che segue: `sh sysctl -p`.
> 

#### Step 1: Utilizza l’SSH per connetterti al tuo server

Per ulteriori informazioni fai riferimento a [questa guida](/pages/cloud/dedicated/getting-started-with-dedicated-server#accedi-al-tuo-server).

#### Step 2: Apri il file di configurazione di rete del tuo server

Il file di configurazione di rete del tuo server si trova in `/etc/network/interfaces` o `/etc/network/interfaces.d`. Usa la riga di comando per localizzare il file e aprilo per modificarlo. Prima di procedere si raccomanda di eseguire il backup.

#### Step 3: Modifica il file di configurazione di rete.

Modifica il file come illustrato nell’esempio seguente. In questo esempio, il nome dell’interfaccia di rete è `eth0`. L’interfaccia del tuo server può essere diversa.

```console
iface eth0 inet6 static 
    address YOUR_IPv6 
    netmask 128

post-up /sbin/ip -f inet6 route add IPv6_GATEWAY dev eth0 
post-up /sbin/ip -f inet6 route add default via IPv6_GATEWAY 
pre-down /sbin/ip -f inet6 route del IPv6_GATEWAY dev eth0
pre-down /sbin/ip -f inet6 route del default via IPv6_zGATEWAY
```
È possibile aggiungere ulteriori indirizzi IPv6 aggiungendo le stringhe `up /sbin/ifconfig eth0 inet6 add YOUR_2nd_IPv6/64` al file.

#### Step 4: Salva il file e applica le modifiche

Salva le tue modifiche sul file, quindi riavvia la rete o il server per applicare le modifiche.

#### Step 5: Testa la connettività IPv6

Puoi testare la connettività IPv6 eseguendo i comandi indicati di seguito:

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

Se non sei in grado di testare (effettuare il ping di) questo indirizzo IPv6, verifica la tua configurazione e riprova. Accertati anche che la macchina da cui stai effettuando il test sia connessa all’IPv6. Se ancora non funziona, testa la tua configurazione in [Modalità rescue](/pages/bare_metal_cloud/dedicated_servers/rescue_mode).

### Fedora 26 e successivi

> [!warning]
>
> Questo esempio è stato realizzato con CentOS 7.0. I risultati possono variare quando si utilizzano altre derivate Redhat.
>

#### Step 1: Utilizza l’SSH per connetterti al tuo server

Per ulteriori informazioni fai riferimento a [questa guida](/pages/cloud/dedicated/getting-started-with-dedicated-server#accedi-al-tuo-server).

#### Step 2: Apri il file di configurazione di rete del tuo server

Il file di configurazione di rete del tuo server si trova in `/etc/sysconfig/network-scripts/ifcfg-eth0`. Usa la riga di comando per localizzare questo file e aprilo per modificarlo.

#### Step 3: Modifica il file di configurazione di rete.

Modifica il file come illustrato nell’esempio seguente. In questo esempio, il nome dell’interfaccia di rete è eth0. L’interfaccia del tuo server può essere diversa. Inoltre, abbiamo omesso la configurazione di failover dell’IPv4 per evitare confusione, ma la configurazione dell’IPv6 viene effettuata nello stesso file di configurazione.

```console
IPV6INIT=yes
IPV6_AUTOCONF=no
IPV6_DEFROUTE=yes
IPV6_FAILURE_FATAL=no
IPV6ADDR=YOUR_IPv6/64
IPV6ADDR_SECONDARIES=YOUR_2nd_IPv6/64 YOUR_3rd_IPv6/64
IPV6_DEFAULTGW=IPv6_GATEWAY
```
Se sulla stessa macchina necessiti di più indirizzi IPv6, aggiungili nella riga `IPV6ADDR_SECONDARIES`, separandoli con uno spazio.

#### Step 4: Salva il file e applica le modifiche

Salva le tue modifiche sul file, quindi riavvia la rete o il server per applicare le modifiche.

#### Step 5: Testa la connettività IPv6

Puoi testare la connettività IPv6 eseguendo i comandi indicati di seguito:

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

Se non sei in grado di testare (effettuare il ping di) questo indirizzo IPv6, verifica la tua configurazione e riprova. Accertati anche che la macchina da cui stai effettuando il test sia connessa all’IPv6. Se ancora non funziona, testa la tua configurazione in [Modalità rescue](/pages/bare_metal_cloud/dedicated_servers/rescue_mode).

### FreeBSD

#### Step 1: Utilizza l’SSH per connetterti al tuo server

Per ulteriori informazioni fai riferimento a [questa guida](/pages/cloud/dedicated/getting-started-with-dedicated-server#accedi-al-tuo-server).

#### Step 2: Apri il file di configurazione di rete del tuo server

Il file di configurazione di rete del tuo server si trova in `/etc/rc.conf`. Usa la riga di comando per localizzare questo file e aprilo per modificarlo.

#### Step 3: Modifica il file di configurazione di rete.

Modifica il file come illustrato nell’esempio seguente. In questo esempio, il nome dell’interfaccia di rete è em0. L’interfaccia del tuo server può essere diversa.

```console
IPv6_activate_all_interfaces="YES" 
IPv6_defaultrouter="IPv6_GATEWAY" 
ifconfig_em0_IPv6="inet6 IPv6_Address prefixlen 64"
ifconfig_em0_alias0="inet6 IPv6_Address_2 prefixlen 64"
ifconfig_em0_alias1="inet6 IPv6_Address_3 prefixlen 64"
```

#### Step 4: Salva il file e riavvia il server

Salva le tue modifiche sul file, quindi riavvia la rete o il server per applicare le modifiche.

#### Step 5: Testa la connettività IPv6

Puoi testare la connettività IPv6 eseguendo i comandi indicati di seguito:

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

Se non sei in grado di testare (effettuare il ping di) questo indirizzo IPv6, verifica la tua configurazione e riprova. Accertati anche che la macchina da cui stai effettuando il test sia connessa all’IPv6. Se ancora non funziona, testa la tua configurazione in [Modalità rescue](/pages/bare_metal_cloud/dedicated_servers/rescue_mode).

### Ubuntu 18.04 e 20.04

#### Step 1: Utilizza l’SSH per connetterti al tuo server

Per ulteriori informazioni fai riferimento a [questa guida](/pages/cloud/dedicated/getting-started-with-dedicated-server#accedi-al-tuo-server).

#### Step 2: Apri il file di configurazione di rete del tuo server

Apri il file di configurazione della rete, file che si trova in `/etc/netplan`. Per dimostrarlo, il nostro file è chiamato "50-cloud-init.yaml".

#### Step 3: Modifica il file di configurazione di rete.

Servendoti di un editor di testo, modificare il file "50-cloud-init.yaml" aggiungendo le righe seguenti alle sezioni interessate, come indicato nell'esempio qui sotto.

Sostituisci i valori generici (YOUR_IPV6, IPV6_PREFIX e IPV6_GATEWAY) e l'interfaccia di rete (se il tuo server non utilizza enp1s0) con i valori specifici.

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

Il file di configurazione deve essere simile all'esempio seguente:

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
> È importante rispettare l'allineamento di ciascun elemento del file, come indicato nell'esempio di cui sopra. Non utilizzare il tasto di tabulazione per creare la tua spaziatura. E' necessario solo il tasto spazio. 
>

#### Step 4: Testare e applicare la configurazione

Per testare la configurazione esegui questo comando:

```bash
netplan try
```

Se è corretta, applicala utilizzando il seguente comando:

```bash
netplan apply
```

#### Step 5: Testa la connettività IPv6

Puoi testare la connettività IPv6 eseguendo i comandi indicati di seguito:

```bash
ping6 -c 4 2001:4860:4860::8888

PING 2001:4860:4860::8888(2001:4860:4860::8888) 56 data bytes
>>> 64 bytes from 2001:4860:4860::8888: icmp_seq=1 ttl=57 time=4.07 ms
64 bytes from 2001:4860:4860::8888: icmp_seq=2 ttl=57 time=4.08 ms
64 bytes from 2001:4860:4860::8888: icmp_seq=3 ttl=57 time=4.08 ms
64 bytes from 2001:4860:4860::8888: icmp_seq=4 ttl=57 time=4.07 ms

--- 2001:4860:4860::8888 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3003ms
rtt min/avg/max/mdev = 4.075/4.079/4.083/0.045 ms
```

### Windows Server 2012

#### Step 1: Utilizza l’RDP per connetterti al tuo server

Per ulteriori informazioni fai riferimento a [questa guida](/pages/cloud/dedicated/getting-started-with-dedicated-server#accedi-al-tuo-server).

#### Step 2: Apri la configurazione di rete del tuo server

Innanzitutto, clicca sull’icona della rete nell’area notifiche per andare al `Centro connessioni di rete e condivisione`{.action}.

![Centro connessioni di rete e condivisione](images/ipv6_network_sharing_center.png){.thumbnail}

Clicca su `Modifica impostazioni scheda di rete`{.action}.

![Modifica impostazioni scheda di rete](images/ipv6_change_adapter_settings.png){.thumbnail}.

Clicca con il tasto destro sulla tua scheda di rete, quindi su `Proprietà`{.action}.

![Proprietà scheda di rete](images/ipv6_network_adapter_properties.png){.thumbnail}

Seleziona `Internet Protocol Versione 6`{.action}, quindi clicca su `Proprietà`{.action}.

![Proprietà](images/ipv6_properties.png){.thumbnail}

#### Step 3: Modifica la configurazione di rete 

Digita la configurazione del tuo IPv6 (`indirizzo IPv6` e `gateway predefinito`) e clicca su `OK`{.action}.

![Proprietà](images/ipv6_configuration.png){.thumbnail}

### Risoluzione dei problemi

Se dopo aver testato la tua connessione riscontri ancora dei problemi, crea una richiesta di assistenza per l’esame delle tue configurazioni. È necessario fornire quando segue:

- Il nome e la versione del sistema operativo che utilizzi sul tuo server.
- Il nome e la directory del file di configurazione di rete. 
- Il contenuto di quel file. 

## Per saperne di più

Partecipa alla nostra Community di utenti all’indirizzo <https://community.ovh.com/en/>.
