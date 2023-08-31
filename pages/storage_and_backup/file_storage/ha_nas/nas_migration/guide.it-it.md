---
title: Migrazione di dati da un NAS-HA verso un altro tramite NFS
excerpt: Questa guida ti mostra come migrare i dati da un NAS-HA a un altro tramite una condivisione NFS.
updated: 2021-02-09
---

> [!primary]
> Questa traduzione è stata generata automaticamente dal nostro partner SYSTRAN. I contenuti potrebbero presentare imprecisioni, ad esempio la nomenclatura dei pulsanti o alcuni dettagli tecnici. In caso di dubbi consigliamo di fare riferimento alla versione inglese o francese della guida. Per aiutarci a migliorare questa traduzione, utilizza il pulsante "Contribuisci" di questa pagina.
>

## Obiettivo

Questa guida ti mostra come trasferire i dati da un NAS-HA a un altro. 

## Prerequisiti

Per effettuare il trasferimento dei tuoi dati, è necessario:

- Un NAS-HA OVHcloud
- Una distribuzione compatibile con NFS
- Aver configurato il tuo NAS-HA seguendo la guida per [montare il tuo NAS-HA tramite una condivisione NFS](/pages/storage_and_backup/file_storage/ha_nas/nas_nfs){.external}.

## Procedura

Compatibilità: Debian 6/7/8 e Ubuntu 12/13/14

Per trasferire i tuoi dati, utilizzeremo il comando `rsync`. Per trasferire i tuoi dati è possibile utilizzare diverse soluzioni. Puoi usarne una invece che un'altra.

L'esempio mostrato qui sotto permette di trasferire i tuoi dati da un punto di mount Source a un punto di mount di Destination.

```sh
rsync -Pva /mnt/SrcNas /mnt/DstNas
```

|Argomento|Descrizione|
|---|---|
|SrcNas|Punto di mount sorgente|
|DstNas|Punto di mount di destinazione|

> [!alert]
>
> Attenzione: se aggiungi altre opzioni a rsync, queste potrebbero non essere compatibili con il sistema di diritti e permessi dei NAS-HA.
>

## Per saperne di più

Se avete bisogno di formazione o di assistenza tecnica per implementare le nostre soluzioni, contattate il vostro rappresentante o cliccate su [questo link](https://www.ovhcloud.com/it/professional-services/) per ottenere un preventivo e richiedere un'analisi personalizzata del vostro progetto da parte dei nostri esperti del team Professional Services.

Contatta la nostra Community di utenti all’indirizzo [https://community.ovh.com/en/](https://community.ovh.com/en/){.external}.