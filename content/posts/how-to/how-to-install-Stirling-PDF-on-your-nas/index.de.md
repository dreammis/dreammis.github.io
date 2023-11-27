---
title: "NAS-Enthusiasten-Gospel, das ultimative PDF-Verarbeitungstool zur Steigerung des Werts Ihres NAS!"
date: 2023-06-27T18:30:40+08:00
categories:
- NAS-Tutorials
draft: false
toc: true
---

## 1. Einführung

Wir haben alle die Frustration erlebt, sich mit einem Stapel PDF-Dokumente auseinandersetzen zu müssen, sei es das Zusammenführen mehrerer PDFs, das Aufteilen einer PDF-Datei, das Umordnen von Seiten in einem PDF oder andere PDF-bezogene Aufgaben. Online-Tools bombardieren Sie entweder mit Werbung, erfordern Zahlungen oder werfen Bedenken hinsichtlich der Privatsphäre auf. Wenn Sie mit diesen Problemen konfrontiert sind, könnte das selbst gehostete PDF-Verarbeitungstool Stirling-PDF die Lösung sein, die Sie benötigen.

---

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/img/202306121301570.png "Bild")

## Vorstellung von Stirling-PDF

Stirling-PDF ist ein leistungsstarkes, lokal gehostetes webbasiertes PDF-Manipulationstool, das auf Docker läuft. Es ermöglicht Ihnen verschiedene Operationen an PDF-Dateien durchzuführen, wie z.B. Aufteilen, Zusammenführen, Konvertieren, Umordnen, Hinzufügen von Bildern, Drehen, Komprimieren und vieles mehr. Es kann alle Ihre PDF-Bedürfnisse erfüllen.

Alle Dateien und PDFs existieren nur auf der Client-Seite und alle heruntergeladenen Dateien werden zu diesem Zeitpunkt vom Server gelöscht.

> Sie müssen sich keine Sorgen machen, dass dieser Service zu viel Platz einnimmt. Es ist der einfachste und platzsparendste PDF-Assistent, den Sie finden können.

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/img/202306121302070.gif "Bild")

#### Hauptfunktionen:

- Vollständige webbasierte Benutzeroberfläche zum Zusammenführen/Aufteilen/Drehen/Verschieben von PDFs und deren Seiten.
- Aufteilen von PDFs in mehrere Dateien
- Zusammenführen mehrerer PDFs zu einem
- Konvertieren von PDFs in Bilder und umgekehrt
- Reparieren von PDFs
- Erkennen und Entfernen von leeren Seiten
- Vergleichen von zwei PDFs und Anzeigen von Textunterschieden
- Hinzufügen von Bildern zu PDFs
- Drehen von PDFs in 90-Grad-Schritten
- Komprimieren von PDFs zur Reduzierung der Dateigröße
- Hinzufügen und Entfernen von Passwörtern
- Hinzufügen von Wasserzeichen
- Konvertieren beliebiger gängiger Dateien in PDF
- Konvertieren von PDFs in Word/Powerpoint/andere Formate
- Extrahieren von Bildern aus PDFs
- OCR (Texterkennung) auf PDFs durchführen

---

So, genug geredet. Lassen Sie uns zu den spezifischen Einrichtungsschritten übergehen:

## 1. Schlüsselpunkt

`Klicken Sie hier, um kostenlos zu folgen` und verirren Sie sich nie.

## 2. Portainer installieren

Anleitung zur Referenz:
[Installieren Sie Portainer, ein Muss-Have-Tool für NAS, in 30 Sekunden](/how-to-install-portainer-in-nas/)

## 3. File Station

Öffnen Sie die File Station und erstellen Sie einen Ordner mit dem Namen `stirling-pdf` im Docker-Ordner.

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/img/202306121329615.png "Bild")

## 4. Stack erstellen

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/img/202306061552130.png "Bild")

## 5. Code bereitstellen

```yaml
version: '3.3'
services:
  stirling-pdf:
    image: frooodle/s-pdf:latest
    ports:
      - '13260:8080'
    volumes:
      - /volume1/docker/stirling-pdf:/usr/share/tesseract-ocr/4.00/tessdata #Erforderlich für zusätzliche OCR-Sprachen
    environment:
     APP_LOCALE: zh_CN
     APP_HOME_NAME: NasDaddy PDF # Haupttitel für die Web-Benutzeroberfläche
     APP_HOME_DESCRIPTION: Papas PDF-Werkzeugkasten # Website-Beschreibung
     APP_NAVBAR_NAME: NasDaddy PDF # Titel für die Navigationsseite
     APP_ROOT_PATH: /
```

1. Wählen Sie den Stack aus.
2. Geben Sie `stirling-pdf` im Namensfeld ein.
3. Geben Sie den obigen Code in den Editor ein.
4. Klicken Sie auf Bereitstellen.

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/img/202306121254282.png "Bild")

## 6. Erfolg

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/img/202306061556495.png "Bild")

## 7. Verwendung

Greifen Sie über Ihren Browser auf das Programm zu: [ip]:[port]

> Ersetzen Sie `[ip]` durch die IP-Adresse Ihres NAS (meine ist hier 172.16.23.106) und `[port]` durch den in der Konfigurationsdatei definierten Port. Wenn Sie meiner Anleitung gefolgt sind, wäre es 13260.

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/img/202306121255093.png "Bild")

## 8. Unterstützung für OCR in Chinesisch

Stirling-PDF verfügt über eine sehr leistungsstarke OCR-Funktion.

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/img/202306121320624.gif "Bild")

Durch Anwendung von OCR auf die Bilder im PDF kann der Text extrahiert werden, genau wie hier:

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/img/202306121321938.png "Bild")

Standardmäßig verwendet OCR die englische Zeichenbibliothek. Wenn wir Chinesisch unterstützen möchten, müssen wir das chinesische Trainingspaket selbst herunterladen:

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/img/202306121322707.png "Bild")

1. Download-Link:

   stirling-pdf-traindata: [Zugangscode: xztp](https://pan.baidu.com/s/1_LguqxLBqWxn5fHJq_IWwQ)

2. Es stehen zwei Trainingspakete zur Verfügung:

   - normal (größer, umfassender, langsamere Erkennungsgeschwindigkeit)
   - fast (kleiner, schlanker, schnellere Erkennungsgeschwindigkeit)

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/img/202306121340441.png "Bild")

3. Legen Sie die Trainingsdateien an folgendem Ort ab:

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/img/202306121331819.png "Bild")

## Abschließend

Durch den Aufbau Ihres eigenen Stirling-PDF können Sie nicht nur PDFs jederzeit und überall verarbeiten, sondern auch sicherstellen, dass Ihre Daten immer unter Ihrer Kontrolle sind und für unnötige Dritte nicht zugänglich sind.

Wenn Ihnen dieser Artikel gefällt, denken Sie bitte daran, "Dad's Digital Garden" zu liken, zu bookmarken und zu folgen. Wir werden weiterhin praktische Anleitungen zur Selbstinstallation von Anwendungen bereitstellen. Gemeinsam nehmen wir unsere Daten in die Hand und erschaffen unsere eigene digitale Welt!

Wenn Sie während des Einrichtungsprozesses auf Probleme stoßen oder Vorschläge haben, hinterlassen Sie bitte einen Kommentar für Diskussion und Lernen.