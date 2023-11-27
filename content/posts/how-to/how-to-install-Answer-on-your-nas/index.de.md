---
title: "Upgrade your NAS: Build a Knowledge Sharing Platform with Answer for the Best Customer Experience"
date: 2023-06-27T18:38:52+08:00
categories:
- NAS Tutorials
draft: false
toc: true
---

## 1. Introduction

Do you want to have a place where you can record your own questions?

Do you want to have a place similar to Zhihu (Q&A) to use with your friends or clients?

Perhaps you need a platform to communicate, record, and solve these questions, helping them better communicate with friends and helping clients understand your products or services.

Today, we will build a Zhihu-like platform called Answer on your NAS.

![Alt text](https://noted.lol/content/images/2023/01/answer-self-hosted-screenshots.png "Pic")

---

## Introduction to Answer

Answer is an open-source knowledge-based community software. With it, you can quickly build your Q&A community, not only for technical support of products but also for customer support, user communication, etc. If you are looking for a simple way to interact with customers and users, Answer may be the tool you are looking for.

**Features:**

1. **Open-source**: This means you can use Answer for free and there are plenty of developers and communities to support it. You can customize it according to your needs.
2. **Knowledge-based community**: Unlike general forums, Answer is designed to answer questions. It can help you quickly find the answers you need and improve efficiency.
3. **Product technical support**: If your product has technical issues, you can provide answers through Answer. This can help your customers better understand and use your products.
4. **Customer support**: You can collect and answer customer questions through Answer. This can not only help you understand your customers but also improve customer satisfaction.
5. **User communication**: Answer can also serve as a platform for user communication. Your users can help each other, share experiences, and provide suggestions.
6. **Random thoughts**: Of course, you can completely use it as a place for random thoughts (that's how I use it).
7. **Markdown support**

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306161511879.png "Pic")

---

Next is the main course: the setup steps.

## 1. Key Points

`Follow for free` to avoid getting lost.

## 2. Install Portainer

Tutorial reference:

[30-second Installation of Portainer, a Must-have Tool for NAS](/how-to-install-portainer-in-nas/)

## 3. File Station

Open the docker folder in File Station and create an `answer` folder.

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306161511165.png "Pic")

## 4. Create Stack

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306061552130.png "Pic")

## 5. Deploy Code

```yaml
version: "3"
services:
  answer:
    image: answerdev/answer
    ports:
      - '9080:80'
    restart: on-failure
    volumes:
      - /volume1/docker/answer:/data
```

1. Select stack.
2. Enter "answer" in the name field.
3. Enter the above code in the editor.
4. Click "Deploy".

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306161511349.png "Pic")

## 6. Success

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306061556495.png "Pic")

## 7. Usage

Access the program in your browser: [ip]:[port]

> The IP is the IP address of your NAS (mine is 172.16.23.106 here), and the port is defined in the configuration file above. If you followed my tutorial, it would be 9080.

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306161512990.png "Pic")

## 8. Configuration

### Konfiguration der Datenbank

Verwenden Sie einfach SQLite. Wenn Ihr Unternehmen es verwendet, empfehlen wir MySQL oder PostgreSQL.

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/202306301702433.png "Bild")

Nächster Schritt

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/img/202306161513642.png "Bild")

Grundkonfiguration

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/img/202306161515259.png "Bild")

## 9. Verwendung

Neue Frage erstellen (unterstützt Markdown):

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/img/202306161516244.png "Bild")

- Listenansicht:

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/img/202306161516186.png "Bild")

- Detailansicht:

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/img/202306161516294.png "Bild")

### Thema einstellen

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/img/202306161518887.png "Bild")

### Administrationsbereich

![Alt-Text](https://img-nasdaddy.liuxingoo.cn/img/202306161518719.png "Bild")

## Zum Schluss

Wenn Ihnen dieser Artikel gefallen hat, vergessen Sie nicht, ihn zu mögen, zu speichern und 【老爸的数字花园】 zu folgen. Wir werden weiterhin praktische Anleitungen zur Selbstinstallation von Anwendungen bereitstellen. Lassen Sie uns gemeinsam unsere Daten beherrschen und unsere digitale Welt erschaffen!

Wenn Sie während des Installationsprozesses auf Probleme stoßen oder Vorschläge haben, hinterlassen Sie bitte unten einen Kommentar. Lassen Sie uns gemeinsam diskutieren und lernen.