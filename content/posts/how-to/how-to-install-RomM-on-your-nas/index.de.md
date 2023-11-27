---
title: "Aufbau Ihrer RomM-Spielsammlung: Wie richten Sie Ihre RomM-Spielsammlung ein?"
date: 2023-06-27T18:47:37+08:00
categories:
- NAS-Tutorials
draft: false
toc: true
---

## 1. Einführung

Wenn Sie wie ich ein Retro-Spiel-Enthusiast sind, der viele alte Spiel-ROMs gesammelt hat, aber Schwierigkeiten hat, sie ordnungsgemäß auf Ihrem NAS zu organisieren, dann kann Ihnen RomM möglicherweise bei Ihrem Problem helfen.

Es kann Ihre Spiele verwalten und organisieren und über einen Webbrowser darauf zugegriffen werden. Darüber hinaus können Sie Ihre Spielinformationen mit RomM bereichern.

![Alt-Text](https://github.com/zurdi15/romm/raw/master/.github/screenshots/gallery.png "Bild")

---

## Vorstellung von RomM

RomM ist ein Spielebibliotheksmanager, der sich auf Retro-Spiele konzentriert. Sie können alle Ihre Spiele über einen Webbrowser verwalten und organisieren. Inspiriert von Jellyfin ermöglicht es Ihnen, alle Ihre Spiele mit einer modernen Benutzeroberfläche zu verwalten und Ihre Spielinformationen mit IGDB-Metadaten zu bereichern.

RomM verfügt über leistungsstarke Funktionen und Möglichkeiten:

- Es kann Ihre Spielebibliothek (alle oder nach Plattform) scannen und mit IGDB-Metadaten anreichern.
- Sie können auf Ihre Spielebibliothek über Ihren Webbrowser zugreifen.

![Alt-Text](https://github.com/zurdi15/romm/raw/master/.github/screenshots/home.png "Bild")

- Wenn die Scanergebnisse ungenau sind, können Sie passende IGDB-Ergebnisse auswählen.

![Alt-Text](https://github.com/zurdi15/romm/raw/master/.github/screenshots/search.png "Bild")

- RomM ist mit der EmuDeck-Dateistruktur kompatibel.
- RomM unterstützt Spiele mit mehreren Dateien.
- Sie können Spiele direkt über Ihren Webbrowser herunterladen.
- Sie können Ihre Spieldateien direkt über Ihren Webbrowser bearbeiten.
- RomM unterstützt Regionen, Revisionen/Versionen und zusätzliche Tags.
- RomM kann SQLite oder MaridDB verwenden (Standard ist SQLite).
- Unterstützung für Mobilgeräte

![Alt-Text](https://github.com/zurdi15/romm/raw/master/.github/screenshots/m_gallery.png "Bild")

---

Einrichtungsschritte:

## 1. Schlüsselpunkte

`Folgen Sie kostenlos`, um auf dem Laufenden zu bleiben

## 2. Portainer installieren

Tutorial-Referenz:
[Installieren Sie Portainer, ein unverzichtbares Tool für NAS, in 30 Sekunden](/how-to-install-portainer-in-nas/)

## 3. File Station

Öffnen Sie die File Station und navigieren Sie zum Docker-Ordner, erstellen Sie einen `romm`-Ordner

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/202306262345210.png "Bild")

1. Erstellen Sie einen `romm`-Ordner unter dem Docker-Verzeichnis.
2. Erstellen Sie unter dem `romm`-Ordner die folgenden Unterordner: `database` (Ich habe SQLite gewählt), `resources` (statische Ressourcen, die von RomM heruntergeladen werden, wie Cover und Beschreibungen) und `library` (Ihr Spieleverzeichnis).

Der Autor bietet zwei unterstützte `Verzeichnisstrukturen` an, und ich habe die `erste` gewählt:

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/202306262345528.png "Bild")

## 4. Erstellen Sie ein IGDB-Konto

1. Registrieren Sie sich auf [Twitch](https://dev.twitch.tv/login).
2. Aktivieren Sie die Zwei-Faktor-Authentifizierung, Sie können Google Authenticator [aktivieren](https://www.twitch.tv/settings/security).

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/202306262345720.png "Bild")

1. Registrieren Sie Ihre Twitch-Anwendung auf dieser Seite [Twitch Developer Portal](https://dev.twitch.tv/console/apps/create).
2. Erstellen Sie einen geheimen Schlüssel.
3. Kopieren Sie die Client-ID und den geheimen Schlüssel.

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/202306262345436.png "Bild")

## 5. Erstellen Sie einen Stack

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/img/202306061552130.png "Bild")

## 6. Den Code bereitstellen

```yaml
version: '3'
services:
  romm:
    image: zurdi15/romm:latest
    container_name: romm
    environment:
      - ROMM_DB_DRIVER=sqlite # Hier habe ich sqlite gewählt, Sie können mysql wählen
      - CLIENT_ID=XXX  # Füllen Sie die Client-ID aus dem vorherigen Schritt ein
      - CLIENT_SECRET=XXX  # Füllen Sie den geheimen Schlüssel aus dem vorherigen Schritt ein
    volumes:
      - '/volume1/docker/library:/romm/library'
      - '/volume1/docker/resources:/romm/resources'
      - '/volume1/docker/database:/romm/database'
    dns:
      - 8.8.8.8
    ports:
      - 13280:80
    restart: "unless-stopped"
```

1. Wählen Sie Stack aus
2. Geben Sie "romm" in das Namensfeld ein
3. Geben Sie den obigen Code in den Editor ein
4. Klicken Sie auf Bereitstellen

## 7. Erfolg

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/img/202306061556495.png "Bild")

## 8. Verwendung

Greifen Sie über Ihren Browser auf das Programm zu: [IP]:[Port]

> Die IP ist die IP-Adresse Ihres NAS (meine ist 172.16.23.106) und der Port ist in der obigen Konfigurationsdatei definiert. Wenn Sie meinem Tutorial gefolgt sind, sollte es 13280 sein.

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/202306262346663.png "Bild")

## 9. ROMs hinzufügen

Platzieren Sie ROM-Dateien im zuvor eingerichteten Verzeichnis gemäß dem angegebenen Format.

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/202306262346631.png "Bild")

## 10. Starten Sie den Scan

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/202306262346339.png "Bild")

Wenn die Dateinamen im richtigen Format vorliegen, werden die Cover und Beschreibungen automatisch gescannt.

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/202306262347274.png "Bild")

Wenn die Dateinamen nicht im richtigen Format sind, ist möglicherweise ein manueller Scan erforderlich.

Wählen Sie ein ROM aus.

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/202306262347280.png "Bild")

Nach der Suche können Sie "Rename Rom" auswählen, um den Dateinamen zu ändern.

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/202306262347425.png "Bild")

## 10. Schließlich, viel Spaß

Wenn ich nostalgisch bin und auf meinem 3DS spielen möchte, kann ich einfach die ROMs herunterladen.

Wählen Sie mehrere Dateien, einschließlich DLCs, aus und laden Sie sie zusammen herunter.

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/202306262347828.png "Bild")

## Schließlich

Romm ist noch nicht perfekt, da es nur englische Namen unterstützt und starre Übereinstimmungsregeln hat.

Aber es gibt großes Potenzial für die Zukunft, und die folgenden Funktionen werden derzeit entwickelt:

1. Online-Upload
2. Speicherverwaltung
3. Benutzerdefinierte Cover

Auch ich interessiere mich für dieses Projekt und beabsichtige, dazu beizutragen. In Zukunft könnte ich:

- Unterstützung für die chinesische Sprache hinzufügen
- ROM-Downloads aktivieren (könnte qb, jackett verwenden)
- Emulatoren integrieren (der Autor und viele andere interessierte Personen arbeiten daran)

Wenn Ihnen dieser Artikel gefällt, denken Sie bitte daran, "Dad's Digital Garden" zu mögen, zu bookmarken und zu folgen. Wir werden Ihnen weiterhin praktische Anleitungen zur Selbsthosting-Anwendung bringen. Gemeinsam nehmen wir unsere Daten in die Hand und schaffen unsere eigene digitale Welt!

Wenn Sie während des Einrichtungsprozesses auf Probleme stoßen oder Vorschläge haben, können Sie gerne einen Kommentar hinterlassen. Lassen Sie uns gemeinsam erkunden und lernen.