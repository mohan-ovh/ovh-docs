---
title: 'Utilizzare l’interfaccia sicura'
excerpt: 'Come confermare le operazioni sensibili tramite l’interfaccia sicura su infrastrutture HDS e PCI-DSS'
updated: 2022-10-12
---

**Ultimo aggiornamento: 12/10/2022**

## Obiettivo

L’interfaccia sicura è un sistema che permette di confermare le operazioni sensibili (come modificare la password o aggiungere nuovi account) effettuate da altri utenti o da terzi sui servizi Hosted Private Cloud con certificazione HDS o PCI-DSS.

**Questa guida ti mostra come utilizzare l’interfaccia per convalidare questo tipo di operazioni.**

## Prerequisiti

- Disporre di un’infrastruttura **Private Cloud** con l’opzione di [sicurezza avanzata](https://www.ovhcloud.com/it/enterprise/products/hosted-private-cloud/safety-compliance/sddc/) (inclusa nei servizi PCI-DSS e HDS) Questo permesso consente la convalida.
- ad esempio https://pcc-xxx-xxx-xxx-xxx.ovh.com/secure/ (facendo attenzione a non dimenticare “/” alla fine dell’indirizzo).

## Procedura

La conferma delle operazioni sensibili tramite l’interfaccia sicura è possibile esclusivamente per gli utenti che dispongono del permesso **token validator**. Questo privilegio, indispensabile all’attivazione dell’opzione **security advanced**,  

viene attribuito di default all’utente “admin” e può essere assegnato direttamente dallo Spazio Cliente anche ad altri utilizzatori.  In caso di necessità, consulta la nostra guida [Introduzione allo Spazio Cliente Private Cloud OVHcloud](/pages/cloud/private-cloud/manager_ovh_private_cloud).

Dall’interfaccia sicura è possibile eseguire tre diverse azioni. Prosegui nella lettura di questa guida in base all’operazione che vuoi effettuare: 

- [Confermare un’operazione tramite token](./#confermare-unoperazione-tramite-token)
- [Modifica la password associata a un utente](./#modificare-la-password-associata-a-un-utente) 
- [Reimpostare una password](./#reimpostare-una-password)

### Confermare un’operazione tramite token

Una volta ricevuto il token per SMS, è necessario inserirlo nell’interfaccia sicura per eseguire l’operazione in attesa.

> [!warning]
>
> Il token ha una validità di 15 minuti e il suo mancato utilizzo comporta l’annullamento dell’operazione.
>
> Per le manutenzioni l’intervento verrà riproposto successivamente in modo automatico, negli altri casi sarà invece l’utente a dover pianificare nuovamente l’operazione. 
>

Ecco un esempio di SMS: 

![Premier SMS](images/SMS1.png){.thumbnail}

Questo messaggio contiene: 

- il **token validator** che ha ricevuto l’SMS  (questa informazione potrebbe rivelarsi utile per la gestione dei token da confermare nel caso in cui l’utente abbia inserito il proprio numero di telefono in diversi account)
- il nome dell’operazione che richiede la conferma
- l’ID dell'operazione
- il token
- un link che consente di confermare l’operazione (attenzione: se l’indirizzo IP della rete a cui è connesso il telefono [non è autorizzato](/pages/cloud/private-cloud/manager_ovh_private_cloud#sicurezza), la pagina non verrà visualizzata).

Per confermare l’operazione, clicca sul link presente nell’SMS ricevuto  e seleziona `Operation Validation`{.action}.

![Conferma dell’operazione](images/operationValidation.png){.thumbnail}

Si aprirà una nuova finestra, a cui potranno autenticarsi soltanto gli utenti che dispongono del permesso **token validator**.

Predisponi l’operazione inserendone l’ID nel campo “Operation id” e clicca su `Load operation`{.action}. Digita il token ricevuto via SMS e clicca sul pulsante `Confirm operation`{.action}.

![token operation](images/operationIdAndToken.png){.thumbnail}

A questo punto gli utenti che dispongono del permesso **token validator** riceveranno un SMS di questo tipo:

![Secondo SMS](images/SMS2.png){.thumbnail}

Questo messaggio contiene: 

- l’utente con il permesso **token validator** che ha ricevuto l’SMS
- il nome e l’ID dell’operazione
- l’utente con il permesso **token validator** che ha confermato l’operazione

### Modificare la password associata a un utente 

La modifica della password può essere effettuata da qualsiasi utente, indipendentemente dal fatto che disponga o meno del permesso **token validator**.  Per poter procedere con questa operazione è però necessario che l’utente sia in possesso della password corrente.

> [!primary]
>
> Nel caso in cui l’utente non disponga più della password, dovrà richiedere a un altro utente con permesso **token validator** attivo di eseguire la modifica per suo conto tramite la procedura di [reimpostazione della password](./#reimpostare-una-password). 
> 

Per modificare la password associata a un utente, accedi all’interfaccia sicura (ad esempio, `https://pcc-xxx-xxx-xxx-xxx.ovh.com/secure/`) e clicca su `Change password`{.action}.

![Modifica la password](images/changePassword.png){.thumbnail}

Nella nuova pagina seleziona il nome utente e definisci la nuova password.

Gli utenti  con permesso [token validator](./#confermare-un-operazione-tramite-token) riceveranno un token per **confermare l’operazione**.

![Definisci la password](images/defineNewPassword.png){.thumbnail}

### Reimpostare una password

Questa procedura è valida soltanto per gli utenti che dispongono del diritto **token validator**. Un utente che non dispone di questa autorizzazione otterrà un errore 400.

> [!primary]
>
> Se un utente senza permesso **token validator** non dispone più della sua password, dovrà chiederne la reimpostazione a un utente che lo possiede.
> 

Per reimpostare la password, accedi all’interfaccia sicura (ad esempio, `https://pcc-xxx-xxx-xxx-xxx.ovh.com/secure/`) e clicca sul pulsante `Password lost`{.action}.

![Password dimenticata](images/passwordLost.png){.thumbnail}

Un messaggio ti indicherà che, per continuare, è necessario essere in grado di ricevere SMS. Se questo è il tuo caso, completa le informazioni richieste (incluso il nome utente associato alla password di cui stai richiedendo la reimpostazione) e clicca su`Next step`{.action}.

![Informazioni utente](images/infoUser.png){.thumbnail}

A questo punto inserisci i due token ricevuti via SMS e posta elettronica e definisci la nuova password.

> [!primary]
>
> Se la procedura di reimpostazione viene effettuata per conto di un altro utente, chi ha eseguito l’operazione dovrà trasmettere la nuova password. È inoltre preferibile che l’utente che la riceve la [modifichi appena possibile](./#modificare-la-password-associata-a-un-utente).
> 

![Token e password](images/tokenAndPassword.png){.thumbnail}

## Per saperne di più

Contatta la nostra Community di utenti all’indirizzo <https://community.ovh.com/en/>.
