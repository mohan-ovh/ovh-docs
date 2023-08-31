---
title: 'Riavvia la tua istanza in modalità di ripristino (Rescue mode)'
excerpt: 'Come riavviare un’istanza in modalità di ripristino (Rescue mode)'
legacy_guide_number: g2029
updated: 2023-01-04
---

## Obiettivo

Se non riesci ad accedere alla tua istanza a causa di una configurazione non corretta o perché hai smarrito la tua chiave SSH, puoi accedere ai tuoi dati e correggere i file di configurazione attivando la modalità di ripristino. 

**Questa guida ti mostra come riavviare la tua istanza in modalità Rescue**

## Prerequisiti

* Aver creato un’istanza [Public Cloud](https://www.ovhcloud.com/it/public-cloud/){.external} nel tuo account OVHcloud
* Avere accesso allo [Spazio Cliente OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.it/&ovhSubsidiary=it){.external}
* Avere accesso all’istanza via SSH con l’utente root

## Procedura

> [!alert]
>
> Ad oggi, la modalità Rescue per le istanze Metal non è disponibile nello Spazio Cliente OVHcloud. Per maggiori informazioni, consulta la guida dedicata al [Rescue mode per le istanze Metal](/pages/public_cloud/compute/rescue_mode_metal_instance).

### Attiva la modalità di ripristino

Per prima cosa, accedi al tuo [Spazio Cliente OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.it/&ovhSubsidiary=it){.external} e clicca sul menu `Public Cloud`{.action}.

Poi, seleziona il tuo progetto Public Cloud dal menu a sinistra e vai su Istanze.

Quindi, clicca sui tre puntini a destra dell’istanza e seleziona `Riavvia in modalità Rescue`{.action}

![Spazio Cliente](images/rescue2022.png){.thumbnail}

A questo punto visualizzi la finestra di dialogo “Riavvia in modalità Rescue”. Clicca sul menu a tendina per selezionare la distribuzione Linux che vuoi utilizzare in modalità Rescue e poi clicca sul pulsante `Riavvia`{.action}.

![Spazio Cliente](images/rescue2.png){.thumbnail}

Una volta riavviato il Rescue mode, una casella di informazioni mostrerà i metodi di accesso disponibili. La tua **password della modalità Rescue** temporanea verrà visualizzata solo nella console VNC. Clicca sull'istanza nella tabella e poi accedi alla scheda `Console VNC`{.action} per recuperarla.

![Spazio Cliente](images/rescuedata.png){.thumbnail}

### Accedi ai tuoi dati

In modalità Rescue, i dati della tua istanza sono visibili come un disco aggiuntivo.  Per potervi accedere, è sufficiente configurare il disco seguendo questa procedura:

Accedi alla tua istanza via SSH Una volta connesso, verifica i dischi disponibili:

```
root@instance:/home/admin# lsblk

NAME MAJ:MIN RM SIZE RO TYPE MOUNTPOINT
vda 253:0 0 1G 0 disk
└─vda1 253:1 0 1023M 0 part /
vdb 253:16 0 10G 0 disk
└─vdb1 253:17 0 10G 0 part
```

monta la partizione:

```
root@instance:/home/admin# mount /dev/vdb1 /mnt
```

A questo punto i tuoi dati sono accessibili nella cartella /mnt.

### Disattiva la modalità Rescue

Una volta completate queste operazioni, è possibile disattivare la modalità Rescue riavviando normalmente la tua istanza. Per farlo, clicca sulla freccia verso il basso e seleziona `Esci dalla modalità Rescue`{.action}.

![Spazio Cliente](images/rescueexit2022.png){.thumbnail}

> [!warning]
> Se il pulsante `Esci dalla modalità Rescue`{.action} non compare in modalità Rescue, consigliamo di aggiornare la scheda.
>

### Attiva la modalità Rescue con le API OpenStack

Per riavviare la tua istanza in Rescue mode utilizzando le API OpenStack, esegui questo comando:

```
# root@server:~# nova rescue INSTANCE_ID
```

Per uscire dalla modalità Rescue, esegui questo comando:

```
# root@server:~# nova rescue INSTANCE_ID
```

## Per saperne di più 

Contatta la nostra Community di utenti all’indirizzo <https://community.ovh.com/en/>.