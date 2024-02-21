---
title: Iniziare a utilizzare un VPS
excerpt: Come gestire un VPS dallo Spazio Cliente OVHcloud e scopri gli step iniziali del suo utilizzo, incluse le connessioni remote e le misure di sicurezza
updated: 2024-02-19
---

> [!primary]
> Questa traduzione è stata generata automaticamente dal nostro partner SYSTRAN. I contenuti potrebbero presentare imprecisioni, ad esempio la nomenclatura dei pulsanti o alcuni dettagli tecnici. In caso di dubbi consigliamo di fare riferimento alla versione inglese o francese della guida. Per aiutarci a migliorare questa traduzione, utilizza il pulsante "Contribuisci" di questa pagina.
>

## Obiettivo

Un server privato virtuale (VPS) è un server dedicato virtualizzato. A differenza delle soluzioni di hosting Web OVHcloud gestite da OVHcloud, la configurazione e la manutenzione di un sistema VPS è di responsabilità dell’amministratore di sistema.

**Scopri le informazioni necessarie per muovere i primi passi nel tuo VPS.**


## Prerequisiti

- Disporre di un [VPS](https://www.ovhcloud.com/it/vps/) nello Spazio Cliente OVHcloud
- Avere accesso allo [Spazio Cliente OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.it/&ovhSubsidiary=it)

## Procedura

Accedi allo [Spazio Cliente OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.it/&ovhSubsidiary=it), sezione `Bare Metal Cloud`{.action} e seleziona il server nella sezione `Server privati virtuali`{.action}.

### Interfaccia del Pannello di controllo

La scheda `Home`{.action} contiene informazioni importanti sul tuo servizio e ti permette di effettuare operazioni essenziali.

![VPS Home](images/vpshome.png){.thumbnail}

#### Il tuo VPS <a name="yourvps"></a>

In questa sezione vengono visualizzate le informazioni di base sul VPS e lo stato del servizio.

##### **Nome**

Cliccando su `...`{.action} e selezionando `Cambia nome`{.action}, è possibile inserire un nome distinto per questo VPS. Questa funzionalità è utile per facilitare la navigazione nello Spazio Cliente quando si gestiscono più servizi VPS. Il nome del servizio interno resta in formato *vps-XXXXX.vps.ovh.net*.

##### **Boot**

La modalità di avvio visualizzata qui è in modalità "normale", in cui il sistema carica il sistema operativo installato (*LOCAL*), oppure in **modalità Rescue**, fornita da OVHcloud in caso di risoluzione dei problemi. Utilizza il pulsante `...`{.action} per [riavviare il VPS](#reboot-current-range) o avvialo in modalità Rescue.

Per maggiori informazioni, consulta la nostra guida sulla modalità [Rescue](/pages/bare_metal_cloud/virtual_private_servers/rescue).

##### **SO/Distribuzione**

Si tratta del sistema operativo attualmente installato. Utilizzare il pulsante `...`{.action} per [reinstallare lo stesso sistema operativo o selezionarne un altro tra le opzioni disponibili](#reinstallvps).

Ti ricordiamo che una reinstallazione comporta la cancellazione di tutti i dati salvati sul VPS (ad eccezione dei dischi aggiuntivi).

> [!primary]
>
> Se è stato ordinato un VPS **Windows**, è possibile scegliere solo un OS Windows per la reinstallazione. Se Windows non è stato selezionato al momento dell'ordine, non potrà essere installato dopo la consegna del VPS.
>

Una volta installato il sistema, è necessario implementare gli aggiornamenti di sicurezza. Troverai maggiori informazioni qui [sotto](#reinstallvps) e nella nostra guida [Proteggere un VPS](/pages/bare_metal_cloud/virtual_private_servers/secure_your_vps).

##### **Zona**/**Localizzazione**

In queste sezioni vengono fornite informazioni sulla localizzazione del VPS. Questa operazione può essere utile, ad esempio, per identificare gli impatti sul servizio indicati in [status reports](https://bare-metal-servers.status-ovhcloud.com/).

#### La tua configurazione

##### **Modello**

Questo elemento indica il riferimento commerciale che identifica il modello di VPS corrispondente alle [offerte VPS sul nostro sito](https://www.ovhcloud.com/it/vps).

##### **vCore**/**Memoria**/**Storage**

Le risorse correnti del VPS vengono mostrate qui e possono essere aggiornate separatamente cliccando sul pulsante corrispondente. Ti ricordiamo che gli upgrade sono limitati dal modello di VPS scelto e possono essere disponibili solo passando a una [gamma superiore](https://www.ovhcloud.com/it/vps).

#### IP

##### **IPv4**

L'indirizzo IPv4 pubblico principale del VPS viene configurato automaticamente al momento dell'installazione. Per maggiori informazioni sulla gestione degli IP, consulta la nostra guida [Configuring IP aliasing](/pages/bare_metal_cloud/virtual_private_servers/configuring-ip-aliasing).

##### **IPv6** / **Gateway**

In questa sezione è possibile visualizzare l'indirizzo IPv6 pubblico e l'indirizzo del gateway associato. che vengono associati automaticamente al VPS durante l’installazione. Per maggiori informazioni, consulta [questa guida](/pages/bare_metal_cloud/virtual_private_servers/configure-ipv6).

##### **DNS secondario**

Questa funzionalità è utile per ospitare i servizi DNS. La nostra guida [Configurare il DNS secondario di OVHcloud su un VPS](/pages/bare_metal_cloud/virtual_private_servers/adding-secondary-dns-on-vps) lo descrive in dettaglio.

#### Riepilogo delle opzioni 

Queste opzioni si riferiscono a servizi VPS aggiuntivi ordinabili dallo Spazio Cliente.

- L'opzione `Snapshot` ti permette di creare uno Snapshot manuale come unico punto di ripristino.
- L'opzione `Backup automatico` permette di conservare più Snapshot del VPS (esclusi i dischi aggiuntivi).
- L'opzione `Dischi aggiuntivi` permette di associare spazio di storage al VPS, ad esempio per salvare i dati di backup.

Tutte le informazioni sulle soluzioni di backup disponibili per il servizio sono disponibili nella [pagina relativa ai prodotti](https://www.ovhcloud.com/it/vps/options/) e nelle rispettive [guide](/products/bare-metal-cloud-virtual-private-servers-backups).

#### Abbonamento

In queste sezioni vengono fornite le informazioni più importanti relative alla fatturazione del servizio. Tutte le informazioni su questo argomento sono disponibili nella [documentazione corrispondente](/products/account-and-service-management-managing-billing-payments-and-services).

### Funzioni VPS disponibili nella scheda "Home page"

> [!warning]
>
> OVHcloud mette a disposizione i servizi la cui configurazione e gestione è di responsabilità dell’utente. È quindi vostra responsabilità assicurarvi che funzionino correttamente.
>
> Questa guida ti aiuta a eseguire le operazioni necessarie alla configurazione del tuo account. Tuttavia, in caso di difficoltà o dubbi relativamente ad amministrazione, utilizzo o implementazione dei servizi su un server, ti consigliamo di contattare un [fornitore di servizi specializzato](https://partner.ovhcloud.com/it/directory/) o contattare la [nostra Community](https://community.ovh.com/en/).
>

### Reinstallazione del VPS <a name="reinstallvps"></a>

Le reinstallazioni possono essere effettuate direttamente dallo Spazio Cliente. Clicca su `...`{.action} accanto a **OS/Distribuzione** e poi su `Reinstalla il tuo VPS`{.action}.

![VPSnewreinstallation](images/2023panel_01.png){.thumbnail}

Nella nuova finestra, seleziona un sistema operativo dall’elenco a discesa. Le opzioni proposte sono immagini compatibili [con un VPS OVHcloud](/pages/public_cloud/compute/image-life-cycle) e attive immediatamente dopo l'installazione.

Se una **chiave SSH** è stata precedentemente archiviata nello [Spazio Cliente OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.it/&ovhSubsidiary=it), è possibile selezionarne una da installare sul sistema. Per saperne di più, consulta la nostra guida [Creare e utilizzare le chiavi SSH](/pages/bare_metal_cloud/dedicated_servers/creating-ssh-keys-dedicated).

> [!primary]
>
> **Licenze**
>
> Alcuni sistemi operativi o piattaforme proprietarie, come Plesk o cPanel, richiedono licenze che generano spese aggiuntive. Le licenze possono essere gestite dallo Spazio Cliente: accedi alla sezione `Bare Metal Cloud`{.action} e clicca su `Licenze`{.action} nella barra di navigazione a sinistra.
>
> Per avere un sistema operativo **Windows** funzionante su un VPS, è necessario **selezionare nel processo di ordine**. Un VPS con un altro OS installato non può essere reinstallato con Windows nel modo descritto sopra.
>

Nello Spazio Cliente viene visualizzato un indicatore di stato dell’installazione. Ti ricordiamo che questo processo potrebbe richiedere fino a 30 minuti.

### Riavvio del VPS <a name="reboot-current-range"></a>

Potrebbe essere necessario riavviare il sistema per applicare configurazioni aggiornate o risolvere un problema. Se possibile, riavviare il software dall'interfaccia grafica del server (Windows, Plesk, ecc.) o dalla riga di comando:

```bash
sudo reboot
```

È comunque possibile effettuare un "riavvio hardware" in qualsiasi momento dallo [Spazio Cliente OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.it/&ovhSubsidiary=it). Nella scheda `Home`{.action}, clicca su `...`{.action} accanto a `Boot` nella sezione **Il tuo VPS**. Seleziona `Riavvia il tuo VPS`{.action} e clicca su `Conferma`{.action} nella finestra che appare.

![Riavvio](images/reboot-vps01.png){.thumbnail}

### Connessione al VPS (OS GNU/Linux)

Durante la prima installazione o la reinstallazione dal Pannello di controllo, viene creato automaticamente un utente con autorizzazioni elevate. Questo utente verrà nominato in base al sistema operativo, ad esempio "ubuntu" o "rocky".

A questo punto, riceverai un’email con il nome utente e la password necessari per accedere al tuo VPS in SSH. SSH è un protocollo di comunicazione sicuro, utilizzato per stabilire connessioni criptate verso un host remoto.

La maggior parte dei sistemi operativi desktop attuali dispone di un client **Open SSH** preinstallato. Le credenziali di accesso consentono quindi di stabilire rapidamente una connessione al VPS nell'applicazione da riga di comando appropriata (`Terminal`, `Command prompt`, `Powershell`, ecc...). Immettere il comando seguente:

```bash
ssh username@IPv4_VPS
```

Esempio:

```bash
ssh ubuntu@169.254.10.250
```

È inoltre possibile utilizzare qualsiasi applicazione di terze parti compatibile con **Open SSH**.

Una volta effettuato l’accesso, è possibile sostituire la password predefinita dell’utente corrente con una forte frase segreta utilizzando questo comando:


```bash
passwd
```

In una distribuzione GNU/Linux, **il prompt della password non mostrerà le voci della tastiera**.

Digita la password corrente e clicca su `Enter`{.action}. Digitare la nuova frase segreta e quindi ridigitarla al prompt successivo per confermarla.

```console
Changing password for ubuntu.
Current password:
New password: 
Retype new password: 
passwd: password updated successfully
```

> [!warning]
> 
> **Attivazione dell'account utente root**
>
> Non è necessario utilizzare l'account utente "root" per avviare l'amministrazione del server. Per utilizzare questo account, è necessario che sia stato abilitato nel sistema operativo del server. Inoltre, per motivi di sicurezza, le connessioni SSH con l’utente "root" sono **disattivate** di default.
> 
Se non diversamente specificato, tutte le operazioni di amministrazione descritte nella nostra documentazione possono essere effettuate dall’account utente predefinito, ovvero digitando `sudo` seguito dal relativo ordine. Per saperne di più su questo argomento, consulta la nostra guida su [Configurazione degli account utente e dell'accesso root su un server](/pages/bare_metal_cloud/dedicated_servers/changing_root_password_linux_ds).
>

**Di seguito sono riportati i passaggi consigliati**:

- Familiarizzare con le connessioni SSH consultando la nostra guida [Introduzione a SSH](/pages/bare_metal_cloud/dedicated_servers/ssh_introduction).
- Utilizza le chiavi SSH come metodo avanzato e più pratico per le connessioni remote: questa guida ti mostra come [creare e utilizzare le chiavi SSH](/pages/bare_metal_cloud/dedicated_servers/creating-ssh-keys-dedicated).
- Utilizza la nostra guida [Proteggere un VPS](/pages/bare_metal_cloud/virtual_private_servers/secure_your_vps) per proteggere il sistema da attacchi automatici di *brute force* e da altre minacce comuni.

> [!primary]
>
Ti ricordiamo che se hai selezionato una **distribuzione con applicazione** (Plesk, cPanel, Docker), le misure di sicurezza generiche potrebbero non essere applicabili al tuo sistema. Per maggiori informazioni, consulta le nostre guide [Iniziare a utilizzare le applicazioni preinstallate](/pages/bare_metal_cloud/virtual_private_servers/apps_first_steps) e [Distribuire cPanel su un VPS](/pages/bare_metal_cloud/virtual_private_servers/cpanel), oltre alla documentazione ufficiale del produttore.
>

### Accedi al tuo VPS Windows

Una volta installato il VPS Windows, riceverai un’email con il nome dell’utente predefinito `Windows user`.

A questo punto, è necessario completare l'installazione di Windows impostando la lingua di visualizzazione, il layout di tastiera e la password dell'amministratore.

Per farlo, utilizza la nostra console KVM: clicca sui `...`{.action} accanto al nome del tuo VPS nella sezione [Il tuo VPS](#yourvps) e seleziona `KVM`{.action}. Per maggiori informazioni su questo strumento, consulta la nostra [guida KVM](/pages/bare_metal_cloud/virtual_private_servers/secure_your_vps).

Per completare l’installazione di un VPS Windows via KVM, segui i passaggi descritti nella nostra guida [Configurare una nuova installazione di Windows Server](/pages/bare_metal_cloud/virtual_private_servers/windows_first_config).

Sul dispositivo Windows locale, è possibile utilizzare l'applicazione client `Remote Desktop Connection` per connettersi al VPS.

![windows remote](images/windows-connect-03.png){.thumbnail}

Inserisci l’indirizzo IPv4 del VPS, l’identificativo e la password. In genere viene visualizzato un messaggio di avviso che richiede di confermare la connessione a causa di un certificato sconosciuto. Fare clic su `Sì`{.action} per accedere.

È inoltre possibile utilizzare qualsiasi applicazione di terze parti compatibile con RDP. Questa condizione è necessaria se Windows non è installato nel dispositivo locale.

> [!primary]
>
In caso di problemi con questa procedura, verificare che sul dispositivo siano consentite connessioni remote (RDP) verificando le impostazioni di sistema, le regole firewall e le eventuali restrizioni di rete.
>

### Metti in sicurezza il tuo VPS

In qualità di amministratore del VPS, sei responsabile della sicurezza delle applicazioni e dei dati in esso ospitati.

Per maggiori informazioni sulla protezione del sistema, consulta la nostra guida [Proteggere un VPS](/pages/bare_metal_cloud/virtual_private_servers/secure_your_vps).

> [!primary]
>
Ti ricordiamo che se hai selezionato una **distribuzione con applicazione** (Plesk, cPanel, Docker), le misure di sicurezza generiche potrebbero non essere applicabili al tuo sistema. Per maggiori informazioni, consulta le nostre guide [Iniziare a utilizzare le applicazioni preinstallate](/pages/bare_metal_cloud/virtual_private_servers/apps_first_steps) e [Distribuire cPanel su un VPS](/pages/bare_metal_cloud/virtual_private_servers/cpanel), oltre alla documentazione ufficiale del produttore.
>

### Associa un dominio

Il passaggio del VPS sul Web avviene generalmente attraverso l'attribuzione di un dominio e la sua configurazione DNS. Per maggiori informazioni sulla gestione dei domini in OVHcloud, consulta la nostra guida [Modificare una zona DNS in OVHcloud](/pages/web_cloud/domains/dns_zone_edit).

### Proteggi un dominio con un certificato SSL

Una volta configurato il VPS, è utile proteggere anche il dominio e il sito Web. Per effettuare questa operazione è necessario disporre di un certificato SSL che consenta l’accesso a Internet del VPS tramite *HTTPS* anziché tramite *HTTP* non protetto.

Questo certificato SSL può essere installato manualmente, direttamente sul VPS. Consulta la documentazione ufficiale della tua distribuzione VPS.

Per un processo più automatizzato, OVHcloud propone anche la soluzione SSL Gateway. Per maggiori informazioni, consulta la [pagina relativa al prodotto](https://www.ovh.it/ssl-gateway/) o la nostra [guida](/products/web-cloud-ssl-gateway).

## Per saperne di più

[FAQ VPS](/pages/bare_metal_cloud/virtual_private_servers/vps-faq)

[Introduzione a SSH](/pages/bare_metal_cloud/dedicated_servers/ssh_introduction)

[Mettere in sicurezza un VPS](/pages/bare_metal_cloud/virtual_private_servers/secure_your_vps)

[Configurare una nuova installazione di Windows Server](/pages/bare_metal_cloud/virtual_private_servers/windows_first_config)

Contatta la nostra Community di utenti all’indirizzo <https://community.ovh.com/en/>.
