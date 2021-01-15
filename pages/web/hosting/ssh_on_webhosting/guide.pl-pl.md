---
title: 'Korzystanie z dostępu do hostingu WWW przez SSH'
id: '1962'
slug: hosting_www_ssh_na_hostingu
excerpt: 'Dowiedz się jak się podłączyć i korzystać z dostępu do Twojego hostingu OVHcloud przez protokół SSH'
section: 'FTP i SSH'
---

**Ostatnia aktualizacja z dnia 04-08-2020**

## Wprowadzenie

Wraz z pakietami hostingowymi OVHcloud zyskujesz dostęp do przestrzeni dyskowej umożliwiającej umieszczanie w Internecie plików z Twoich stron www lub Twoich aplikacji. Do przestrzeni dyskowej możesz zalogować się używając, między innymi, protokołu FTP lub SSH oraz odpowiadających im haseł.

**Odkryj jak się podłączyć i korzystać z dostępu do Twojego hostingu OVHcloud przez protokół SSH.**

## Wymagania początkowe

- Posiadanie [hostingu WWW OVHcloud](https://www.ovh.pl/hosting/) z dostępem przez protokół SSH.
- Posiadanie informacji umożliwiających logowanie się do przestrzeni dyskowej za pomocą SSH.
- Mieć dostęp do [panelu klienta OVHcloud](https://www.ovh.com/auth/?action=gotomanager), sekcja `Web Cloud`{.action}.

## W praktyce

### Etap 1: upewnij się, że dostęp przez SSH jest aktywny

Rozpocznij od zalogowania się do [panelu klienta OVHcloud](https://www.ovh.com/auth/?action=gotomanager) w sekcji `Web Cloud`{.action} i kliknij `Hostingi`{.action} na pasku usług po lewej stronie. Wybierz odpowiedni hosting i przejdź do zakładki `FTP - SSH`{.action}. Wyświetlą się wówczas dane dotyczące Twojej przestrzeni dyskowej. 

Odnajdź w tabeli kolumnę „SSH”, aby sprawdzić, czy dany użytkownik SSH (lub „Login SSH”) posiada aktywny dostęp przez protokół SSH. Jeżeli tak nie jest, pojawi się informacja „Wyłączony”.

![usessh](images/use-ssh-step1.png){.thumbnail}

Jeżeli dostęp nie jest aktywny, kliknij przycisk `...`{.action} po prawej stronie wybranego użytkownika, a następnie `Zmień`{.action}. W oknie, które się wyświetli, włącz dostęp SSH, a następnie dokończ procedurę zmiany ustawienia. Jeżeli nie znajdujesz opcji aktywacji, sprawdź, czy [Twoja oferta hostingowa www OVHcloud](https://www.ovh.pl/hosting/) posiada dostęp przez protokół SSH.

### Etap 2: pobranie informacji niezbędnych do logowania

Aby zalogować się do przestrzeni dyskowej przez SSH, należy posiadać następujące dane. Jeżeli ich nie posiadasz, znajdziesz je w zakładce `FTP - SSH`{.action}.

|Element|Gdzie go znaleźć?|
|---|---|
|Aktywny użytkownik SSH|Odnajdziesz go w kolumnie „Login SSH” tabeli. Przypominamy, że użytkownik ten musi [posiadać aktywny dostęp przez SSH](./#etap-1-upewnij-sie-ze-dostep-przez-ssh-jest-aktywny).|
|Hasło użytkownika SSH|Jeżeli nie pamiętasz hasła, możesz je zmienić klikając przycisk `...`{.action}, a następnie `Zmień hasło`{.action}.|
|Adres serwera SSH|Wyszukaj opcję „Dostęp do klastra przez SSH”. W elemencie, który wtedy się pojawi, adres serwera SSH rozpoczyna się po „ssh://” i kończy przed znakiem „:”.|
|Port połączenia z serwerem SSH|Wyszukaj opcję „Dostęp do klastra przez SSH”. W elemencie, który się wtedy pojawi, numer portu podany jest po znaku „:”.|

Oto przykład tego, jak może on wyglądać: `ssh://ssh.cluster023.hosting.ovh.net:22/`. Adres serwera SSH to „ssh.cluster023.hosting.ovh.net”, a „22” - numer portu łączenia SSH.

![usessh](images/use-ssh-step2.png){.thumbnail}

### Etap 3: zaloguj się do przestrzeni dyskowej przez protokół SSH

Aby zalogować się przez SSH, użyj terminala, dzięki któremu będziesz mógł(mogła) działać bezpośrednio na Twojej przestrzeni dyskowej za pomocą wierszy poleceń.  

Narzędzie to jest zainstalowane domyślnie na MacOS, Linuxie i Windows 10. Starsza wersja środowiska Windows wymagać będzie instalacji programu, takiego jak PuTTY lub dodania funkcji OpenSSH. Ponieważ operacja ta jest ściśle związana z używanym przez Ciebie systemem operacyjnym, nie możemy opisać jej przebiegu w tej dokumentacji. 

Masz teraz dwie możliwości zalogowania się, w zależności od używanej przez Ciebie metody:

#### 3.1 Za pośrednictwem terminala

> [!warning]
> Nasza oferta hostingowa na posiada dostępu „super użytkownik” (lub „root”) przez protokół SSH.

Po otworzeniu terminala, zastosuj poniższe polecenie, zastępując elementy „sshlogin”, „sshserver” oraz „connectionport” przez Twoje dane identyfikacyjne SSH. 

```ssh
ssh sshlogin@sshserver -p connectionport
```

Po wysłaniu polecenia zostaniesz poproszony(-a) o wpisanie hasła użytkownika SSH. Po zalogowaniu przejdź do etapu kolejnego: „[Operacje na przestrzeni dyskowej za pomocą SSH](./#etap-4-przeprowadzanie-operacji-na-przestrzeni-dyskowej-z-wykorzystaniem-ssh_1)”.

![usessh](images/use-ssh-step3.png){.thumbnail}

#### 3.2 Za pomocą oprogramowania

Po otwarciu danego oprogramowania (np. PuTTY), wpisz dane do logowania SSH. Ponieważ operacja ta jest nieodłącznie związana z tym oprogramowaniem, nie możemy opisać jej szczegółowo w niniejszej dokumentacji. W ramach przypomnienia zamieszczamy poniżej informacje, które należy wprowadzić:

|Dane do uzupełnienia|Szczegóły|
|---|---|
|Serwer SSH|Podaj adres serwera SSH otrzymany [w trakcie realizacji etapu 2](./#etap-2-pobranie-informacji-niezbednych-do-logowania). W zależności od użytego oprogramowania, jego nazwa może być określona jako: „Adres serwera”, „Nazwa hosta” lub „Host name”.|
|Port połączenia|Wpisz port połączenia SSH otrzymany [w trakcie realizacji etapu 2](./#etap-2-pobranie-informacji-niezbednych-do-logowania).|
|Login SSH|Podaj użytkownika SSH. W zależności od użytego oprogramowania, może być on nazwany „Nazwa użytkownika”, „Identyfikator”, „Login” albo „Username”.|
|Hasło użytkownika SSH|Wpisz hasło powiązane z loginem SSH.<br><br> W zależności od użytego oprogramowania, jego nazwa może również przybrać formę angielskiego „Password”.|

Po zalogowaniu, przejdź do następnego etapu.

### Etap 4: przeprowadzanie operacji na przestrzeni dyskowej z wykorzystaniem SSH

Do przeprowadzania operacji na przestrzeni dyskowej musisz posłużyć się odpowiednimi poleceniami. Polecenia te mają konkretne znaczenie w języku angielskim. Dla ułatwienia możesz posłużyć się zamieszczoną poniżej listą. Uwaga, **lista nie jest kompletna**.

|Zamówienie|Znaczenie w języku angielskim|Opis| 
|---|---|---|
|pwd|Print working directory|Wyświetla katalog roboczy, w którym aktualnie się znajdujesz.| 
|cd `arg`|Change directory|Umożliwia przejście do katalogu roboczego wskazanego w miejsce `arg`.|
|cd `..`|Change directory|Umożliwia zmianę katalogu roboczego i przejście o jeden poziom wyżej w hierarchicznej strukturze Twoich katalogów.|
|cd|Change directory|Bez wskazywania argumentu, pozwala na przejście do katalogu głównego Twojej przestrzeni dyskowej (home).|
|ls|List|Wyświetla w formie listy zawartość Twojego katalogu roboczego. Dodaj atrybuty, aby zmienić wyświetlanie rezultatu polecenia (np.`ls -ulhG`).| 
|chmod `droit` `arg`|Change mode|Zmienia uprawnienia do pliku lub katalogu wskazanego jako argument `arg`.| 
|mkdir `arg`|Make directory|Pozwala utworzyć katalog noszący nazwę argumentu `arg`.| 
|touch `arg`|Touch|Tworzy pusty plik o nazwie wskazanej jako argument `arg`, jeżeli taki plik jeszcze nie istnieje.|
|rm `arg`|Remove|Usuwa plik wskazany jako argument `arg`.| 
|rm -r `arg`|Remove|Usuwa w sposób rekurencyjny katalog wskazany jako argument `arg` wraz z całą jego zawartością| 
|mv `arg1` `arg2`|Move|Zmienia nazwę lub przenosi dany element (określony jako `arg1`) do nowej lokalizacji (określonej jako `arg2`).| 

Za pomocą specjalnego polecenia możesz również uruchomić skrypt korzystający z określonej wersji PHP. Przykładowo, w przypadku wersji PHP 7.1, użyj następującego polecenia, dostosowując jego elementy do Twojej profilu:

```sh
/usr/local/php7.1/bin/php myscript.php
```

W zależności od wersji PHP, której chcesz używać, środowisko uruchomieniowe może wymagać modyfikacji, aby zagwarantować kompatybilność. Sprawdź naszą dokumentację”>.

## Sprawdź również

[Zmiana konfiguracji hostingu](../zmiana_srodowiska_uruchomieniowego_dla_hostingu_www/).

[Konfiguracja pliku .ovhconfig w hostingu](../konfiguracja-pliku-ovhconfig/).

Dołącz do społeczności naszych użytkowników na stronie <https://community.ovh.com/en/>.
