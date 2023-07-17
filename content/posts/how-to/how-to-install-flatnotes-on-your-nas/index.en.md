---
title: "Simple, Clean, Ad-Free Niche Free Note-taking App: Self-built Tutorial for Flatnotes on NAS"
date: 2023-06-27T17:59:52+08:00
categories:
- NAS Tutorial
draft: false
toc: true
lightgallery: true
---

## 1. Introduction

There are countless note-taking apps, such as Apple Notes, Evernote, Obsidian, Notion... even WeChat's file transfer assistant.

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306060920807.png "Pic")

They all have their own advantages and disadvantages:

- Slow speed and requires internet connection (Notion)
- Built-in note app on smartphones (does not support Markdown, not suitable for long texts)
- Bulky and data stored in the cloud (Notion, Evernote)
- Unable to record notes anytime (Evernote)

Today's protagonist is `Flatnotes`, which is simple, focused, privately hosted, with dual editors for Markdown and rich text, and full-text search.

---

- ## Introduction to Flatnotes

  Flatnotes is a powerful and simple, focused note-taking app.

  ### 1. Markdown/Rich Text `Dual Editor`

  It provides both raw Markdown editing mode and WYSIWYG (What You See Is What You Get) Markdown editing mode.

  ![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306060923631.png "Pic")


  ### 2. Advanced Search

  With Flatnotes' `advanced search` feature, you can easily find your notes without manually searching through a large number of notes.

  ![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306060924617.png "Pic")

  ### 3. Custom Tags

  With the tagging feature, you can better organize and categorize your notes. Simply add one or more `tags` to easily find specific notes.

  ![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306060929248.png "Pic")

  ![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306060929310.png "Pic")

  ### 4. Light/Dark Themes

  Flatnotes offers both `light and dark themes` to suit your preferences and keep your eyes comfortable even after long-term use.

  ![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306060930206.png "Pic")

---

Let's set it up step by step:

## 1. Key Points

`Follow for free` to stay on track

## 2. Install Portainer

Tutorial reference:
[30-second Installation of Portainer, a Must-have Tool for NAS](/how-to-install-portainer-in-nas/)

##  3. File Station

Open File Station and create a `flatnotes` folder in the Docker folder.

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306060936127.png "Pic")

## 3. Create Stack

![Alt text](https://mariushosting.com/wp-content/uploads/2022/08/1-Synology-Portainer-Add-Stack.png "Pic")

## 4. Create Stack

```yaml
version: "3"

services:
  flatnotes:
    container_name: flatnotes
    image: dullage/flatnotes:latest
    environment:
      FLATNOTES_AUTH_TYPE: "password" # Password mode (optional: None for no password, TOTP)
      FLATNOTES_USERNAME: "user"
      FLATNOTES_PASSWORD: "changeMe!" # Password can be modified
      FLATNOTES_SECRET_KEY: "aLongRandomSeriesOfCharacters"
    volumes:
      - "/volume1/docker/flatnotes:/app/data"
      # - "./index:/app/data/.flatnotes"  
      # Optional: specify the existing note directory
    ports:
      - "13326:8080" # Custom port, use a port different from others
    restart: unless-stopped
```

1. Select Stack
2. Enter "flatnotes" in the name field
3. Enter the above code in the editor
4. Click deploy

## 5. Success

![Alt text](https://mariushosting.com/wp-content/uploads/2023/02/Excalidraw-Synology-NAS-Set-up-3.png "Pic")



## 6. Usage

1. Open the program in your browser: [ip]:[port]

> The IP address for your NAS is the IP address where your NAS is located (in this case, mine is 172.16.23.106), and the port is defined in the configuration file above. If you followed my tutorial, it would be 13326.

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306060944832.png "Pic")

## 7. Enjoy

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306060944583.png "Pic")

## Finally

If you liked this article, please remember to like, bookmark, and follow [Dad's Digital Garden](https://img-nasdaddy.liuxingoo.cn/img/202306060944583.png). We will continue to bring you more practical self-built application guides. Together, let's take control of our own data and create our own digital world!

If you encounter any problems during the setup process or have any suggestions, please feel free to leave a comment below. Let's explore and learn together.