---
title: "Das perfekte lokale Lesezeichen-Management für NAS-Nutzer: Eine All-in-One-Lösung für Informationsmanagement - Wie man Hoarder einrichtet und nutzt, um Ihre digitalen Informationen zu verwalten?"
date: 2024-05-26T13:22:49+08:00
categories:
- NAS-Tutorials
draft: false
toc: true
description: Der KI-Lesezeichenordner für NAS-Nutzer
featuredImage: "back.png"
featuredImagePreview: "back.png"
---
Der KI-Lesezeichenordner für NAS-Nutzer
<!--more-->
# Das perfekte lokale Lesezeichen-Management für NAS-Nutzer: Eine All-in-One-Lösung für Informationsmanagement - Wie man Hoarder einrichtet und nutzt, um Ihre digitalen Informationen zu verwalten?

## 1. Einleitung

Heute freue ich mich, allen NAS-Enthusiasten ein `neues Spielzeug` vorzustellen - ein brandneues Lesezeichen- und Notizverwaltungssystem.

Ich habe mich absolut `verliebt` und plane, meinen aktuellen Dienst zu ersetzen.

Ich habe zuvor über meine Nutzung von `linkding` [linkding](/how-to-install-linkding-in-nas/) gesprochen.

![image-20230817175338692](image-20230817175338692.png)

### Warum brauchen Sie einen Lesezeichen-Manager?

In dieser Ära der Informationsüberflutung durchsuchen wir täglich unzählige Informationen auf SMZDM, WeChat-Offiziellen-Konten und im Internet, sei es interessante Artikel, praktische Tools oder flüchtige Inspirationen. Wir hoffen, sie wiederzufinden, wenn wir sie brauchen.

Jedoch können herkömmliche Lesezeichenverwaltungstools nur einen Teil des Problems lösen. Oft `sammeln wir, aber öffnen nie wieder`, was unseren wirklichen Bedürfnissen nach Informationsmanagement nicht gerecht wird.

Aber die heutige Vorstellung von `Hoarder` — einer selbstgehosteten Lesezeichenanwendung, die für Datensammler konzipiert ist, ausgestattet mit `KI-Smart-Tags` und `Volltextsuche`-Fähigkeiten, wird die Art und Weise, wie Sie Informationen sammeln, vollständig verändern.

Stellen Sie sich vor, Sie könnten tiefgründige Artikel, die spät in der Nacht entdeckt wurden, oder Inspirationsbilder, die früh am Morgen begegnet wurden, mit einem Klick speichern, jederzeit und überall zugänglich.

![image-20240526125313648](image-20240526125313648.png)

Als Nächstes werde ich Sie Schritt für Schritt durch die Einrichtung Ihres leistungsstarken Hoarder-Lesezeichen- und Notizverwaltungstools führen.

## Vorstellung von Hoarder

Hoarder ist nicht nur eine selbstgehostete Lesezeichenanwendung; es integriert KI-Technologie, mit dem Ziel, Datensammlern ein ultimatives Informationsmanagement-Erlebnis zu bieten. Hier sind die Kernfunktionen von Hoarder:

- **Lesezeichen setzen, einfache Notizen machen, Bilder speichern**: Eine All-in-One-Lösung für Informationsbedürfnisse.
- **Automatisches Abrufen von Linktiteln, Beschreibungen und Bildern**: Überspringen Sie die mühsame manuelle Bearbeitung, um Effizienz zu steigern.
- **Lesezeichen in Listen organisieren**: Benutzerdefinierte Kategorisierung, einfach umfangreiche Inhalte verwalten.
- **Volltextsuche**: Schnell jeden gespeicherten Inhalt finden, wichtige Informationen nie wieder verlieren.
- **KI-basiertes automatisches Tagging-System**: Verwenden Sie lokale oder Online-Modelle, wie ollama, für intelligentes Tagging, um die Inhaltsorganisation intelligenter zu machen.

![image-20240526121651529](image-20240526121651529.png)

- **Unterstützt Chrome- und Firefox-Erweiterungen**: Schnelles Setzen von Lesezeichen mit einem Klick, nahtlose Integration des Browsererlebnisses.
- **iOS- und Android-Apps**: Verwalten Sie Ihre Informationsbibliothek jederzeit und überall.

![Startseiten-Screenshot](https://github.com/hoarder-app/hoarder/raw/main/screenshots/homepage.png?raw=true)

- **Unterstützung für Nachtmodus**: Schützen Sie Ihre Augen, passen Sie sich verschiedenen Nutzungsumgebungen an.
- **Priorität auf Selbsthosting**: Volle Kontrolle über Ihre Daten und Privatsphäre.

---

Einrichtungsschritte:

## 1. Wichtigster Punkt

`Drücken Sie den kostenlosen Folgen-Button`, um nicht verloren zu gehen.

## 2. Docker-Verwaltungsgrafiktool

#### Für Synology DSM 7.2 und höher können Sie direkt den *Container-Manager* verwenden

![container-manager-1](\images\container-manager-1.png)

#### QNAP ContainerStation 

![container-station-1](\images\container-station-1.png)

![container-station-2](\images\container-station-2.png)

#### Portainer selbst installieren

Tutorial-Referenz:
[Installieren Sie das wesentliche NAS-Tool Portainer in 30 Sekunden](/how-to-install-portainer-in-nas/)

Als Nächstes verwenden wir den Container-Manager von Synology als Beispiel.

##  3. Dateistation

Öffnen Sie den Docker-Ordner in der Dateistation, erstellen Sie einen `hoarder`-Ordner.

![image-20240526111947464](image-20240526111947464.png)

Erstellen Sie der Reihe nach folgende Verzeichnisse:

- web_data
- redis
- meilisearch

![image-20240526112146870](image-20240526112146870.png)

Erstellen Sie eine .env-Datei.

![image-20240526112424470](image-20240526112424470.png)

Inhalt der .env-Datei:

```
HOARDER_VERSION=release
NEXTAUTH_SECRET=AP8jEDXsVZ7bmnO+dQeqDP0uX+Y0yNV/BaQWrDXG/aSCwVSf
MEILI_MASTER_KEY=5BMHyWfjut7F10vbuHR2sGEAeaQEySDLOEzxxXuw+nmpBeb1
NEXTAUTH_URL=http://localhost:3000
# Optional, wenn Sie keine KI zur Kategorisierung benötigen, entfernen Sie die folgenden zwei Zeilen
OPENAI_BASE_URL=https://xxx.com/v1
OPENAI_API_KEY=sk-xxxxx
```

Besondere Konfigurationserklärung:

NEXTAUTH_SECRET: Hauptsächlich bezogen auf den JWT-Schlüssel, generieren Sie ihn mit `openssl rand -base64 36`, oder Sie können meinen direkt kopieren.

MEILI_MASTER_KEY: Wie oben.

Wenn Sie die KI verwenden möchten, um entsprechende Tags zu generieren, müssen Sie die folgenden zwei konfigurieren:

OPENAI_BASE_URL: Konfigurieren Sie Ihren KI-Knoten.

OPENAI_API_KEY: Entsprechender Schlüssel.

Wie wir alle wissen, `können Sie nicht auf OpenAI zugreifen`, also verwende ich Tools wie OneAPI, um meinen eigenen OpenAI-Knoten zu bauen. Dieses Tutorial wird nicht tiefer eintauchen, aber wenn Sie mehr erfahren möchten, können Sie gerne mit mir kommunizieren.

## 4. Container-Manager 

Für diesen Zweck verwende ich den Container-Manager von Synology für die Einrichtung, Portainer und QNAP sind ähnlich:

![image-20240526113540778](image-20240526113540778.png)

Kopieren Sie die folgende Konfiguration:

```
version: "3.8"
services:
  web:
    image: ghcr.io/hoarder-app/hoarder-web:${HOARDER_VERSION:-release}
    restart: unless-stopped
    volumes:
      - /volume1/docker/hoarder/web_data:/data
    ports:
      - 23000:3000
    env_file:
      - .env
    environment:
      REDIS_HOST: redis
      MEILI_ADDR: http://meilisearch:7700
      DATA_DIR: /data
  redis:
    image: redis:7.2-alpine
    restart: unless-stopped
    volumes:
      - /volume1/docker/hoarder/redis:/data
  chrome:
    image: gcr.io/zenika-hub/alpine-chrome:123
    restart: unless-stopped
    command:
      - --no-sandbox
      - --disable-gpu
      - --disable-dev-shm-usage
      - --remote-debugging-address=0.0.0.0
      - --remote-debugging-port=9222
      - --hide-scrollbars
  meilisearch:
    image: getmeili/meilisearch:v1.6
    restart: unless-stopped
    env_file:
      - .env
    environment:
      MEILI_NO_ANALYTICS: "true"
    volumes:
      - /volume1/docker/hoarder/meilisearch:/meili_data
  workers:
    image: ghcr.io/hoarder-app/hoarder-workers:${HOARDER_VERSION:-release}
    restart: unless-stopped
    volumes:
      - /volume1/docker/hoarder/web_data:/data
    env_file:
      - .env
    environment:
      REDIS_HOST: redis
      MEILI_ADDR: http://meilisearch:7700
      BROWSER_WEB_URL: http://chrome:9222
      DATA_DIR: /data
    depends_on:
      web:
        condition: service_started

```

Wie gezeigt einsetzen.

![image-20240526120045059](image-20240526120045059.png)

## 5. Nutzung

Geben Sie das Programm im Browser ein: [ip]:[port]

> Die IP ist die IP Ihres NAS (meine hier ist 172.16.23.106), und der Port ist in der obigen Konfigurationsdatei definiert, was 23000 ist, wenn Sie meinem Tutorial gefolgt sind.

![image-20240526120240066](image-20240526120240066.png)

Nach der Registrierung und Anmeldung,

![image-20240526120513838](image-20240526120513838.png)

Wenn Sie nicht möchten, dass andere Ihren Dienst nutzen,

Nach der Registrierung Ihres Kontos, deaktivieren Sie die Kontoregistrierungsfunktion in der Umgebungsvariablen. Fügen Sie diese Zeile zum .env-Teil hinzu:

DISABLE_SIGNUPS=true

## 6. Besondere Funktionen-Vorstellung

#### Browser-Erweiterung

Suchen Sie nach hoarder.app

![image-20240526120629619](image-20240526120629619.png)

`Konfigurieren Sie Ihre Serveradresse`:

![image-20240526120703992](image-20240526120703992.png)

#### App-Download

iOS

![image-20240526120739062](image-20240526120739062.png)

Android

![image-20240526120802863](image-20240526120802863.png)

#### Nutzung der Browser-Erweiterung

Am Beispiel des Artikels des Community-Modells `Jinsheng Nai Ba's Müllmann`,

Einfach auf den Erweiterungsbutton klicken, um zu sammeln.

![image-20240526121540724](image-20240526121540724.png)

Zurück auf der Web-Seite können Sie sehen, dass der Artikel erfolgreich gesammelt wurde, und er ist bereits von `KI` kategorisiert.

![image-20240526121651529](image-20240526121651529.png)

Hier werden einige `Bilder nicht angezeigt`, wahrscheinlich wegen des `Hotlink-Schutzes` der Plattform.

Hier, wenn ich mein eigenes Open-Source-Projekt social-auto-upload sammle, `sind die Bilder normal`.

![image-20240526123041892](image-20240526123041892.png)

KI-basierte Kategorisierungstags können auch mit `benutzerdefinierten Tags` und `Notizen` ergänzt werden.

Sie können auch umschalten, um `Screenshots zu der Zeit` zu erfassen.

![image-20240526123209809](image-20240526123209809.png)

Das System kann alle Tags sehen, einschließlich KI und Ihren eigenen.

![image-20240526123245287](image-20240526123245287.png)

#### Unterstützt Volltexterkennung

Es unterstützt `Volltextsuche` für alle gesammelten Webseiten oder Notizen. Dies hilft uns zweifellos, schnell das zu finden, was wir aus den gesammelten Notizen und Links wollen.

Zum Beispiel erscheint das Wort `Zufallszahl` in dieser Sammlung:

![image-20240526123439222](image-20240526123439222.png)

Dann können Sie direkt nach `Zufallszahl` in der Suche suchen.

![image-20240526123511861](image-20240526123511861.png)

Versuchen wir diesen sehr spezifischen Begriff: `UGOS`.

![image-20240526123600559](image-20240526123600559.png)

Es hat auch den Artikel gefunden, der `UGOS` erwähnt.

![image-20240526123652148](image-20240526123652148.png)

## Zusammenfassung

Wenn Ihnen dieser Artikel gefallen hat, denken Sie bitte daran, zu liken, zu sammeln und [Papas Digitalen Garten] zu folgen. Wir werden weiterhin mehr praktische Anleitungen zur Selbsthosting-Anwendung bringen. Zusammen nehmen wir die Kontrolle über unsere Daten und erschaffen unsere eigene digitale Welt!

Wenn Sie während des Einrichtungsprozesses auf Probleme stoßen oder Vorschläge haben, zögern Sie nicht, unten einen Kommentar zu hinterlassen. Lassen Sie uns diskutieren und gemeinsam lernen.