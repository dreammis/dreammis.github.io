---
title: "Ein Universum in NAS: Wie man Github auf NAS ausführt"
date: 2023-06-27T18:28:44+08:00
categories:
- NAS Tutorials
draft: false
toc: true
---

## 1. Einführung

Wenn Sie ein Python-Entwickler sind, der leidenschaftlich an verschiedenen Projekten arbeitet oder eine Person, die gerne Kreationen teilt, benötigen Sie möglicherweise eine Plattform, die es Ihnen ermöglicht, Versionen zu verfolgen und einfach zusammenzuarbeiten. In solchen Fällen könnten Sie öffentliche Cloud-Dienste wie GitHub (die unberechenbare Macht), Gitee oder GitLab verwenden. Möglicherweise sind Sie jedoch besorgt über die Datensicherheit und bevorzugen es, alles unter Ihrer Kontrolle zu haben. Wie können Sie also all diese Anforderungen erfüllen? Die Antwort lautet `Gitea`, ein leistungsstarker, leichtgewichtiger und selbst gehosteter Git-Dienst.

---

## Vorstellung von Gitea

Gitea ist ein Open-Source-Git-Dienst, der als selbst gehostetes GitHub verstanden werden kann. Gitea unterstützt das Selbsthosting, was bedeutet, dass Sie Gitea auf Ihrem eigenen Server bereitstellen und ausführen können. Es bietet eine saubere und benutzerfreundliche Benutzeroberfläche, mit der Benutzer ihre Repositories erstellen, klonen und verwalten können. Insbesondere ist Gitea darauf ausgelegt, einfach und leichtgewichtig zu sein, sodass es auf verschiedenen Plattformen und Umgebungen ausgeführt werden kann.

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306100932342.png "Bild")

Im Vergleich zu ähnlicher Software verfügt Gitea über folgende Funktionen:

- **Leichtgewichtig**: Gitea ist eine sehr leichtgewichtige Anwendung, die minimale Systemressourcen zum Ausführen benötigt. Dies macht es ideal für den persönlichen oder kleinen Teamgebrauch. Mit 3 Jahren Laufzeit und 251 Projekten ist der Ressourcenverbrauch so gering, dass selbst eine Schnecke damit umgehen kann.

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306100935404.png "Bild")

- **Selbst gehostet**: Gitea kann auf Ihrem eigenen Server ausgeführt werden, sodass Sie die volle Kontrolle über Ihre Daten und Dienste haben. Sie müssen sich keine Sorgen um Probleme mit Drittanbieterdiensten wie Datenverlust oder Dienstabschaltung machen.
- **Benutzerfreundlich**: Gitea bietet eine benutzerfreundliche Benutzeroberfläche, mit der Sie Ihren Code einfach verwalten können. Egal, ob Sie ein Programmierer oder ein Nicht-Programmierer sind, Gitea kann Ihnen dabei helfen, Ihre Arbeit effizient zu erledigen.
- **Open Source**: Gitea ist ein Open-Source-Projekt, was bedeutet, dass Sie den Quellcode anzeigen und sogar nach Ihren eigenen Bedürfnissen anpassen können.

Ab Version 1.91 unterstützt Gitea die Funktion "Action". Dies ist eine leistungsstarke Funktion, die Ihren Entwicklungsworkflow automatisiert, z. B. das automatische Erstellen, Testen und Bereitstellen Ihres Codes.

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306100939541.png "Bild")

---

Als nächstes gehen wir die spezifischen Einrichtungsschritte durch:

## 1. Schlüsselpunkt

"Folgen Sie kostenlos", um nicht den Überblick zu verlieren.

## 2. Portainer installieren

Tutorial-Referenz: [30-Sekunden-Installation von Portainer, einem Muss-Have-Tool für NAS](/how-to-install-portainer-in-nas/)

## 3. File Station

Öffnen Sie die File Station und erstellen Sie einen Ordner "Gitea" im Docker-Ordner.

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306100941410.png "Bild")

## 4. Stack erstellen

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306061552130.png "Bild")

## 5. Code bereitstellen

```markdown
```yaml
version: '2'
services:
  gitea:
    image: gitea/gitea:latest
    container_name: gitea
    volumes:
      - /volume1/docker/gitea:/data
      - /etc/localtime:/etc/localtime:ro
    ports:
      - "10011:3000" # http port
      - "2200:22" # ssh port
    restart: always
```

1. Wählen Sie den Stack aus.
2. Geben Sie "gitea" in das Namensfeld ein.
3. Geben Sie den obigen Code in den Editor ein.
4. Klicken Sie auf "Bereitstellen".

## 6. Erfolg

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306061556495.png "Bild")

## 6. Verwendung

Greifen Sie über Ihren Browser auf das Programm zu: [ip]:[port]

> Ersetzen Sie "ip" durch die IP-Adresse Ihres NAS (z. B. 192.168.2.32) und "port" durch den in der Konfigurationsdatei definierten Port (z. B. 10011, wenn Sie meinem Tutorial gefolgt sind).

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306100948705.png "Bild")

## 7. Erstkonfiguration

- Verwenden Sie SQLite

SQLite ist für den leichten Gebrauch ausreichend und erfordert keine große Datenbank wie MySQL oder PostgreSQL.

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306100949012.png "Bild")

- Server-Domain

Wenn Sie nur internen Zugriff benötigen, müssen Sie nichts ändern. Wenn Sie externen Zugriff benötigen, ersetzen Sie die Server-Domain durch Ihre öffentliche IP-Adresse.

Server-Domain: Für internen Zugriff nicht ändern, für externen Zugriff durch Domain ersetzen (z. B. gitea.nasdaddy.cn).

Base URL: Für internen Zugriff nicht ändern, für externen Zugriff durch Domain ersetzen (muss http oder https sein, z. B. https://gitea.nasdaddy.cn).

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306100954477.png "Bild")

- Andere

Sie müssen die E-Mail nicht konfigurieren, verwenden Sie Ihre eigene.

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306100957267.png "Bild")

Konfigurieren Sie das Administrator-Konto.

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306100959307.png "Bild")

- Abschluss

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306100959159.png "Bild")

## 8. Theme ändern

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306101002925.png "Bild")

## 9. Mein Lieblingsfeature (Mirror Clone)

Mit Giteas Ein-Klick-Migration können Sie Repositories (einschließlich Commits, Branches und Tags) von GitHub und anderen Projekten, an denen ich teilgenommen habe, einfach migrieren.

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306101004251.png "Bild")

Zum Beispiel für das beliebte Projekt gpt4free kann der Autor das Repository jederzeit aufgrund von Druck schließen. Also habe ich das Repository in meiner privaten Cloud gespiegelt!

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306101006053.png "Bild")

## Abschließend

Wenn Ihnen dieser Artikel gefällt, denken Sie bitte daran, "Dad's Digital Garden" zu liken, zu bookmarken und zu folgen. Wir werden Ihnen weiterhin praktische Anleitungen zur selbst gehosteten Anwendung bringen. Übernehmen wir die Kontrolle über unsere eigenen Daten und schaffen wir unsere eigene digitale Welt!

Wenn Sie während des Einrichtungsprozesses auf Probleme stoßen oder Vorschläge haben, können Sie gerne einen Kommentar zur Diskussion und zum Lernen hinterlassen.```