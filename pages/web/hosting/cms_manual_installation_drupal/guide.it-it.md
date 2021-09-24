---
title: 'CMS: installa manualmente Drupal'
excerpt: Come fai a installare manualmente Drupal?
id: '1976'
slug: cms_installa_manualmente_drupal
legacy_guide_number: g1976
section: CMS
---


## Parte 1: preparazione all’installazione
Software

Per installare il CMS Drupal sulla tua offerta di hosting condiviso, ti consigliamo di utilizzare un client FTP come FileZilla (gratuito).

## [b]Credenziali[/b]
Assicurati di disporre delle credenziali (Nic-handle e password) di accesso al tuo [Spazio Cliente OVH](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.it/&ovhSubsidiary=it).


- Recupera le credenziali FTP per accedere al tuo hosting Web.

- Assicurati di avere a disposizione le credenziali per accedere al tuo database SQL.
Per recuperare le tue credenziali SQL, consulta questa guida:[]({legacy}1909)



## Parte 2: recupero dei file sorgente

- Accedi al sito di [Drupal](http://www.drupal.it/).



![](images/img_3234.jpg){.thumbnail}
In genere, il link disponibile ti permette di scaricare l'ultima versione stabile del CMS.
Nel nostro esempio, la versione utilizzata è la 7.41.
Il file scaricato generalmente è compresso (.zip). Per aprirlo e installarlo è necessario decomprimerlo.


## Parte 3: configurazione dei file sull'hosting via FTP

- Decomprimi la cartella:


Apri la cartella in cui hai scaricato il file compresso.

Clicca con il tasto destro, seleziona Estrai tutto... o Estrai qui e indica la cartella di destinazione dei tuoi file.

Se hai bisogno di aiuto, segui i numerosi tutorial online e scarica uno dei tanti programmi per decomprimere file .zip disponibili su Internet.

La cartella di destinazione si chiamerà Drupal-xxx (xxx spesso è sostituito dal numero della versione).

![](images/img_3233.jpg){.thumbnail}

- Accedi al tuo hosting Web via FTP


Accedi al tuo hosting e salva i file di Drupal.

Se hai bisogno di aiuto per accedere in FTP alla tua soluzione di hosting condiviso, consulta la guida []({legacy}1374)

- Trasferisci i tuoi file via FTP


Per salvare i tuoi file sull'FTP, segui questi step.

## Step 1
Apri FileZilla.

Nella sezione Sito locale, che contiene l'elenco dei file presenti sul tuo pc, apri la cartella decompressa Drupal-xxx in cui sono presenti i file del tuo CMS.
Nella sezione Sito remoto, che corrisponde in questo caso al tuo hosting condiviso OVH, apri la cartella www in cui dovrai salvare tutti i file del CMS.
Se questa cartella non esiste, puoi crearla.
Per poter effettuare l'installazione dal tuo dominio, i tuoi file devono necessariamente essere salvati nella cartella "www".

## Step 2
Una volta che hai aperto le cartelle:

Nella sezione Sito locale trovi i file necessari all'installazione di Drupal.

Selezionali tutti premendo i tasti CTRL+A.

Trascina i tuoi file nella cartella "www" della sezione Sito remoto.

![](images/img_3199.jpg){.thumbnail}
È molto probabile che la cartella "www" non sia vuota. Non è obbligatorio eliminare i file presenti al suo interno.

## Step 3
Attendi qualche minuto fino al completo trasferimento dei file sul server FTP remoto.

Al termine dell'operazione, assicurati che tutti i file e le cartelle siano state spostate correttamente.

![](images/img_3200.jpg){.thumbnail}


## Step 1 - Installa Drupal
Inserisci il tuo dominio nella barra degli indirizzi del tuo browser.
Si apre questa pagina:

Seleziona Standard
Install with commonly used features pre-configured. e clicca su Save and continue.

![](images/img_3219.jpg){.thumbnail}


## Step 2 - Scegli una lingua
La lingua di installazione predefinita è l'inglese. Per modificarla, clicca su Learn how to install Drupal in other languages, scegli il pacchetto della tua lingua e ricarica la pagina. A questo punto, seleziona "Italian (italiano)" e clicca su Save and continue.

![](images/img_3218.jpg){.thumbnail}


## Step 3 - Imposta il database
Recupera le credenziali del tuo database (se hai bisogno di aiuto, consulta la guida[]({legacy}1374)).

Inserisci le informazioni del tuo database:

Seleziona MySQL, MariaDB o equivalente.


- Nome database: il nome scelto al momento della sua creazione nello Spazio Cliente OVH.

- Nome utente database: uguale al nome del database.

- Password database: se non l'hai modificata, la password che hai ricevuto per email durante al momento della creazione del tuo database.

- Clicca poi su OPZIONI AVANZATE".



![](images/img_3202.jpg){.thumbnail}

- Host database: il nome del server del tuo database, indicato nell'email di installazione o nel tuo Spazio Cliente OVH. Generalmente finisce per .mysql.db.

- Porta database: lascia vuoto questo campo.

- Prefisso tabella: utile per realizzare più installazioni di Drupal o altri CMS utilizzando lo stesso database. In questo caso, è necessario inserire un prefisso diverso per ognuna delle installazioni. Nel dubbio, lascia il campo vuoto.



![](images/img_3203.jpg){.thumbnail}
Importante: le credenziali del database non vengono inviate automaticamente durante l'installazione dell'hosting. Per riceverle, attiva il database nel tuo Spazio Cliente OVH.
Clicca su Salva e continua per confermare le informazioni di accesso al tuo database.


## Step 4 - Progressione dell'installazione
Se hai inserito correttamente le informazioni del tuo database, l'installazione si avvia.
Altrimenti, ripeti l'operazione.


- Attendi il completamento dell'installazione.



![](images/img_3190.jpg){.thumbnail}


## Step 5 - Configura sito
Inserisci le informazioni del tuo CMS Drupal.

- Nome del sito: il nome del tuo dominio.

- Indirizzo e-mail del sito: l'indirizzo che utilizzerà il tuo sito per inviare i messaggi agli iscritti.

- Nome utente: il nome dell'account amministratore del tuo sito (nel nostro esempio, admin).

- Indirizzo e-mail: l'indirizzo che sarà associato al tuo account amministratore.

- Password: la password del tuo account amministratore.

- Conferma la password: inserisci di nuovo la tua password.



![](images/img_3206.jpg){.thumbnail}

- Paese predefinito: scegli il Paese e la lingua del tuo sito.
- Fuso orario predefinito: inserisci il fuso orario del tuo sito.

- Seleziona le opzioni Controlla automaticamente gli aggiornamenti disponibili e Ricevi le notifiche per e-mail.

- Clicca su Salva e continua.



![](images/img_3207.jpg){.thumbnail}


## Step 6 - Finalizzazione
Il tuo CMS Drupal è installato!
Clicca su Visita il nuovo sito.

![](images/img_3208.jpg){.thumbnail}
Costruisci il tuo sito con il tuo CMS Drupal!

![](images/img_3209.jpg){.thumbnail}


## Supporto Drupal
Se hai bisogno di aiuto per utilizzare il tuo CMS, ti consigliamo di consultare i forum dedicati alla soluzione e la pagina del [supporto ](https://www.drupal.org/support).
Il supporto OVH non risponde alle domande relative alla configurazione del tuo CMS.
Se hai bisogno di aiuto, consulta la guida []({legacy}2053) disponibile online.


## Errori comuni

- Errore "OVH - Sito in costruzione"


Hai configurato i tuoi file sul tuo server FTP, ma continui a visualizzare la pagina "Sito in construzione" di OVH.

Quando installi il tuo hosting, OVH realizza una pagina di attesa per permetterti di caricare i file del tuo sito.

Se salvi i file nella cartella www ma non elimini il contenuto inserito da OVH, potrebbe verificarsi questo problema.

Per risolverlo, elimina o rinomina il file "index.html" che OVH ha salvato sul tuo hosting.

Se rinomini semplicemente il file, puoi riattivarlo in qualsiasi momento per utilizzarlo come pagina di attesa.

Altre informazioni utili: per essere presi in carico, i file del tuo sito devono trovarsi nella cartella "www".

![](images/img_3217.jpg){.thumbnail}

- Errore con la versione di PHP


È un errore che riguarda la versione PHP del tuo server.

La causa è semplice: l'ultima versione di PHP non è stata attivata.

Per modificare la versione PHP del tuo hosting coindiviso, consulta la guida [Configura PHP sul tuo Hosting Web OVH]({legacy}1207)

