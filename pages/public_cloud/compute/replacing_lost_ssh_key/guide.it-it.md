---
title: Sostituisci la tua chiave SSH in caso di perdita
excerpt: Sostituisci la tua chiave SSH in caso di perdita
legacy_guide_number: g2069
updated: 2022-02-10
---

> [!primary]
> Questa traduzione è stata generata automaticamente dal nostro partner SYSTRAN. I contenuti potrebbero presentare imprecisioni, ad esempio la nomenclatura dei pulsanti o alcuni dettagli tecnici. In caso di dubbi consigliamo di fare riferimento alla versione inglese o francese della guida. Per aiutarci a migliorare questa traduzione, utilizza il pulsante "Contribuisci" di questa pagina.
>


## Obiettivo

In caso di perdita di chiave SSH, sia in seguito a reinstallazione di un dispositivo che in seguito ad altre operazioni, è possibile che non sia più possibile connettersi alla tua istanza se non hai configurato alcun metodo alternativo per connetterti alla tua istanza.

Per recuperare l'accesso, abbiamo messo a tua disposizione una [modalità Rescue](/pages/public_cloud/compute/put_an_instance_in_rescue_mode) che ti permette di connetterti tramite una password e modificare i tuoi file.

**Questa guida ti mostra come configurare il file *authorized_keys* dell'utente *admin* per poter aggiungere una nuova chiave SSH per recuperare l'accesso alla tua istanza.**

## Prerequisiti

- Disporre di una [Istanza Public Cloud](https://www.ovhcloud.com/it/public-cloud/) nel tuo account OVHcloud
- Avere accesso alla tua istanza via SSH in [modalità Rescue](/pages/public_cloud/compute/put_an_instance_in_rescue_mode)
- Creare una chiave SSH

## Procedura

> [!primary]
>
Per salvare una chiave SSH nello Spazio Cliente OVHcloud, ti consigliamo di utilizzare la cifratura RSA o ECDSA. ED25519 non è attualmente supportato.
>

Dopo aver montato il disco della tua istanza in [modalità Rescue](/pages/public_cloud/compute/put_an_instance_in_rescue_mode#accedi-ai-tuoi-dati), sarai in grado di accedere a tutti i tuoi file.

Il file contenente le tue chiavi SSH è il file:

```sh
/mnt/home/USER_NAME/.ssh/authorized_keys
```

Per aggiungere la nuova chiave SSH, è sufficiente modificare questo file e aggiungere la nuova chiave:

```sh
sudo vim /mnt/home/USER_NAME/.ssh/authorized_keys
ssh-rsa 1111111111122222222222333333333333444444444555555555556666666666
777777777778888888888999999900000000000000000000000000== old@sshkey
ssh-rsa AAAAAAAAABBBBBBBBBBBCCCCCCCCCCCCCCCCDDDDDDDDDDDDDDDDDDDEEEEEEEEE
EEFFFFFFFFFFFFFGGGGGGGGGGGGGhhhhhhhhhhhhhhhhhhhhhhhhhh== new@sshkey
```

### Modifica la chiave SSH utente predefinita

Per modificare la chiave SSH del tuo utente predefinito, dovrai semplicemente collegarti alla cartella personale del tuo utente. Ad esempio, per l'utente admin, il file da trovare sarà nella cartella seguente:

```sh
/home/admin/.ssh/authorized_keys
```

Per un'istanza con Ubuntu, l'utente di default viene pubblicato. Il file sarà quindi nella cartella seguente:

```sh
/home/ubuntu/.ssh/authorized_keys
```

### Modifica la password utente predefinita

Puoi anche modificare la password dell'utente di default utilizzando la modalità Rescue e i comandi seguenti (nel caso in cui l'utente sia admin):

La directory di root viene modificata per posizionarsi direttamente sul disco dell'istanza:

> [!primary]
>
Nell'esempio qui sotto, abbiamo utilizzato vdb1 come nome del disco del server e montato come punto di mount.
>

```sh
/home/admin# mount /dev/vdb1 /mnt/
/home/admin# chroot /mnt/
```

Modifica la password amministratore:

```sh
passwd admin
```

Una volta effettuata la modifica e salvata, è sufficiente riavviare la tua istanza sul disco per poter connetterti alla tua istanza con la nuova chiave SSH.

## Per saperne di più

[Devenire utente root e selezionare una password](/pages/public_cloud/compute/become_root_and_change_password)

Contatta la nostra Community di utenti all’indirizzo <https://community.ovh.com/en/>.
