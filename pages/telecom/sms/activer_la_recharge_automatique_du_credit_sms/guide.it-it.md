---
title: Gestire i crediti SMS e attivare la ricarica automatica
slug: attivare-la-ricarica-automatica-del-credito-sms 
excerpt: Come gestire i tuoi crediti SMS OVHcloud
section: Gestisci la tua offerta
---

**Ultimo aggiornamento: 19/05/2020**

## Obiettivo

Questa guida ti spiega cosa sono i crediti SMS, come ricaricarli in modo automatico e come trasferirli tra i tuoi account SMS.

## Prerequisiti

* Disporre di un account SMS OVHcloud attivo
* Avere accesso alle [API OVHcloud](https://api.ovh.com/console/)(soltanto per trasferire i crediti).

## Procedura

### **Pack crediti SMS **

0,7 credito SMS corrisponde al costo per l’invio di 1 SMS in Italia, la tariffa è decrescente in base al numero di crediti SMS acquistati in una sola volta . 

Per visualizzare la lista completa dei Pack SMS clicca qui: [https://www.ovh.it/sms/](https://www.ovh.it/sms/).

**Ad esempio, per l’acquisto di un pack di 100 crediti SMS, il costo di ciascun credito è pari a 0,042 € IVA esclusa.**

Il costo per l’invio di 1 SMS in Italia è pari a 0,7 credito. Con questo pack, è possibile inviare fino a 143 SMS in Francia metropolitana.
Il costo per l’invio di 1 SMS in India è pari a 0,1 crediti. Con questo pack è possibile inviare fino a 1000 SMS india.

Per visualizzare i costi, in crediti, per l’invio dei tuoi SMS in base alle loro destinazioni, clicca qui: [https://www.ovh.it/sms/tariffe/](https://www.ovh.it/sms/tariffe/).

> [!primary]
>
> Un SMS può contenere un numero limitato di caratteri in base alla codifica. Per maggiori dettagli sulla codifica e i caratteri autorizzati, consulta questa guida: 
> 
> [Inviare SMS dallo Spazio Cliente OVHcloud](../inviare_sms_dallo_spazio_cliente/#step--2-scrivi-il-tuo-sms)
>

### **Ricarica automatica**

Per disporre sempre di credito sufficiente sul tuo account SMS, è possibile e attivare la ricarica automatica. Non appena viene raggiunta la soglia minima di crediti rimanenti, un nuovo numero di crediti viene automaticamente aggiunto al tuo account SMS.

Per attivare la ricarica automatica, accedi allo [Spazio Cliente OVHcloud](https://www.ovh.com/auth/?action=gotomanager){.external}, clicca sulla scheda `Telecom`{.action} e poi sulla sezione `SMS`{.action} nel menu a sinistra. Seleziona l’account SMS su cui attivare la ricarica automatica.

Clicca sul menu `Opzioni`{.action} (1) e poi su Ricarica automatica`{.action} (2).

![credit sms](images/smscredit1.png){.thumbnail}

Quindi clicca su `Modifica`{.action}nella sezione “Gestisci le opzioni”.

![credit sms](images/smscredit2.png){.thumbnail}

Infine, compila i campi richiesti:

* Soglia minima (1): al raggiungimento di questa soglia, scatta automaticamente la ricarica.
* Quantità da ricaricare (2): si riferisce al numero di crediti da ricaricare sul tuo account SMS. È possibile scegliere tra: 100, 200, 250, 500 e 1000.
* Clicca sul pulsante `Conferma`{.action} per convalidare l’operazione.

![credit sms](images/smscredit3.png){.thumbnail}

### **Il trasferimento dei crediti**

> [!primary]
>
> È possibile trasferire i crediti soltanto tra gli account SMS di uno stesso identificativo cliente OVHcloud. Il trasferimento dei crediti tra due diversi identificativi OVHcloud non è consentito.
>

Il trasferimento dei crediti è consentito solo tramite API.

Accedi alla pagina [https://api.ovh.com/](https://api.ovh.com/console/) e poi utilizza l’API seguente:

> [!api]
>
> @api {post} /sms/{serviceName}/transferCredits
>

A questo punto, è necessario completare i campi seguenti:

* serviceName: inserisci il nome dell’account SMS utilizzato per trasferire i crediti
* credits: inserisci il numero di crediti da trasferire
* smsAccountTarget: inserisci il nome dell’account SMS che riceve i crediti

Clicca su `Esegui`{.action} per confermare il trasferimento, che avverrà in modo immediato.

## Per saperne di più

Contatta la nostra Community di utenti all’indirizzo [https://community.ovh.com/en/](https://community.ovh.com/en/).
