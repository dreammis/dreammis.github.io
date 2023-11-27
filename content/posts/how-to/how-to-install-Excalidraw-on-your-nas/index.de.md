---
title: "Wie man das Herz seiner geliebten Person mit der Kraft der Technologie zurückgewinnt: Ich habe Excalidraw verwendet, um ihr mein Herz zu erklären"
date: 2023-06-27T17:48:41+08:00
categories:
- Nas Tutorials
draft: false
toc: true
---

## 1. Einleitung

Streiten Sie sich oft mit Ihrer Freundin über Text- und Sprachnachrichten auf WeChat über bestimmte Probleme?

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/img/202305291425520.gif "Bild")

Durch den Bildschirm und den Austausch von Informationen über Text ist es unvermeidlich, dass es verschiedene "Missverständnisse" beim Verstehen gibt.

Die Konsequenzen sind:

- 😒 Kleinere können dazu führen, dass die Freundin geht.
- 😫 Größere können zur Trennung einer Ehe führen.

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/img/202305291422135.png "Bild")

Was sollten Sie also tun?

In solchen Momenten gibt es nichts, was "eins (X)" nicht lösen kann.

Ich meine "ein Bild". Sie benötigen "ein Werkzeug", das Ihre Gedanken klar darstellen kann, anstatt Worte oder Sprache.

In solchen Momenten kann Excalidraw Ihr Problem perfekt lösen.

---

## Fallstudie

Hier ist ein Beispiel, wie ich eine unerwartete Situation mit meiner Freundin Zhijian mithilfe eines Bildes gelöst habe.

Während des gesamten Prozesses, ohne Worte zu benötigen, können Sie verstehen, was passiert ist und das Kommunikationsproblem perfekt lösen.

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/img/202305291435555.png "Bild")

---

## Einführung in Portainer

Excalidraw ist ein Online-Zeichenwerkzeug, mit dem Benutzer frei einfache handgezeichnete Bilder zeichnen können. Die Funktionen dieses Werkzeugs sind:

- Einfache Bedienung ohne komplexe Funktionen, sehr geeignet für schnelles "Mind Mapping" oder "einfache Illustrationen".
- Excalidraw bietet grundlegende Zeichenwerkzeuge wie Linien, Formen und Text sowie Farb-, Größen- und andere Attributseinstellungen. Es ist sehr intuitiv und auch für Personen ohne Zeichenerfahrung leicht verständlich.
- Unterstützt "Zusammenarbeit mehrerer Personen", sodass Freunde auf der gleichen Leinwand zeichnen können. Dies ist sehr hilfreich für Teamarbeit oder Fernunterricht.
- Leistungsstarke Verwaltung der "Materialbibliothek".

---

## 1. Schlüsselpunkt

"Folgen Sie kostenlos", damit Sie nicht verloren gehen.

## 2. Installation von Portainer

Anleitung:
[30-Sekunden-Installation von Portainer, einem Muss für Nas](/how-to-install-portainer-in-nas/)

## 3. Erstellen eines Stacks

![Alt-Text](https://mariushosting.com/wp-content/uploads/2022/08/1-Synology-Portainer-Add-Stack.png "Bild")

## 4. Erstellen eines Stacks

```yaml
version: "3.9"
services:
  excalidraw:
    container_name: Excalidraw
    healthcheck:
     test: curl -f http://localhost:80/ || exit 1
    image: excalidraw/excalidraw:latest
    ports:
      - 3765:80 # Stellen Sie sicher, dass die Portnummer nicht mit der Originalen in Konflikt gerät
    restart: on-failure:5
    stdin_open: true
    environment:
      - NODE_ENV=production
```

1. Wählen Sie den Stack aus.
2. Geben Sie "excalidraw" in das Namensfeld ein.
3. Geben Sie den obigen Code in den Editor ein.
4. Klicken Sie auf "Bereitstellen".

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/img/202305291442842.png "Bild")

## 5. Erfolg

![Alt-Text](https://mariushosting.com/wp-content/uploads/2023/02/Excalidraw-Synology-NAS-Set-up-3.png "Bild")

## 6. Verwendung

1. Geben Sie die Adresse im Browser ein: https://[`NAS-IP-Adresse`]:3765
2. Zeichnen Sie frei.
3. Exportieren Sie (png, svg).

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/img/202305291454803.png "Bild")

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/img/202305291454150.png "Bild")

## 7. Material hinzufügen

Excalidraw verfügt über eine große Anzahl von Benutzermaterialien, die Sie frei hinzufügen können, und sie gehören Ihnen.

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/img/202305291455876.png "Bild")

Wie man hinzufügt:

1. Klicken Sie auf "Material durchsuchen".
2. Fügen Sie Ihre Lieblingsmaterialien hinzu.

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/img/202305291455833.png "Bild")

## Abschließend

Ich hoffe, Ihnen hat dieses Tutorial gefallen. Wenn Sie es hilfreich fanden, denken Sie bitte daran, es zu mögen und zu bookmarken. Teilen Sie es auch gerne mit Ihren Freunden.

Wenn Sie während des Einrichtungsprozesses auf Probleme stoßen oder Vorschläge haben, hinterlassen Sie bitte einen Kommentar unten. Wir können diskutieren und gemeinsam lernen.

Wenn Ihre Freundin Ihnen nicht erlaubt, ein NAS zu kaufen, können Sie ihr sagen, dass der Kauf eines NAS dazu dient, sie besser zu lieben 🤣

Folgen Sie [Nasdaddy](https://nasdaddy.com) für interessante NAS-Spielzeuge und die Bereitstellung einer privaten Cloud.