---
title: Come utilizzare PostgreSQL
excerpt: Guida all'utilizzo dei tuoi database
updated: 2023-02-15
---

**Ultimo aggiornamento: 15/02/2023**

Vuoi utilizzare PostgreSQL? Scopri come creare e gestire i tuoi database con la massima semplicità!


## Introduzione

### Prerequisiti

- Un'istanza Web Cloud Databases attiva
- Aver consultato [la guida all’utilizzo di Web Cloud Databases](/pages/web/clouddb/starting_with_clouddb)

### Cose un database PostgreSQL?
PostgreSQL è un modello di database relazionale a oggetti (ORDBMS). È un sistema solido ed estendibile, in grado di gestire con la massima affidabilità un grande volume di dati. Dispone anche di una Community open source molto attiva.


## Connettiti al database


> [!primary]
>
> Ricordiamo che questa offerta non dà accesso all’host ma ai database ospitati su di esso. È possibile utilizzare tutti i comandi SQL generici e i software come HeidiSQL o SQuirreL SQL sono totalmente compatibili.
> 

Per accedere al tuo database, sono necessarie queste informazioni:

- indirizzo della tua istanza
- porta
- nome utente
- password
- nome del database

Questi dati sono disponibili nella sezione Web del tuo [Spazio Cliente OVHcloud](https://www.ovh.com/manager/web/){.external}.

Se necessario, consulta la guida: [Inziare a utilizzare Web Cloud Databases](/it/clouddb/starting_with_clouddb/guide.it-it.md){.ref}


### Connessione da riga di comando

```bash
psql --host=server --port=porta --user=utente --password=password nome_database
```


### Connessione con script PHP

```php
1. <?php
2. $myPDO = new PDO('pgsql:host=host;port=porta;dbname= nome_database', ' utente', 'password');
3. ?>
```


### Connessione da software (SQuirreL SQL)
- Avvia SQuirreL SQL, clicca su `Aliases`{.action} e poi su `+`{.action}


![launch SQuirreL SQL](images/1.PNG){.thumbnail}

- Completa i campi qui sotto e clicca su `OK`{.action} per confermare:
    - **Name**: scegli un nome
    - **Driver**: scegli "PostgreSQL"
    - **URL**: inserisci l’indirizzo del server e la porta in formato jdbc:postgresql://server:porta/nome_database
    - **User Name**: inserisci il nome utente
    - **Password**: inserisci la password


![config connection](images/2.PNG){.thumbnail}

- Clicca su `Connect`{.action} per confermare


![valid connection](images/3.PNG){.thumbnail}

A questo punto, sei connesso al tuo database:


![config connection](images/4.PNG){.thumbnail}


### Connessione con phpPgAdmin
*Presto disponibile in un’altra guida.*


## Esporta un database PostgreSQL

### Esportare il tuo database da riga di comando

```bash
pg_dump --host=server --port=porta --user=utente --password=password nome_database > nome_database.sql
```


## Importa un database PostgreSQL

### Importare il tuo database da riga di comando

```bash
psql --host=server --port=porta --user=utemte --password=password nome_database < nome_database.sql
```

## Per saperne di più

Per prestazioni specializzate (referenziamento, sviluppo, ecc...), contatta i [partner OVHcloud](https://partner.ovhcloud.com/it/).

Per usufruire di un supporto per l'utilizzo e la configurazione delle soluzioni OVHcloud, è possibile consultare le nostre soluzioni [offerte di supporto](https://www.ovhcloud.com/it/support-levels/).

Contatta la nostra Community di utenti all'indirizzo <https://community.ovh.com>.