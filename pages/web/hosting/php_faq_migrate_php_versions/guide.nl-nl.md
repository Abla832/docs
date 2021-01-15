---
deprecated: true
title: 'Webhosting: FAQ Migratie naar de meest recente PHP versies'
excerpt: FAQ voor migratie naar de meest recente PHP versies
slug: webhosting_faq_migratie_naar_de_meest_recente_php_versies
legacy_guide_number: g1758
---


## Informatie over PHP
Wat is PHP?
PHP is een open-source programmeertaal, die voornamelijk wordt gebruikt om dynamische webpagina's te maken.
Het is tegenwoordig een van de meest gebruikte programmeertalen op het web, en wordt gebruikt door content managers zoals Wordpress, Joomla and Drupal.
Waarom gaat OVH sommige PHP-versies deactiveren?/b]
Zoals alle programmeertalen, blijft PHP evolueren. De wijzigingen brengen nieuwe functies, bug correcties, etc. De oudere versies blijven actief gedurende een duidelijk omschreven levenscyclus en daarna gestopt.
Deze oudere versies worden niet onderhouden en vormen dus  veiligheidsrisico's voor OVH en zijn gebruikers, daarom gaan we deze deactiveren.
Wat zijn de voordelen van de overgang naar de nieuwe PHP-versies voor de gebruiker?
Door het migreren van uw site naar de meest recente PHP versies, zult u minder risico lopen op veiligheidsrisico's (pirating), terwijl u gebruik kunt gaan maken van nieuwe functies en onze support.
Bovendien biedt OVH gratis PHP-FPM optimalisatie om uw prestaties te verbeteren (vanaf versie 5.3), klik [hier](https://www.ovh.com/fr/hebergement-web/optimisation-php-fpm.xml) voor meer informatie.
Welke versies betreft het en vanaf wanneer worden deze gedeactiveerd?
Hieronder vindt u de getroffen versies:

|Versie|Date of end-of-life|Geen support gedurende [jaar] + [maanden]|
|4.X|7 augustus 2008|6 jaar en 8 maanden|
|5.2|6 Januari 2011|4 jaar en 3 maanden|
|5.3|14 augustus 2014|8 maanden|


Source: http://php.net/eol.php

Deze versies worden gedeactiveerd vanaf 24 september 2015. U kunt de werktaak volgen via dit adres: [http://travaux.ovh.net/?do=details&id=12795](http://travaux.ovh.net/?do=details&id=12795)
Om welke hostings gaat het?
Dit betreft al onze webhosting contracten onder Linux, 60Free en Demo1G uitgezonderd.
Mijn site of een gedeelte van mijn site gebruikt verouderde PHP versies, wat nu?
Met ingang van 24 september 2015, gaan uw sites en uw geplande taken (CRON) standaard over naar PHP 5.4.

Wij adviseren u dringend om uw sites en geplande taken zo vlug mogelijk te testen met deze nieuwe versies. We leggen later in deze FAQ uit hoe u dit kunt doen.
Waarom migreert OVH niet automatisch mijn scripts?/b]
Het deactiveren van oudere versies en de overgang naar standaard PHP 5.4 zal automatisch gebeuren.
Echter, alle sites zijn uniek, dus kan OVH niet ieder script van elke klant aanpassen, daarom dienen de klanten dit zelf uit te voeren.


## STAP 1: zorg ervoor dat uw website compatibel is
A) Indien u een content manager gebruikt zoals Wordpress, Joomla, Dotclear PHPBB, etc., moet u eerst uw website updaten door het volgen van hun officiële handleidingen:

- Wordpress: [https://codex.wordpress.org/Updating_WordPress](https://codex.wordpress.org/Updating_WordPress)
- Joomla: [https://docs.joomla.org/Portal:Upgrading_Versions](https://docs.joomla.org/Portal:Upgrading_Versions)
- Drupal: [https://www.drupal.org/node/1494290r](https://www.drupal.org/node/1494290)
- Prestashop: [url="http://doc.prestashop.com/display/PS15/Updating+PrestaShop"]http://doc.prestashop.com/display/PS15/Updating+PrestaShop[/url]

B) Indien u een gepersonaliseerde solution op uw website uitvoert, volg dan de officiële PHP migratie handleidingen: [http://php.net/manual/en/appendices.php](http://php.net/manual/en/appendices.php)
Als u niet de developer van uw website bent, neem dan contact op met uw webmaster.


## STAP 2: configureer zo snel mogelijk de PHP-versie van uw hosting
Ga naar de root van uw website via FTP. Volg deze handleiding[/url]: [url="https://www.ovh.co.uk/g1380.filezilla-user-guide"], indien nodig.


- U moet een .ovhconfig bestand aanmaken als u er nog geen hebt. Plaats de volgende vier lijnen in een leeg bestand met een teksteditor (we gebruiken in dit voorbeeld versie 5.6):


```
app.engine=php
app.engine.version=5.6
http.firewall=none
environment=production
```



Bewaar dit bestand als ".ovhconfig", en upload het naar de root van de webserver.


- Als u al een .ovhconfig bestand hebt, controleer dan de content ervan met behulp van een text editor, bijv. Bloc-Notes.


Voor meer informatie over het configureren van dit bestand, raden wij u aan deze handleiding[/url]: [url="http://www.ovh.co.uk/g1207.configure-php-web-hosting"] te raadplegen.


## Gebruiksvoorbeeld
Hoe weet ik welke PHP versie mijn website gebruikt?
Download dit bestand: [info.php](https://www.ovh.com/fr/documents/info.php) (rechter muisklik en dan 'Save As').
Als u zelf het bestand wilt aanmaken, is het afdoende om een tekstbestand aan te maken en hier in te zetten: <?php phpinfo(); ?>
Registreer het vervolgens in .php format en geef het de volgende naam: 'info.php'.

Publiceer het bestand via FTP naar de root van uw website of websites (indien u er verschillende heeft die zijn gekoppeld aan subdomeinen). Bijvoorbeeld: /www/mywordpress/
Ga met uw webbrowser naar info.php. Bijvoorbeeld: www.your-site.com/mywordpress/info.php

![](images/img_2601.jpg){.thumbnail}
OVH heeft ook afgelopen maart-april 2015 preventief een e-mail verzonden aan de betreffende gebruikers, met een opsomming van de gebruikte PHP-versies.
Ik beschik over subdomeinen of een multi-domein aanbod, kan ik verschillende PHP versies activeren?
Ja, OVH autoriseert een verschillende PHP versie voor elk van uw subdomeinen (een multi-domein wordt gezien als een subdomein).
Hiervoer dient u een .ovhconfig bestand aan te maken op de root van een bepaald subdomein. Het .ovhconfig bestand wordt als volgt geüpload: 


- Het bestand is geopend vanaf de root van het domein van de applicatie. Bijvoorbeeld «www.exemple.com» verwijst naar het bestand «/www» en «beta.example.com» verwijst naar het bestand «/beta», het bestand «/www/.ovhconfig» 

wordt meegenomen in de query http://www.exemple.com/index.php, terwijl het bestand «/beta/.ovhconfig» verantwoordelijk zal zijn voor een query naar http://beta.exemple.com/index.php.

- Als het bestand .ovhconfig niet specifiek op het subdomein van fase 1 wordt gevonden, wordt vervolgens het bestand «/.ovhconfig» geladen
- Als geen van de bovenstaande bestanden bestaan, wordt de standaard configuratie van uw account toegepast (PHP 5.4 met FPM)


Ik heb een .htaccess bestand geconfigureerd om een PHP versie te forceren. Wat zal hiermee gebeuren?
Vanaf 24/09/2015, zal het gebruik van .htaccess niet langer support ontvangen op de server voor de SetEnv PHP_VER 5 directive. Uw website zal automatisch migreren naar PHP 5.4. Als u een latere versie wilt forceren, zoals 5.6, moet u .ovhconfig (een bestand op uw FTP) configureren.
Andere directives op het .htaccess bestand, bijv. URL rewriting, redirection, etc., zullen actief blijven.
Ik heb problemen met het migreren. Wat kan ik doen?
Ons support team kan uw website niet migreren voor u, maar het team kan u wel helpen bij het updaten van uw PHP versie (met behulp van het .ovhconfig file). Dit team is niet aansprakelijk voor eventuele problemen die zich kunnen voordoen.

