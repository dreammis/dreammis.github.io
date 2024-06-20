---
title: "A Must-Have for NAS Experts: A Comprehensive Guide to Easy Document Management with Paperless-ngx"
date: 2023-12-13T12:59:45+08:00
categories:
- NAS Tutorials
draft: false
# url : /posts/xxx  # Specify URL
toc: true
description: Explore Paperless-ngx, the new intelligent document management solution for middle-aged men.
---

## 1. Introduction

After all the tinkering, I realized that `90% of NAS applications are useless`.

![](9058fdc48d0956b6f4f84b29e4a4a940.jpg)

Only `3 or 2` of them are actually useful.

Most of the time, after following various guides and tutorials to set them up, we just `leave them there untouched`.

From the first NAS I had, the Star Snail, to now, after 8 years, I have researched countless self-hosted applications.

The protagonist I am introducing today belongs to the remaining 10% that are actually useful.

To be more precise, it can be considered as the top 1% among this 10% of usefulness.

The benefits it brings me are not only related to life and work, but also to better `document management and file search`.

Thanks to it, I have saved at least `500 hours`.

---

Before formally introducing it, I want to talk about another topic: why I have always been `unable to leave the Apple ecosystem`.

The Apple ecosystem has brought me not only `convenient systems`, `security`, and `smooth integration of all devices`, but also one of the biggest reasons: Apple's powerful `photo-OCR function`.

For example, if I want to find a `chat screenshot` from a conversation I had with a seller a while ago, in order to provide evidence,

Compared to the previous method of searching through each image one by one, I can now simply search for the keyword `screwdriver`. Apple Photos will directly locate the image that contains a `screwdriver`.

![image-20231213105413936](image-20231213105413936.png)

![image-20231213105424615](image-20231213105424615.png)

If you are not familiar with this feature yet, don't rush to try it yourself.

The toy I am introducing to you today can bring you the same:

- The same effect as the Apple feature.
- Hosted on `your NAS`.
- Complete control over your data.

![image-20231213110140424](image-20231213134631394.png)

- It also supports `online preview`:

![image-20231213131049730](image-20231213131049730.png)

- It supports all `digital documents`: Not only images, but also PDFs, Word documents, Excel spreadsheets, and even Markdown files. It truly achieves document digitization, unified management, and efficient search.

![image-20231213110911380](image-20231213110911380.png)

This is the new toy I am bringing to you today, Paperless-ngx. As the name suggests, it is all about going paperless.

It can help you organize your contracts, `physical documents`, bills, and more, while also managing digital documents (Word, Excel, PDF, etc.).

![paperless-ngx-banner](paperless-ngx-banner.png)

---

## Introduction to Paperless-ngx

Paperless-ngx is not just a document management system. It is a complete solution that converts your physical files into searchable online archives, reducing the use of paper. Its core features include:

- **Document organization and indexing**: Organize scanned documents using tags, correspondents, types, and more.
- **OCR text recognition**: Perform optical character recognition on documents to enable text search and selection, even for documents with images.
- **Multi-language support**: Utilize the open-source Tesseract engine to support over 100 languages.
- **Long-term storage format**: Save documents in PDF/A format, designed for long-term storage.
- **Intelligent tagging and classification**: Automatically add tags, correspondents, and document types using machine learning.
- **Wide range of file support**: Support for PDF documents, images, plain text files, Office documents, and more.
- **Customizable file management**: Paperless-ngx manages file names and folders, supporting different configurations.
- **Modern web application**: Customizable dashboard, filters, batch editing, drag and drop upload, custom views, shared links, and more.
- **Full-text search**: Auto-complete, relevance ranking, and highlighting of matched query parts.
- **Email handling**: Import documents from email accounts and configure multiple accounts and rules.
- **Multi-user permission system**: Built-in robust multi-user permission system.
- **Multi-core system optimization**: Parallel processing of multiple documents.

---

Setup Steps:

## 1. Key Points

`Follow for free` to stay on track.

## 2. Docker Management GUI Tools

#### Synology DSM 7.2 or above can directly use *Container Manager*

![container-manager-1](images/container-manager-1.png)

#### QNAP ContainerStation

![container-station-1](images/container-station-1.png)

![container-station-2](images/container-station-2.png)

#### Install Portainer Yourself

Tutorial reference:

[Install Portainer in NAS in 30 seconds](/how-to-install-portainer-in-nas/)

## 3. File Station

- Open File Station and create a `paperless-ngx` folder in the docker folder.

![image-20231212182330224](image-20231212182330224.png)

- Create the following directories inside the `paperless-ngx` folder:
  - consume
  - data
  - export
  - media
  - pgdata
  - redisdata

![image-20231212182342117](image-20231212182342117.png)

## 4. Container Manager

I am using Synology's Container Manager for this setup, but Portainer and QNAP are similar:

### Upload Configuration

![image-20231212182358034](image-20231212182358034.png)

Copy the following configuration:

```yaml
version: "3.4"
services:
  broker:
    image: library/redis:7
    restart: unless-stopped
    volumes:
      - /volume1/docker/paperless-ngx/redisdata:/data

  db:
    image: library/postgres:15
    restart: unless-stopped
    volumes:
      - /volume1/docker/paperless-ngx/pgdata:/var/lib/postgresql/data
    environment:
      POSTGRES_DB: paperless
      POSTGRES_USER: paperless
      POSTGRES_PASSWORD: paperless

webserver:
  image: paperlessngx/paperless-ngx:latest
  restart: unless-stopped
  depends_on:
    - db
    - broker
    - gotenberg
    - tika
  ports:
    - "28000:8000"  # change it if you like
  healthcheck:
    test: ["CMD", "curl", "-fs", "-S", "--max-time", "2", "http://localhost:8000"]
    interval: 30s
    timeout: 10s
    retries: 5
  volumes:
    - /volume1/docker/paperless-ngx/data:/usr/src/paperless/data
    - /volume1/docker/paperless-ngx/media:/usr/src/paperless/media
    - /volume1/docker/paperless-ngx/export:/usr/src/paperless/export
    - /volume1/docker/paperless-ngx/consume:/usr/src/paperless/consume
  environment:
    PAPERLESS_REDIS: redis://broker:6379
    PAPERLESS_DBHOST: db
    PAPERLESS_TIKA_ENABLED: 1
    PAPERLESS_TIKA_GOTENBERG_ENDPOINT: http://gotenberg:3000
    PAPERLESS_TIKA_ENDPOINT: http://tika:9998
    PAPERLESS_OCR_LANGUAGES: chi-sim chi-tra  # change it if you like
    PAPERLESS_OCR_LANGUAGE: eng+chi_sim  # change it if you like
    USERMAP_UID: 0
    USERMAP_GID: 0
    PAPERLESS_TIME_ZONE: Asia/Shanghai  # change it if you like
  dns:
    - 8.8.8.8
    - 8.8.4.4

gotenberg:
  image: gotenberg/gotenberg:7.10
  restart: unless-stopped
  command:
    - "gotenberg"
    - "--chromium-disable-javascript=true"
    - "--chromium-allow-list=file:///tmp/.*"

tika:
  image: apache/tika:latest
  restart: unless-stopped
```

Explanation of the configuration (customizable):

> I have marked the parts in the above file that I think can be modified with "# change it if you like". For the rest of the parts, it is not recommended for beginners to modify.

- webserver's port section: you can change it to another port number such as "`38000:8000`", `do not modify the 8000 at the end`

- PAPERLESS_OCR_LANGUAGES: set the `supported languages` for paperless, chi-sim chi-tra (Simplified Chinese, Traditional Chinese), you can add the language you want, such as jpn

  In addition, the system already includes English, German, Italian, etc.

- PAPERLESS_OCR_LANGUAGE: `default language for OCR`, I have set it to English and Simplified Chinese here

- PAPERLESS_TIME_ZONE: set your time zone

### Wait:

![image-20231212182432126](image-20231212182432126.png)

### Done:

![image-20231212182442058](image-20231212182442058.png)

## 5. Usage

Access the program in the browser: [ip]:[port]

> ip is the IP address of your NAS (mine is 172.16.22.22), and the port is defined in the configuration file above. If you follow my tutorial, it is 28000.

![image-20231213115505007](image-20231213115505007.png)

But it seems that you don't have a username and password yet, so let's `create an account and password`:

Select the webserver container and open the terminal:

![image-20231212182454272](image-20231212182454272.png)

> python3 manage.py createsuperuser

Enter the following information:

- username
- email
- password

![image-20231212182500769](image-20231212182500769.png)

## 6. Special Features Showcase

### Home Page:

![image-20231212182524985](image-20231212182524985.png)

### Test PDF File:

![image-20231212182535297](image-20231212182535297.png)

The text has been extracted:

![image-20231212182553777](image-20231212182553777.png)

#### Online Preview:

![image-20231212182603518](image-20231212182603518.png)

#### Search Function:

![image-20231212182610480](image-20231213134836910.png)

### Images:

![image-20231212182618189](image-20231212182618189.png)

In the edit view, you can see the recognized result and make modifications:

![image-20231212182641514](image-20231212182641514.png)

#### Search:

![image-20231212182625422](image-20231213134930564.png)

### Trying with Word Files:



![image-20231212182740034](image-20231212182740034.png)

![image-20231212182653729](image-20231213135041397.png)

### Other Apps / Support

You can also download third-party app `paperless_app`

![image-20231213123109606](image-20231213123109606.png)

You can also choose to use other scanning apps and then import them into pp (better recognition), such as the free Microsoft Lens

![Screenshot from Microsoft Lens on an iPhone](36f6ef86-6b7c-4c39-bff4-21cc62f1202d.jpg)

![Screenshot from Microsoft Lens on an iPhone](31173df1-6cbb-4e55-ad5f-0041273d89d7.jpg)

You can also choose to connect your physical printer and automatically upload to paperless:

![image-20231213123313667](image-20231213123313667.png)

If you have more ideas, please feel free to share.

## Finally

If you like this article, please remember to like, bookmark, and follow [Dad's Digital Garden](https://example.com). We will continue to bring more practical self-built application guides. Together, let's take control of our own data and create our own digital world!

If you encounter any problems or have any suggestions during the setup process, please feel free to leave a comment below for discussion and learning.
