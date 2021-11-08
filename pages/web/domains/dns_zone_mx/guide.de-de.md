---
title: 'MX-Eintrag zur Konfiguration Ihrer Domain hinzufügen'
excerpt: 'Hier erfahren Sie, wie Sie bei OVH einen MX-Eintrag zur Konfiguration Ihrer Domain hinzufügen.'
slug: webhosting_e-mail_mx-konfiguration_mit_dns_zone_von_ovh
legacy_guide_number: g2012
section: 'DNS und DNS-Zone'
order: 4
---

**Stand 05.12.2018**

## Einleitung

Der MX-Eintrag (Mail Exchange) legt den für die E-Mail-Adressen der Domain zuständigen E-Mail-Server fest. Dadurch wird Servern, die E-Mails an Ihre Adressen versenden, mitgeteilt, wohin sie diese versenden sollen. Möglicherweise verfügt Ihr Anbieter über mehrere E-Mail-Server. Erstellen Sie in diesem Fall auch mehrere MX-Einträge.

**In dieser Anleitung erfahren Sie, wie Sie bei OVH einen MX-Eintrag zur Konfiguration Ihrer Domain hinzufügen.**

## Voraussetzungen

- Sie haben über Ihr [OVH Kundencenter](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.de/&ovhSubsidiary=de){.external} Zugriff auf die Verwaltung der betreffenden Domain.
- Sie sind in Ihrem [OVH Kundencenter](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.de/&ovhSubsidiary=de){.external} eingeloggt.
- Die betreffende Domain verwendet die OVH Konfiguration (das heißt die OVH DNS-Server).

> [!warning]
>
> - Wenn Ihre Domain nicht die DNS-Server von OVH verwendet, muss die Änderung über das Interface des Anbieters vorgenommen werden, bei dem die Konfiguration Ihrer Domain verwaltet wird.
>
> - Wenn Ihre Domain bei OVH registriert ist, können Sie überprüfen, ob diese die OVH Konfiguration verwendet. Gehen Sie hierzu in Ihrem [Kundencenter](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.de/&ovhSubsidiary=de){.external} zur entsprechenden Domain und anschließend auf den Tab `DNS-Server`{.action}.
>

## Beschreibung

### Schritt 1: Den MX-Eintrag verstehen

Der MX-Eintrag verbindet Ihre Domain mit den Servern Ihres E-Mail-Anbieters (zum Beispiel OVH). Wenn jemand eine E-Mail an Sie versendet, weiß der Server der ausgehenden E-Mail dank des MX-Eintrags, an welchen Server er diese zu übermitteln hat.

Da für eine Domain mehrere MX-Einträge erstellten werden können, muss für jeden Eintrag die Priorität festgelegt werden. Dadurch wissen die Ausgangsserver, an welchen Server sie die E-Mails zuerst senden sollen. Beachten Sie jedoch, dass die Erstellung mehrerer MX-Einträge nur für Server desselben Anbieters möglich ist.

**Seien Sie vorsichtig bei der Änderung von MX-Einträgen**. Wenn Sie eine falsche Änderung vornehmen, kann es sein, dass Ihre E-Mail-Adressen keine Nachrichten mehr empfangen können. 

### Schritt 2: OVH MX-Konfiguration kennenlernen

In der folgenden Tabelle wird Ihnen die OVH MX-Konfiguration für MX Plan (separat oder in einem [OVH Webhosting](https://www.ovhcloud.com/de/web-hosting/){.external} enthalten), [E-Mail Pro](https://www.ovhcloud.com/de/emails/email-pro/){.external} und [Exchange](https://www.ovhcloud.com/de/emails/){.external} angezeigt. Unsere E-Mail-Server verfügen über Antispam und Antivirus.

|Domain|TTL|Eintrag|Priorität|Ziel|
|---|---|---|---|---|
|*leer lassen*|3600|MX|1|mx0.mail.ovh.net.|
|*leer lassen*|3600|MX|5|mx1.mail.ovh.net.|
|*leer lassen*|3600|MX|50|mx2.mail.ovh.net.|
|*leer lassen*|3600|MX|100|mx3.mail.ovh.net.|
|*leer lassen*|3600|MX|200|mx4.mail.ovh.net.|

Verwenden Sie diese MX-Einträge für die DNS-Konfiguration Ihrer Domain. Im nächsten Schritt erfahren Sie, wie Sie die OVH DNS-Konfiguration Ihrer Domain entsprechend ändern.

### Schritt 3: MX-Eintrag bearbeiten

Um MX-Einträge in der Konfiguration Ihrer OVH Domain zu ändern, loggen Sie sich in Ihrem [OVH Kundencenter](https://www.ovh.com/auth/?action=gotomanager&from=https://www.ovh.de/&ovhSubsidiary=de){.external} ein. Gehen Sie links im Menü in den Bereich `Domains`{.action}, klicken Sie auf die betreffende Domain und anschließend auf den Tab `DNS Zone`{.action}.

In der Tabelle wird die OVH Konfiguration Ihrer Domain angezeigt. Jede Zeile entspricht einem DNS-Eintrag. Überprüfen Sie über die Filterfunktion zunächst, ob in der DNS-Konfiguration Ihrer Domain bereits MX-Einträge vorhanden sind.

![dnsmxrecord](images/mx-records-dns-zone.png){.thumbnail}

Wenn bereits MX-Einträge vorhanden sind und Sie diese ersetzen möchten, klicken Sie rechts am Ende jeder betreffenden Zeile auf das Zahnrad-Symbol und wählen Sie dann `Eintrag löschen`{.action} aus. Achten Sie jedoch darauf, dass für Ihre Domain immer ein MX-Eintrag bestehen bleibt, während Sie neue MX-Einträge hinzufügen.

Um Einträge hinzuzufügen, klicken Sie auf `Eintrag hinzufügen`{.action} und wählen Sie dann `MX`{.action} aus. Tragen Sie die angeforderten Informationen für die ausgewählte E-Mail-Lösung ein:

- **OVH E-Mail-Lösung**: Lesen Sie in dieser Anleitung „[Schritt 2: OVH MX-Konfiguration kennenlernen](https://docs.ovh.com/de/domains/webhosting_e-mail_mx-konfiguration_mit_dns_zone_von_ovh/#schritt-2-ovh-mx-konfiguration-kennenlernen){.external}“.

- **E-Mail-Lösung eines anderen Anbieters**: Informieren Sie sich über die MX-Konfiguration beim Anbieter Ihres E-Mail-Dienstes.

Wenn Sie alle Informationen eingegeben haben, folgen Sie den nächsten Schritten und klicken Sie anschließend auf `Bestätigen`{.action}.

> [!primary]
>
> Die Änderung erfordert eine Propagationszeit zwischen 4 und 24 Stunden, bis sie voll wirksam ist.
>

## Weiterführende Informationen

[Webhosting − Allgemeine Informationen zu den DNS Servern](https://docs.ovh.com/de/domains/webhosting_allgemeine_informationen_zu_den_dns_servern/){.external}

[Bearbeiten der OVH DNS-Zone](https://docs.ovh.com/de/domains/webhosting_bearbeiten_der_dns_zone/){.external}

Für den Austausch mit unserer User Community gehen Sie auf [https://community.ovh.com/en/](https://community.ovh.com/en/){.external}.