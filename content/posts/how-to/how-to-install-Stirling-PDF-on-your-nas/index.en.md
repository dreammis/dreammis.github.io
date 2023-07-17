---
title: "NAS Enthusiasts' Gospel, the Ultimate PDF Processing Tool to Enhance the Value of Your NAS!"
date: 2023-06-27T18:30:40+08:00
categories:
- NAS Tutorials
draft: false
toc: true
---

## 1. Introduction

We have all experienced the frustration of dealing with a pile of PDF documents, whether it's merging several PDFs, splitting a PDF file, rearranging pages in a PDF, or any other PDF-related tasks. Online tools you find either bombard you with ads, require payment, or raise concerns about privacy. If you're facing these issues, then the self-hosted PDF processing tool, Stirling-PDF, might be the solution you need.

---

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306121301570.png "Pic")

## Introducing Stirling-PDF

Stirling-PDF is a powerful locally hosted web-based PDF manipulation tool that runs on Docker. It allows you to perform various operations on PDF files, such as splitting, merging, converting, rearranging, adding images, rotating, compressing, and more. It can handle all your PDF needs.

All files and PDFs exist only on the client side, and any downloaded files are deleted from the server at that time.

> You don't have to worry about this service taking up too much space. It's the most hassle-free and space-saving PDF assistant you can find.

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306121302070.gif "Pic")

#### Key Features:

- Full web GUI for merging/splitting/rotating/moving PDFs and their pages.
- Splitting PDF into multiple files
- Merging multiple PDFs into one
- Converting PDF to images and vice versa
- Fixing PDFs
- Detecting and removing blank pages
- Comparing two PDFs and displaying text differences
- Adding images to PDFs
- Rotating PDFs in 90-degree increments
- Compressing PDFs to reduce file size
- Adding and removing passwords
- Adding watermarks
- Converting any common file to PDF
- Converting PDF to Word/Powerpoint/other formats
- Extracting images from PDFs
- Performing OCR on PDFs

---

Alright, enough talk. Let's move on to the specific setup steps:

## 1. Key Point

`Click to follow for free` and never get lost.

## 2. Install Portainer

Tutorial reference:
[Install Portainer, a Must-Have Tool for NAS, in 30 Seconds](/how-to-install-portainer-in-nas/)

## 3. File Station

Open File Station and create a `stirling-pdf` folder in the docker folder.

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306121329615.png "Pic")

## 4. Create Stack

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306061552130.png "Pic")

## 5. Deploy the Code

```yaml
version: '3.3'
services:
  stirling-pdf:
    image: frooodle/s-pdf:latest
    ports:
      - '13260:8080'
    volumes:
      - /volume1/docker/stirling-pdf:/usr/share/tesseract-ocr/4.00/tessdata #Required for extra OCR languages
    environment:
     APP_LOCALE: zh_CN
     APP_HOME_NAME: NasDaddy PDF # Main title for the web interface
     APP_HOME_DESCRIPTION: Dad's PDF Toolbox # Website description
     APP_NAVBAR_NAME: NasDaddy PDF # Title for the navigation page
     APP_ROOT_PATH: /
```

1. Select stack.
2. Enter `stirling-pdf` in the name field.
3. Enter the above code in the editor.
4. Click on deploy.

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306121254282.png "Pic")

## 6. Success

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306061556495.png "Pic")

## 7. Usage

Access the program in your browser: [ip]:[port]

> Replace `[ip]` with the IP address of your NAS (mine is 172.16.23.106 here), and `[port]` with the port defined in the configuration file. If you followed my tutorial, it would be 13260.

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306121255093.png "Pic")

## 8. Chinese Support for OCR

Stirling-PDF has a very powerful OCR function.

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306121320624.gif "Pic")

By applying OCR to the images in the PDF, the text can be extracted, just like this:

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306121321938.png "Pic")

By default, OCR uses the English character library. If we want to support Chinese, we need to download the Chinese training package ourselves:

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306121322707.png "Pic")

1. Download link:

   stirling-pdf-traindata: [Access code: xztp](https://pan.baidu.com/s/1_LguqxLBqWxn5fHJq_IWwQ)

2. There are two training packages available:

   - normal (larger, more comprehensive, slower recognition speed)
   - fast (smaller, more streamlined, faster recognition speed)

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306121340441.png "Pic")

3. Place the training files in the following location:

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306121331819.png "Pic")

## Finally

By building your own Stirling-PDF, you can not only process PDFs anytime and anywhere, but also ensure that your data is always under your control and not accessible to unnecessary third parties.

If you like this article, please remember to like, bookmark, and follow "Dad's Digital Garden". We will continue to bring more practical self-built application guides. Together, let's take control of our own data and create our own digital world!

If you encounter any problems during the setup process or have any suggestions, please feel free to leave a comment below for discussion and learning.