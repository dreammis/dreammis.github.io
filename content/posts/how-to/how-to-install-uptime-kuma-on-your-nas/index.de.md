---
title: "Ein Muss für NAS-Benutzer: Diese Überwachungsmaßnahmen nicht überspringen! So richten Sie Uptime Kuma ein"
date: 2023-10-25T10:21:48+08:00
categories:
- NAS Tutorials
draft: false
# url : /posts/xxx  # URL angeben
toc: true
description: [Das heute vorgestellte Tool ist ein unverzichtbares Werkzeug, das alles überwachen kann, ob es sich um Ihr NAS oder Ihre persönliche Website handelt.]
---
Das heute vorgestellte Tool ist ein unverzichtbares Werkzeug, das alles überwachen kann, ob es sich um Ihr NAS oder Ihre persönliche Website handelt. Und es geht nicht nur um die schöne Benutzeroberfläche, was noch wichtiger ist, ist, dass es bis zu 80 Arten von Benachrichtigungen unterstützt. Im späteren Teil dieses Artikels werden wir Sie auch darüber informieren, wie Sie kostenlose Benachrichtigungen (Slack-Bots) verwenden können, um Sie über dringende Situationen auf dem Laufenden zu halten.
<!--more-->


## 1. Einführung

Haben Sie jemals Angst um die Stabilität Ihres NAS gehabt? Haben Sie jemals festgestellt, dass Ihre Dienste lange Zeit ausgefallen sind, wenn Sie sie benötigen?

Wünschen Sie sich ein leistungsstarkes Tool, das Ihnen jederzeit und überall den Echtzeit-Gesundheitsstatus Ihrer Online-Dienste liefert?

Als NAS-Enthusiast sollten Sie in Betracht ziehen, Ihr eigenes Überwachungstool zu erstellen.

Das heute vorgestellte Tool ist ein unverzichtbares Werkzeug, das alles überwachen kann, ob es sich um Ihr NAS oder Ihre persönliche Website handelt.

![Meine Uptime Kuma-Benutzeroberfläche](image-20231025094855748.png)



Und es geht nicht nur um die schöne Benutzeroberfläche, was noch wichtiger ist, ist, dass es bis zu `80 Arten von Benachrichtigungen` unterstützt. Im späteren Teil dieses Artikels werden wir Sie auch darüber informieren, wie Sie kostenlose Benachrichtigungen (`Slack-Bots`) verwenden können, um Sie über `dringende Situationen` auf dem Laufenden zu halten.

![Slack-Benachrichtigungen](image-20231025095253674.png)



---

## Einführung in Uptime Kuma

Uptime Kuma ist ein benutzerfreundliches, selbst gehostetes Überwachungstool, mit dem Sie den Gesundheitszustand Ihrer Online-Dienste jederzeit und überall in Echtzeit überwachen können. Hier sind seine Hauptfunktionen:

### ⭐ Funktionen

- **Mehrere Überwachungsmethoden**: Unterstützt die Überwachung von HTTP(s), TCP, HTTP(s)-Schlüsselwörtern, HTTP(s)-JSON-Abfragen, Ping, DNS-Einträgen, Benachrichtigungen, Steam-Spielservern, Docker-Containern und mehr.
- **Moderne Benutzeroberfläche**: Bietet ein schönes und responsives UI/UX-Design.
- **Vielfältige Benachrichtigungsmethoden**: Unterstützt Telegram, Discord, Gotify, Slack, Pushover, E-Mail (SMTP) und mehr sowie über 90 andere Benachrichtigungsdienste.
- **Hochfrequente Überwachung**: Unterstützt eine Überwachung alle 20 Sekunden.
- **Unterstützung mehrerer Sprachen**: Erfüllt die Bedürfnisse von Benutzern aus verschiedenen Ländern und Regionen.
- **Mehrere Statusseiten**: Bietet klare und detaillierte Berichte zum Gesundheitszustand des Dienstes.
- **Benutzerdefinierte Domain-Mapping**: Weist die Statusseite einer bestimmten Domain zu.
- **Ping-Diagramme**: Zeigt intuitiv die Änderungen der Ping-Werte für Dienste an.
- **Zertifikatsinformationen**: Überprüft bequem den SSL-Zertifikatsstatus von Diensten.
- **Proxy-Unterstützung**: Überwacht über einen Proxy, um die Privatsphäre und Sicherheit der Überwachung zu gewährleisten.
- **Zwei-Faktor-Authentifizierung**: Erhöht die Sicherheit von Konten.

---

Einrichtungsschritte:

## 1. Wichtiger Punkt

`Folgen Sie kostenlos`, verlaufen Sie sich nicht

## 2. Docker-Verwaltungsoberfläche

#### Synology DSM 7.2 oder höher kann direkt den *Container Manager* verwenden

![Syno Container](images/container-manager-1.png)

#### QNAP ContainerStation

![Container Station](images/container-station-1.png)

![Container Station](images/container-station-2.png)



#### Portainer selbst installieren

Tutorial-Referenz:

[30-Sekunden-Installation des essentiellen Tools Portainer für NAS](/how-to-install-portainer-in-nas/)

Als nächstes verwenden wir Portainer als Beispiel.

## 3. File Station

Öffnen Sie die File Station und erstellen Sie einen Ordner mit dem Namen `Uptime-Kuma` im Docker-Ordner.

![image-20231025095535250](image-20231025095535250.png)

## 4. Erstellen Sie einen Stack

![1 Synology Portainer Stack hinzufügen](images/portainer-slack-add.png)

## 5. Den Code bereitstellen

```yaml
version: '3.3'

services:
  uptime-kuma:
    image: louislam/uptime-kuma:1
    container_name: uptime-kuma
    volumes:
      - /volume1/docker/uptime-kuma/data:/app/data
      - //var/run/docker.sock:/var/run/docker.sock  # Fügen Sie diese Zeile hinzu, wenn Sie Docker-Container überwachen müssen
    ports:
      - 3001:3001
    restart: always
    
```

1. Wählen Sie den Stack aus.
2. Geben Sie `Uptime-Kuma` im Namensfeld ein.
3. Geben Sie den obigen Code im Editor ein.
4. Klicken Sie auf Bereitstellen.

## 6. Erfolg

![portainer-slack-add-success](images/portainer-slack-add-success.png)

## 7. Verwendung

Greifen Sie über Ihren Browser auf das Programm zu: [ip]:[port]

> Ersetzen Sie `ip` durch die IP-Adresse Ihres NAS (in diesem Fall ist meine 172.16.22.73) und ersetzen Sie `port` durch den in der Konfigurationsdatei definierten Port (wenn Sie meinem Tutorial gefolgt sind, ist es 3001).

![image-20231025095836150](image-20231025095836150.png)

## 8. Sonstiges

### Wie man Überwachung hinzufügt

Sie können Ihre Überwachungsparameter und Wiederholungseinstellungen nach Bedarf anpassen.

![image-20231025100007245](image-20231025100007245.png)

### Wie man Benachrichtigungen konfiguriert

Uptime Kuma unterstützt fast alle gängigen Benachrichtigungsmethoden, einschließlich nationaler wie Feishu und WeChat Work.

Hier zeige ich Ihnen nur, wie Sie Slack-Benachrichtigungen (kostenlos) einrichten können.

#### Slack

> Ich werde nicht zeigen, wie man ein Slack-Konto erstellt. Die folgenden Schritte konzentrieren sich auf das Erstellen eines Slack-Bots und das Senden von Benachrichtigungen.

1. Erstellen Sie eine Slack-App

https://api.slack.com/apps/new

![image-20231025100352521](image-20231025100352521.png)

2. Wählen Sie Ihren Arbeitsbereich aus

![image-20231025100411844](image-20231025100411844.png)

3. Richten Sie einen Webhook ein

![image-20231025100435840](image-20231025100435840.png)

4. Aktivieren Sie den Bot

![image-20231025100450202](image-20231025100450202.png)

5. Richten Sie den Benachrichtigungskanal ein (erstellen Sie zuerst den Kanal)

![image-20231025100540427](image-20231025100540427.png)

6. Kopieren Sie schließlich die Webhook-URL

![image-20231025100604397](image-20231025100604397.png)

7. Setzen Sie die Slack-Benachrichtigungs-URL in Uptime

![image-20231025100656642](image-20231025100656642.png)

## Zum Schluss

Jetzt kennen Sie die leistungsstarken Funktionen und Verwendungsmöglichkeiten von Uptime Kuma. Warum versuchen Sie nicht, Ihr eigenes Überwachungstool zu erstellen?

Wenn Ihnen dieser Artikel gefallen hat, denken Sie bitte daran, [Dad's Digital Garden](https://example.com) zu liken, zu bookmarken und zu folgen. Wir werden Ihnen weiterhin praktische Anleitungen zur Erstellung eigener Anwendungen bieten. Übernehmen wir die Kontrolle über unsere eigenen Daten und schaffen wir unsere eigene digitale Welt!

Wenn Sie während des Einrichtungsprozesses auf Probleme stoßen oder Vorschläge haben, können Sie gerne einen Kommentar hinterlassen, um zu diskutieren und zu lernen.