---
title: Installare i moduli in 1 click OVHcloud
excerpt: Come creare il tuo sito utilizzando i moduli in 1 click
slug: hosting_condiviso_guida_ai_moduli_degli_hosting_condivisi
section: CMS
order: 01
---

**Ultimo aggiornamento: 31/01/2023**

> [!primary]
> Questa traduzione è stata generata automaticamente dal nostro partner SYSTRAN. I contenuti potrebbero presentare imprecisioni, ad esempio la nomenclatura dei pulsanti o alcuni dettagli tecnici. In caso di dubbi consigliamo di fare riferimento alla versione inglese o francese della guida. Per aiutarci a migliorare questa traduzione, utilizza il pulsante "Modifica" di questa pagina.
>

## Obiettivo

I moduli in 1 click permettono di creare un sito Web in modo semplice e veloce, anche senza possedere competenze tecniche specifiche, grazie all’utilizzo dei CMS più diffusi: WordPress, PrestaShop, Drupal e Joomla!.

**Questa guida ti mostra come utilizzare i moduli in 1 click di OVHcloud per mettere online il tuo sito Web.**

## Prerequisiti

- Disporre di una soluzione di [hosting Web](https://www.ovhcloud.com/it/web-hosting/){.external} attiva
- Avere accesso allo [Spazio Cliente OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.it/&ovhSubsidiary=it){.external}
- Utilizzare [una versione di PHP compatibile](https://docs.ovh.com/it/hosting/configura_php_sul_tuo_hosting_web_condiviso_2014_ovh/) sul tuo hosting Web.
- Aver [configurato correttamente il file.ovhconfig](https://docs.ovh.com/it/hosting/configurare-file-ovhconfig/)
- La directory in cui verrà installato il tuo modulo deve essere vuota o al momento inesistente.
- Aver impostato come multisito il dominio (ed eventualmente il sottodominio) che verrà utilizzato per il sito Web

## Procedura

### Scegli il CMS più adatto alle tue esigenze

Un CMS (Content Management System) consente di progettare un sito Web tramite un'interfaccia intuitiva e di semplice utilizzo. In base al tipo di progetto da realizzare è possibile scegliere tra diverse opzioni, per usufruire di una struttura pronta all’uso e personalizzabile (tema, contenuti, ecc...).

Con i moduli in 1 click di OVHcloud sono disponibili 4 CMS.  Se hai già scelto il CMS da installare, prosegui nella lettura di questa guida. In caso contrario, la nostra [pagina comparativa dei CMS](https://www.ovhcloud.com/it/web-hosting/uc-cms-comparison/){.external} potrebbe esserti di aiuto.

Se il CMS che hai scelto non è presente fra le opzioni proposte da OVHcloud, potrai installarlo manualmente nel tuo spazio di hosting, se compatibile con il piano attivato (per visualizzare le nostre offerte, [clicca qui](https://www.ovhcloud.com/it/web-hosting/){.external}).

![Logo dei CMS](images/CMS_logo.png){.thumbnail}

### Accedi alla pagina di gestione dei moduli in 1 click

Accedi allo [Spazio Cliente OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.it/&ovhSubsidiary=it) e seleziona `Web Cloud`{.action}. e seleziona il tuo servizio nella sezione `Hosting`{.action}. Clicca sulla scheda `CMS in 1 click`{.action} per visualizzare i moduli in uso, gestirli e installarne di nuovi.

![Accesso alla sezione Moduli in 1 click](images/access_to_the_1_click_modules_section.png){.thumbnail}

### Aggiungi un modulo

Per avviare l’installazione di un nuovo CMS, clicca sul pulsante `Aggiungi un modulo`{.action}.

Si apre una finestra da cui è possibile selezionare l’applicazione e scegliere il dominio su cui installare il tuo sito:

![Scelta del modulo](images/add_a_module.png){.thumbnail}

Se il dominio non è presente nella lista, seleziona la scheda `Multisito`{.action} per aggiungerlo e ripeti l’operazione.

Per maggiori informazioni, consulta la guida [Ospitare più siti su uno stesso hosting](https://docs.ovh.com/it/hosting/configurare-un-multisito-su-un-hosting-web/){.external}.

Una volta selezionato il dominio, scegli se effettuare un'installazione base o avanzata:

- l’installazione base, impostata di default, è la più semplice e veloce: provvediamo a installare il CMS e ti comunichiamo le credenziali necessarie per amministrarlo 
- l'installazione avanzata ti permette invece di personalizzare la configurazione inserendo alcune informazioni indispensabili per il corretto funzionamento del CMS sul tuo database: dati di connessione, directory di installazione, impostazione della lingua, nome e password amministratore, ecc…

#### Installazione base di un modulo

Assicurati che la casella `Installazione avanzata`{.action} non sia selezionata e clicca su `Installa`{.action}.

> [!warning]
>
> Affinché l’operazione vada a buon fine, è necessario che la directory di installazione sia vuota e che sia disponibile un database.
> 

![Installazione base di un modulo](images/choose_installation.png){.thumbnail}

Una volta completata l'installazione, riceverai un'email con le informazioni necessarie per accedere all'interfaccia di gestione del CMS. Per personalizzare il sito, accedi alla pagina.

#### Installazione avanzata di un modulo

Assicurati che la casella `Installazione avanzata`{.action} sia selezionata e clicca su `Continua`{.action}:

![Installazione avanzata di un modulo](images/advanced_installation.png){.thumbnail}

##### Scegli il database

A questo punto, inserisci i dati di accesso al tuo database. Esistono diverse possibilità:

- se il database è già creato sul tuo hosting, selezionalo dalla lista e inserisci le informazioni richieste
- se il database non è ancora stato creato sul tuo hosting, segui le indicazioni per crearlo, poi selezionalo dalla lista e inserisci le informazioni richieste
- se il database è stato creato sulla tua istanza CloudDB, selezionalo `Database esterno al tuo hosting Web`{.action} nella lista e inserisci le informazioni richieste. L'istanza e lo spazio di hosting devono essere ospitati nello stesso datacenter
- se il database è stato creato su un altro hosting Web OVHcloud, selezionalo `Database esterno al tuo hosting Web`{.action} nella lista e inserisci le informazioni richieste. Il database e lo spazio di hosting devono essere ospitati nello stesso datacenter

Una volta inseriti tutti i dati, clicca su `Continua`{.action}.

> [!warning]
>
> Se le informazioni fornite non sono corrette, il processo di installazione non verrà completato. Per evitare questo problema ti consigliamo di testare la connessione al tuo database prima di effettuare l’operazione.
> 

![Database per l'installazione avanzata](images/advanced_installation_database.png){.thumbnail}

##### Configura il modulo

Inserisci le informazioni richieste:

- *Nome dell'amministratore*: l'identificativo per accedere all'interfaccia di gestione del tuo CMS
- *Password*: la password per accedere all'interfaccia di gestione del tuo CMS
- *Dominio*: il dominio su cui verrà installato il sito. Per maggiori informazioni, consulta la guida [Ospitare più siti su uno stesso hosting](https://docs.ovh.com/it/hosting/configurare-un-multisito-su-un-hosting-web/).
- *Lingua*: la lingua di installazione del CMS
- *Percorso di installazione*: questo campo viene compilato automaticamente quando si seleziona il dominio, ma è possibile completarlo aggiungendovi sottocartelle

Una volta inserite tutte le informazioni, clicca su `Continua`{.action}.

> [!warning]
>
> Affinché l’operazione vada a buon fine è necessario che il percorso di installazione inserito non contenga alcun file.
> 

![Configurazione del modulo per installazione avanzata](images/advanced_installation_configuration.png){.thumbnail}

##### Conferma l'installazione

Verifica la correttezza delle informazioni e clicca su `Conferma`{.action}:

![Conferma dell’installazione in modalità avanzata](images/advanced_installation_summary.png){.thumbnail}

### Personalizza il tuo sito

Se l’operazione è andata a buon fine, ricevi un’email di conferma della corretta installazione del modulo. A questo punto, potrai accedere all’interfaccia di gestione per modificare il tema del tuo sito Web e pubblicare i primi contenuti.

Per maggiori informazioni sulle funzionalità disponibili ti consigliamo di consultare la pagina ufficiale del tuo CMS, in cui potrai trovare tutta la documentazione necessaria per realizzare il tuo progetto.

|CMS|Documentazione Ufficiale|
|---|---|
|WordPress|[Primi passi con WordPress](https://codex.wordpress.org/it:Primi_passi_con_WordPress){.external}|
|PrestaShop|[Guida introduttiva di PrestaShop](http://doc.prestashop.com/display/PS17/Guida+introduttiva+di+PrestaShop+1.7){.external}|
|Joomla!|[Documentazione Joomla!](https://docs.joomla.org/Joomla_info_page/it-IT){.external}|
|Drupal|[Documentazione Drupal](http://www.drupal.it/home-documentazione){.external}|

## Per saperne di più

[Scegli il CMS per il tuo sito Web](https://www.ovhcloud.com/it/web-hosting/uc-cms-comparison/){.external}

[Ospitare più siti su uno stesso hosting](https://docs.ovh.com/it/hosting/configurare-un-multisito-su-un-hosting-web/){.external}

[Gestire un database da un hosting condiviso](https://docs.ovh.com/it/hosting/gestisci_un_database_dal_tuo_hosting_condiviso/){.external}

[Gestire il vostro CMS](https://docs.ovh.com/it/hosting/1-click-module-management/)

[Disinstallare il tuo CMS](https://docs.ovh.com/it/hosting/1-click-module-management/#step-3-elimina-il-tuo-modulo)

Scopri la nostra soluzione [Cloud Database](https://www.ovh.it/cloud/cloud-databases/){.external}

Per prestazioni specializzate (referenziamento, sviluppo, ecc...), contatta i [partner OVHcloud](https://partner.ovhcloud.com/it/).

Per usufruire di un supporto per l'utilizzo e la configurazione delle soluzioni OVHcloud, è possibile consultare le nostre soluzioni [offerte di supporto](https://www.ovhcloud.com/it/support-levels/).

Contatta la nostra Community di utenti all'indirizzo <https://community.ovh.com/en/>.
