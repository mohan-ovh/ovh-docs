---
title: Accedere al database del tuo database server
slug: connessione-database-server-bdd
excerpt: Come connettersi al database
section: CloudDB
order: 3
---

> [!primary]
> Questa traduzione è stata generata automaticamente dal nostro partner SYSTRAN. I contenuti potrebbero presentare imprecisioni, ad esempio la nomenclatura dei pulsanti o alcuni dettagli tecnici. In caso di dubbi consigliamo di fare riferimento alla versione inglese o francese della guida. Per aiutarci a migliorare questa traduzione, utilizza il pulsante "Modifica" di questa pagina.
>

**Ultimo aggiornamento: 03/02/2022**

## Obiettivo

È possibile consultare il contenuto del tuo database tramite un'interfaccia. Per effettuare questa operazione, è possibile connettersi in diversi modi.

**Questa guida ti mostra come connettersi al database sul tuo database server.**

## Prerequisiti

- Disporre di una [soluzione Cloud Database](https://www.ovh.it/cloud-databases/){.external}
- Avere accesso allo [Spazio Cliente OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.it/&ovhSubsidiary=it){.external}

## Procedura

> [!primary]
>
> Ti ricordiamo che non esiste un accesso super utente "root".
> <br> I comandi SQL generici funzionano normalmente e i software HeidiSQL, SQuirreL SQL o Adminer sono pienamente compatibili.
> 

### Connettersi a un database MySQL o MariaDB 

> [!primary]
>
> MariaDB è un derivato di MySQL e i diversi comandi sono esattamente gli stessi per questi 2 tipi di database.
> 

####  Per phpMyAdmin OVHcloud 

Accedi allo [Spazio Cliente OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.it/&ovhSubsidiary=it){.external}. Clicca sulla scheda `Web Cloud` e poi su `Database`{.action}. Seleziona il nome del tuo database server.

Dalla scheda `Informazioni generali`, il link di accesso nel riquadro **"Amministrazione del database"** è disponibile nella sezione "Interfaccia utente".

![private-sql](images/private-sql-phpma01.png){.thumbnail}

Si aprirà la pagina di connessione di phpMyAdmin.

![private-sql](images/private-sql-phpma02.png){.thumbnail}

- **Server:** inserisci il nome host del tuo server visibile nella scheda `Informazioni generali`, nel riquadro **"Amministrazione del database"** con la voce "Nome host" nella parte **SQL**.
- **Utente:** inserisci il nome utente creato nella scheda `Utenti e diritti` del tuo database server.
- **Password:** inserisci la password associata all'utente
- **Porta:** inserisci la porta indicata nella scheda `Informazioni generali`, nel riquadro **"Amministrazione del database"** con la voce "Porta" nella parte **SQL**. 

Se la connessione avrà successo, comparirà la pagina successiva di phpMyAdmin.

![private-sql](images/private-sql-phpma03.png){.thumbnail}

> **In caso di errore #1045**
> 
> In caso di errore #1045, significa che le credenziali non sono corrette. È quindi necessario verificare il nome utente e/o la password.
> 
> **In caso di errore #2005**
> 
> In caso di errore #2005, ti consigliamo di verificare il nome del server e il suo corretto funzionamento.

#### Accedi al database al di fuori dello Spazio Cliente OVH

Per connetterti al tuo database, assicurati di recuperare queste informazioni:

- **Server:** l'hostname del tuo server è visibile nella scheda `Informazioni `generali del tuo server database, nel quadro **"Amministrazione del database"** con la voce "Nome host" nella parte **SQL**.
- **Utente:** il nome utente creato nella scheda `Utenti e diritti` del tuo database server.
- **Password:** la password associata all'utente
- **Porta:** la porta è visibile nella scheda `Informazioni `generali del tuo database server, nel quadro **"Amministrazione del database"** con la voce "Porta" della parte **SQL**.
- **Nome del database:** i database sono elencati nella scheda `Database` del tuo database server.

##### 1. Connessione online di comando

```bash
mysql --host=server --user=username --port=port --password=password database_name
```

##### 2. Connessione tramite script PHP


```php
1. <?php
2. $db = new PDO('mysql:host=host;port=port;dbname=dbname', 'username', 'password');
3. >
```

##### 3. Connessione tramite software (SQuirreL SQL)

> [!primary]
>
> Nel nostro esempio utilizziamo il software open source SQquirreL, ma altre interfacce come HeidiSQL o Adminer sono totalmente compatibili. 

- Lanciate SQuirreL SQL e cliccate su `Aliases`{.action}, poi su `+`{.action}

![launch SQuirreL SQL](images/1.png){.thumbnail}

- Completa i campi qui sotto e conferma con il pulsante `OK`{.action}:
    - **Name**: Scegli un nome
    - **Driver**: Scegli "MySQL Driver"
    - **URL**: Indica l'indirizzo del server e la porta nella forma jdbc:mysql://server:port
    - **User Name**: Inserisci il nome utente
    - **Password**: Indica la password

![config connection](images/2.png){.thumbnail}

- Conferma di nuovo con il pulsante `Connect`{.action}

![valid connection](images/3.png){.thumbnail}

Da questo momento sei connesso correttamente al tuo database:

![config connection](images/4.PNG){.thumbnail}


##### 4. Connessione via phpMyAdmin

È possibile utilizzare la propria interfaccia phpMyAdmin per esplorare il contenuto del database. installa phpMyAdmin sul tuo server o hosting Web. Durante l'installazione, assicurati di configurare correttamente le informazioni del tuo database server e del tuo database in modo che phpMyAdmin possa connettersi.



### Connettersi a un database PostgreSQL 


Per connetterti al tuo database, assicurati di recuperare queste informazioni:

- **Server:** l'hostname del tuo server è visibile nella scheda `Informazioni `generali del tuo server database, nel quadro **"Amministrazione del database"** con la voce "Nome host" nella parte **SQL**.
- **Utente:** il nome utente creato nella scheda `Utenti e diritti` del tuo database server.
- **Password:** la password associata all'utente
- **Porta:** la porta è visibile nella scheda `Informazioni `generali del tuo database server, nel quadro **"Amministrazione del database"** con la voce "Porta" della parte **SQL**.
- **Nome del database:** i database sono elencati nella scheda `Database` del tuo database server.

#### Connessione online di comando

```bash
psql —host=server —port=port —user=utente —password=password nome_database
```

#### Connessione tramite script PHP

```php
1. <?php
2. $myPDO = new PDO('pgsql:host=host;port=port;dbname=dbname', 'username', 'password');
3
```

#### Connessione tramite software (SQuirreL SQL)

> [!primary]
>
> Nel nostro esempio utilizziamo il software open source SQquirreL, ma altre interfacce come HeidiSQL o Adminer sono totalmente compatibili.

- Lanciate SQuirreL SQL e cliccate su `Aliases`{.action}, poi su `+`{.action}

![launch SQuirreL SQL](images/1.png){.thumbnail}

- Completa i campi qui sotto e conferma con il pulsante `OK`{.action}:
    - **Name**: Scegli un nome
    - **Driver**: Scegli "PostgreSQL"
    - **URL**: Indica l'indirizzo del server e la porta nella forma jdbc:postgresql://server:port/database
    - **User Name**: Inserisci il nome utente
    - **Password**: Indica la password

![config connection](images/2.png){.thumbnail}

- Conferma di nuovo con il pulsante `Connect`{.action}

![valid connection](images/3.png){.thumbnail}

Da questo momento sei connesso correttamente al tuo database:

![config connection](images/4.PNG){.thumbnail}

## Per saperne di più

Contatta la nostra Community di utenti all’indirizzo <https://community.ovh.com>.

