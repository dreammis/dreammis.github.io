---
title: "Building Your RomM Game Library: How to Set Up Your RomM Game Library?"
date: 2023-06-27T18:47:37+08:00
categories:
- NAS Tutorials
draft: false
toc: true
---

## 1. Introduction

If you are like me, a retro game enthusiast who has collected many old game ROMs, but struggles to organize them properly on your NAS, then RomM might be able to solve your problem.

It can manage and organize all your games and can be accessed through a web browser. Additionally, you can enrich your game information using RomM.

![Alt text](https://github.com/zurdi15/romm/raw/master/.github/screenshots/gallery.png "Pic")

---

## Introducing RomM

RomM is a game library manager focused on retro games. You can manage and organize all your games through a web browser. Inspired by Jellyfin, it allows you to manage all your games using a modern interface and enriches your game information using IGDB metadata.

RomM has powerful features and functionalities:

- It can scan your game library (all or by platform) and enrich it with IGDB metadata.
- You can access your game library through your web browser.

![Alt text](https://github.com/zurdi15/romm/raw/master/.github/screenshots/home.png "Pic")

- If the scan results are inaccurate, you can choose matching IGDB results.

![Alt text](https://github.com/zurdi15/romm/raw/master/.github/screenshots/search.png "Pic")

- RomM is compatible with EmuDeck file structure.
- RomM supports multi-file games.
- You can download games directly from your web browser.
- You can edit your game files directly from your web browser.
- RomM supports regions, revisions/versions, and additional tags.
- RomM can use SQLite or MaridDB (default is SQLite).
- Mobile support

![Alt text](https://github.com/zurdi15/romm/raw/master/.github/screenshots/m_gallery.png "Pic")

---

Setup Steps:

## 1. Key Points

`Follow for free` to stay on track

## 2. Install Portainer

Tutorial reference:
[Install Portainer, a Must-Have Tool for NAS, in 30 Seconds](/how-to-install-portainer-in-nas/)

## 3. File Station

Open File Station and navigate to the docker folder, create a `romm` folder

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306262345210.png "Pic")

1. Create a `romm` folder under the docker directory.
2. Under the `romm` folder, create the following subfolders: `database` (I chose SQLite), `resources` (static resources downloaded by RomM, such as covers and descriptions), and `library` (your game directory).

The author provides two supported `directory structures`, and I chose the `first one`:

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306262345528.png "Pic")

## 4. Create an IGDB Account

1. Register on [Twitch](https://dev.twitch.tv/login).
2. Enable two-factor authentication, you can use Google Authenticator [enabled](https://www.twitch.tv/settings/security).

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306262345720.png "Pic")

1. Register your Twitch application on this page [Twitch Developer Portal](https://dev.twitch.tv/console/apps/create).
2. Create a secret key.
3. Copy the client ID and secret key.

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306262345436.png "Pic")

## 5. Create a Stack

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306061552130.png "Pic")

## 6. Deploy the Code

```yaml
version: '3'
services:
  romm:
    image: zurdi15/romm:latest
    container_name: romm
    environment:
      - ROMM_DB_DRIVER=sqlite # Here I chose sqlite, you can choose mysql
      - CLIENT_ID=XXX  # Fill in the client ID from the previous step
      - CLIENT_SECRET=XXX  # Fill in the client secret from the previous step
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

1. Choose stack
2. Enter "romm" in the name field
3. Enter the above code in the editor
4. Click deploy

## 7. Success

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306061556495.png "Pic")

## 8. Usage

Access the program in your browser: [ip]:[port]

> The IP is the IP address of your NAS (mine is 172.16.23.106), and the port is defined in the configuration file above. If you followed my tutorial, it should be 13280.

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306262346663.png "Pic")

## 9. Add ROMs

Place ROM files in the directory you set up earlier, following the specified format.

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306262346631.png "Pic")

## 10. Start scanning

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306262346339.png "Pic")

If the file names are in the correct format, the covers and descriptions will be scanned automatically.

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306262347274.png "Pic")

If the file names are not in the correct format, manual scanning may be required.

Select a ROM.

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306262347280.png "Pic")

After searching, you can select "Rename Rom" to modify the file name.

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306262347425.png "Pic")

## 10. Finally, enjoy

When I feel nostalgic and want to play on my 3DS, I can simply download the ROMs.

Select multiple files, including DLCs, and download them together.

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306262347828.png "Pic")

## Finally

Romm is still not perfect, as it only supports English names and has rigid matching rules.

But there is great potential for the future, and the following features are currently being developed:

1. Online upload
2. Save management
3. Custom covers

I am also interested in this project and intend to contribute to it. In the future, I may:

- Add Chinese language support
- Enable ROM downloads (may use qb, jackett)
- Integrate emulators (the author and many other interested people are working on this)

If you like this article, please remember to like, bookmark, and follow "Dad's Digital Garden". We will continue to bring you more practical self-hosted application guides. Together, let's take control of our own data and create our own digital world!

If you encounter any problems or have any suggestions during the setup process, feel free to leave a comment below. Let's explore and learn together.