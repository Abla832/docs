---
title: 'Iniziare a utilizzare un VPS'
excerpt: 'Come eseguire le prime operazioni su un VPS'
slug: iniziare-a-utilizzare-vps
section: 'Per iniziare'
order: 1
---

**Ultimo aggiornamento: 21/12/2020**
 
## Obiettivo

Un Virtual Private Server (VPS) è un server dedicato virtualizzato. A differenza di un hosting Web, la cui gestione tecnica è affidata a OVHcloud, per un VPS l’amministrazione è sotto la tua completa responsabilità.

**Questa guida ti mostra le operazioni di base da effettuare sul tuo server virtuale appena consegnato e installato.**


> [!warning]
>
> OVHcloud mette a disposizione i server, ma non è autorizzata ad accedervi e non si occupa quindi della loro amministrazione. Garantire quotidianamente la gestione software e la sicurezza di queste macchine è quindi responsabilità dell’utente. Questa guida ti aiuta a muovere i primi passi nell’utilizzo del tuo VPS. Tuttavia, in caso di difficoltà o dubbi relativi ad amministrazione e sicurezza, ti consigliamo di contattare un fornitore specializzato. Per maggiori informazioni consulta la sezione “Per saperne di più” di questa guida.
> 


## Prerequisiti

- Aver ordinato un VPS sul [sito OVHcloud](https://www.ovhcloud.com/it/vps/){.external}. 
- Avere accesso allo [Spazio Cliente OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.it/&ovhSubsidiary=it){.external}
- Avere a disposizione le credenziali di accesso ricevute via email dopo l’installazione

## Procedura

Per visualizzare le informazioni relative al tuo VPS, accedi al tuo [Spazio Cliente OVHcloud](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.it/&ovhSubsidiary=it){.external} e, nella colonna di sinistra, clicca su `Bare Metal Cloud`{.action} e poi seleziona il tuo servizio sotto la voce `VPS`{.action}. 

Questa dashboard contiene informazioni importanti sul tuo servizio e ti consente di effettuare le operazioni di base. Comparirà in modo diverso a seconda della gamma del tuo VPS. 

- L'indirizzo di riferimento inizia sempre con *vpsXXXX.ovh.net* (dove le*X*sono una serie di cifre). 
- Se gestisci un VPS meno recente, noterai che il suo indirizzo di riferimento è strutturato diversamente: *vpsXXXX.ovh.net* (dove le*X*sono una serie di numeri). 

Per l’attuale gamma di VPS, prosegui nella lettura di questa guida, alla sezione: **Iniziare a utilizzare un VPS (gamma attuale)**. 

Per un modello VPS meno recente, prosegui nella lettura di questa guida: [Iniziare a utilizzare un VPS (gamma meno recente)](./#iniziare-a-utilizzare-un-vps-gamma-meno-recente_1)

### Iniziare a utilizzare un VPS (gamma attuale)

#### Accesso al tuo VPS (gamma attuale)

Durante l’installazione (o la reinstallazione) del VPS dal tuo Spazio Cliente, verrà creato un nuovo utente con tutti i privilegi e riceverai un’email con le relative credenziali di accesso.
Il nome utente sarà generato in base al sistema operativo in uso, ad esempio “ubuntu” o “debian”. 

Accedi al tuo VPS in SSH inserendo nome utente e password. Il protocollo SSH ti garantisce una connessione totalmente sicura. Per saperne di più, consulta [la nostra guida d’introduzione a SSH per i server dedicati OVHcloud](../../dedicated/introduzione-ssh/). Questo tipo di accesso viene effettuato su Linux e MAC tramite un terminale e, con Windows, utilizzando un software di terze parti (ad esempio PuTTy).

Se utilizzi PuTTy, avvia l’applicazione e inserisci il nome del server o l’indirizzo IPv4 corrispondente per stabilire una connessione. Una volta inseriti nome utente e password, potrai accedere all’interfaccia online di comando (CLI).

![utilizzo putty](images/putty1.png){.thumbnail}

Una volta avviato il terminale, accedi al tuo VPS digitando il seguente comando con le informazioni fornite nell’email  (nome utente e indirizzo IPv4):

```sh
ssh nome_utente@IPv4_del_tuo_VPS
```

Dato che hai effettuato l’accesso con i privilegi di root (utente sudo), puoi digitare i comandi necessari per effettuare le operazioni amministrative. Prima, però, ti consigliamo di modificare la password:

```sh
~$ sudo passwd
New password:
Retype new password:
passwd: password updated successfully
```

Attenzione: le password non vengono mostrate. Dopodiché passa all’utente “root”e definisci la password admin:

```sh
~$ sudo su -
~#passwd
New password:
Retype new password:
passwd: password updated successfully
```

#### Attiva le connessioni root

Per motivi di sicurezza, la connessione con l'utente "root" viene disattivata di default. Per autorizzare questo tipo di connessioni, consulta questa [guida](../root-password/#attiva-la-password-di-root_1).

#### Installa o reinstalla il tuo VPS (gamma attuale)

Le operazioni di installazione possono essere effettuate direttamente dallo Spazio Cliente OVHcloud. Apri la scheda “Home Page”, seleziona “SO/Distribuzione” nell’aera **Il tuo VPS**, quindi clicca sui tre puntini`...`{.action} e infine su `Reinstalla il tuo VPS`{.action}.

![Reinstalla il VPS](images/2020panel_02.png){.thumbnail}

Si apre una finestra da cui potrai scegliere:

- il sistema operativo da utilizzare
- una chiave SSH (se hai già creato chiavi nel tuo Spazio Cliente OVHcloud)

![Reinstalla il VPS](images/2020panel_01.png){.thumbnail}

> [!primary]
>
> Alcuni sistemi operativi o piattaforme proprietarie come Plesk o cPanel richiedono licenze che generano costi aggiuntivi. Le operazioni di gestione delle licenze sono disponibili dallo Spazio Cliente: è sufficiente accedere alla sezione `Bare Metal Cloud` in alto a destra e cliccare su `Licenze`{.action}.
> 
> Un sistema operativo **Windows** può essere utilizzato su un VPS solo se questa **opzione viene selezionata in fase d’ordine**. Sui VPS con altri sistemi operativi non è quindi possibile reinstallare Windows.
> 

L’operazione di reinstallazione potrebbe richiedere fino a 30 minuti. Una barra di progressione ti mostrerà lo stato di avanzamento del processo:

### Iniziare a utilizzare un VPS (gamma meno recente)

#### Accedi al tuo VPS (gamma meno recente)

Durante l'installazione (o la reinstallazione) del VPS, ricevi un’email con la password di accesso root per stabilire una connessione totalmente sicura utilizzando il protocollo SSH. Per saperne di più, consulta [la nostra guida d’introduzione a SSH per i server dedicati OVHcloud](../../dedicated/introduzione-ssh/). 

Questo tipo di accesso viene effettuato su Linux e MAC tramite un terminale e, con Windows, utilizzando un software di terze parti (ad esempio Putty).

Se utilizzi PuTTy, avvia l’applicazione e inserisci il nome del server o l’indirizzo IPv4 corrispondente per stabilire una connessione. Una volta inseriti nome utente e password, potrai accedere all’interfaccia online di comando (CLI).

![utilizzo putty](images/putty1.png){.thumbnail}

Una volta avviato il terminale, accedi al tuo VPS digitando il comando:

```sh
ssh root@IPv4_del_tuo_VPS
```

o

```sh
ssh root@indirizzo_di_riferimento_del_tuo_VPS
```

#### Installa o reinstalla il tuo VPS (gamma meno recente)

Le operazioni di installazione possono essere effettuate direttamente dallo Spazio Cliente OVHcloud cliccando sul pulsante `Reinstalla il tuo VPS`{.action}:

![Reinstalla il VPS](images/reinstall_manager.png){.thumbnail}

Si apre una finestra da cui potrai scegliere:

- il sistema operativo da utilizzare
- la lingua di installazione
- una chiave SSH (se hai già creato chiavi nel tuo Spazio Cliente OVHcloud)


![Menu di reinstallazione](images/reinstall_menu.png){.thumbnail}

> [!primary]
>
> Alcuni sistemi operativi o piattaforme proprietarie come Plesk o cPanel richiedono licenze che generano costi aggiuntivi. Le operazioni di gestione delle licenze sono disponibili dallo Spazio Cliente: è sufficiente accedere alla sezione `Bare Metal Cloud` in alto a destra e cliccare su `Licenze`{.action}.
> 
> Un sistema operativo **Windows** può essere utilizzato su un VPS solo se questa **opzione viene selezionata in fase d’ordine**. Sui VPS con altri sistemi operativi non è quindi possibile reinstallare Windows.
> 

L’operazione di reinstallazione potrebbe richiedere fino a 30 minuti. Una barra di progressione ti mostrerà lo stato di avanzamento del processo:

### Metti in sicurezza il tuo VPS

Come spiegato nella parte iniziale di questa guida, in quanto amministratore del tuo VPS sei anche responsabile della sua sicurezza e dei dati in esso contenuti.

Per ulteriori informazioni sulla [protezione di un VPS](../consigli-sicurezza-vps/){.external}, consulta la nostra guida dedicata all’argomento.


### Proteggi il tuo dominio con un certificato SSL

Una volta installato e reso sicuro il VPS, è utile proteggere anche il tuo dominio e il tuo sito. Utilizzare un certificato SSL consente agli utenti di accedere alle tue pagine Web anche tramite *HTTPS*, oltre che in *HTTP*.

Questo tipo di certificato può essere installato manualmente direttamente sul VPS. Per eseguire questa operazione, fai riferimento alla documentazione ufficiale della distribuzione utilizzata.

Se invece preferisci una soluzione automatica, scegli il servizio [SSL Gateway](https://www.ovh.it/ssl-gateway/) offerto da OVHcloud e consulta la nostra [pagina commerciale](https://www.ovh.it/ssl-gateway/){.external} e le nostre [guide](https://docs.ovh.com/it/ssl-gateway/){.external} per utilizzarlo.

## Per saperne di più

[Introduzione a SSH](../../dedicated/introduzione-ssh/){.external}

Contatta la nostra Community di utenti all’indirizzo <https://community.ovh.com/en/>.