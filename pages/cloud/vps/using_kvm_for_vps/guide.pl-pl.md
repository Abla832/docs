---
title: Używanie konsoli KVM z VPS
excerpt: Dowiedz się, jak uzyskać dostęp do serwera VPS przy użyciu funkcji KVM 
slug: kvm_na_serwerach_vps
section: Pierwsze kroki
---

**Ostatnia aktualizacja z dnia 7-06-2020**

## Wprowadzenie

Konsola KVM pozwala na bezpośrednie połączenie z serwerem VPS bez konieczności korzystania z zewnętrznego oprogramowania (terminal, Putty, itp.). Konsola ta jest dostępna w Panelu klienta OVHcloud lub w API OVHcloud.  

**Niniejszy przewodnik opisuje dwie metody dostępu do KVM.**

## Wymagania początkowe

- Jeden [VPS](https://www.ovhcloud.com/pl/vps/) na koncie OVHcloud.
- Dostęp do [Panelu klienta](https://www.ovh.com/auth/?action=gotomanager)

## W praktyce

### Logowanie do KVM w Panelu klienta OVHcloud

#### Aktualna gama VPS

Zaloguj się do Twojego [panelu klienta OVHcloud](https://www.ovh.com/auth/?action=gotomanager), wejdź do sekcji `Bare Metal Cloud`{.action} i wybierz Twój serwer na liście nawigacyjnej znajdującej się po lewej stronie, pod `VPS`{.action}. W tej sekcji kliknij `...`{.action} po prawej stronie nazwy serwera VPS w polu "Twój VPS".

![Otwórz KVM](images/kvm-new1.png){.thumbnail}

#### Poprzednia gama VPS

Zaloguj się do Twojego [panelu klienta OVHcloud](https://www.ovh.com/auth/?action=gotomanager), wejdź do sekcji `Bare Metal Cloud`{.action} i wybierz Twój serwer na liście nawigacyjnej znajdującej się po lewej stronie, pod `VPS`{.action}. W tej sekcji kliknij link skrócony o nazwie `KVM`{.action}.

![Kliknij przycisk](images/kvm-new2.png){.thumbnail}

### Korzystanie z konsoli KVM

Otworzy się ekran KVM. Jest to małe okno wskazujące połączenie z serwerem. Ponieważ okno jest dość małe, nawigowanie w interfejsie Twojego serwera za pomocą prętów przewijania może być bardzo trudne. Dlatego zalecamy otwarcie KVM w nowym oknie pełnym ekranem za pomocą przycisku "Otwórz w nowym oknie" w prawym dolnym rogu okna kontekstowego.

> [!primary]
>
> Jeśli masz problemy z podwójnym wpisem, może to być spowodowane automatyczną regulacją ekranu. Zalecamy otwarcie KVM w nowym oknie klikając na przycisk "Otwórz w nowym oknie".
> Jeśli nadal masz problemy z wyświetlaczem, zalecamy usunięcie z adresu URL części "auto". Jeśli adres URL to https://compute.sbg1.cloud.ovh.net:6080/vnc_auto.html?token=xxxxxxxxxxxx, musi się on zmienić na https://compute.sbg1.cloud.ovh.net:6080/vnc.html?token=xxxxxxxxxxxx (link może być inny niż ten podany przykład ilustruje tylko część adresu URL do usunięcia)
>

Połączenie z siecią

> [!primary]
>
> Klawiatura może mieć inny układ niż ty. Upewnij się, że to sprawdzić, ponieważ klawiatura może być AZERTY zamiast QWERTY, na przykład.
>

### Połączenie z KVM przez API

Zdarza się, że napotkasz problemy z połączeniem z KVM za pomocą panelu konfiguracyjnego OVHcloud, zwłaszcza w przypadku starszych wersji. W takim przypadku możesz użyć rozwiązania API. W tym celu zaloguj się przez API [OVHcloud](https://api.ovh.com/).

#### Na serwerze VPS 2014

Jeśli posiadasz serwer VPS 2014, może wystąpić *błąd 1 06*. Przegląd API za pomocą poniższego zaproszenia może rozwiązać ten problem.

> [!api]
>
> @api {POST} /vps/{serviceName}/openConsoleAccess
>
> Parametry połączenia API:
>
>> serviceName
>>> ID serwera VPS, który wygląda jak vpsxxxxx.ovh.net
>> Protokół:
>>> VNC

Pomimo pozytywnego powrotu API połączenie może trwać kilka minut, zanim port zostanie faktycznie otwarty.

Zalecamy użycie jednego z następujących klientów:

- [UltraVnc](https://www.uvnc.com/downloads/ultravnc.html){.external}
- [VNC Viewer](https://www.realvnc.com/en/connect/download/viewer/){.external}

Korzystaj ze szczegółowych informacji dostarczonych przez wywołanie API, aby zdalnie połączyć się z serwerem VPS za pomocą jednego z wyżej wymienionych klientów oprogramowania.

#### Na serwerze VPS 2016

W przypadku problemów z KVM, postępuj zgodnie z poleceniem API dotyczącym dostępu do KVM:

> [!api]
>
> @api {POST} /vps/{serviceName}/getConsoleUrl
>
> Parametry połączenia API:
>
>> serviceName
>>> ID serwera VPS, który wygląda jak vpsxxxxx.ovh.net
>

> [!primary]
>
> Jeśli nadal masz problemy z wyświetlaczem, zalecamy usunięcie z adresu URL części "auto". Jeśli adres URL jest (link dla Ciebie może być inny, przykład ten pokazuje tylko część adresu URL do usunięcia) https://compute.sbg1.cloud.ovh.net:6080/vnc_auto.html?token=xxxxxxxxxxxx to musi stać się https://compute.sbg1.cloud.ovh.net:6080/vnc.html?token=xxxxxxxxxxxx
>

## Sprawdź również

Dołącz do społeczności naszych użytkowników na stronie <https://community.ovh.com>.