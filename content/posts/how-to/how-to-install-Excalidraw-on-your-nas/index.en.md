---
title: "How to Win Back Your Loved One's Heart with the Power of Technology: I Used Excalidraw to Make Her Understand My Heart"
date: 2023-06-27T17:48:41+08:00
categories:
- Nas Tutorial
draft: false
toc: true
---

## 1. Introduction

Do you often find yourself arguing with your girlfriend through text and voice messages on WeChat over some issues?

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305291425520.gif "Pic")

Through the screen and the exchange of information through text, it is inevitable that there will be various "misunderstandings" in understanding.

The consequences are:

- 😒 Minor ones may lead to the girlfriend leaving.
- 😫 Major ones may lead to the breakup of a marriage.

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305291422135.png "Pic")

So what should you do?

At this time, there is nothing that "one (X)" cannot solve.

I'm referring to "a picture." What you need is "a tool" that can clearly depict your thoughts, rather than words or language.

At this time, Excalidraw can perfectly solve your problem.

---

## Case Study

Here is an example of how I resolved an unexpected situation with my girlfriend, Zhijian, using a picture.

Throughout the process, without the need for words, you can understand what happened, perfectly solving the communication problem.

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305291435555.png "Pic")

---

## Introduction to Portainer

Excalidraw is an online drawing tool that allows users to freely draw simple hand-drawn pictures. The features of this tool are:

- Easy to use, without complex functions, very suitable for quick "mind mapping" or "simple illustrations."
- Excalidraw provides basic drawing tools such as lines, shapes, and text, as well as color, size, and other attribute settings. It is very intuitive, and even people without drawing experience can quickly get started.
- Supports "collaboration among multiple people," allowing friends to draw on the same canvas, which is very helpful for team collaboration or remote teaching.
- Powerful "material library" management.

---

## 1. Key Point

"Follow for free" so you won't get lost.

## 2. Installing Portainer

Tutorial reference:
[30-second Installation of Portainer, a Must-Have Tool for Nas](/how-to-install-portainer-in-nas/)

## 3. Creating a Stack

![Alt text](https://mariushosting.com/wp-content/uploads/2022/08/1-Synology-Portainer-Add-Stack.png "Pic")

## 4. Creating a Stack

```yaml
version: "3.9"
services:
  excalidraw:
    container_name: Excalidraw
    healthcheck:
     test: curl -f http://localhost:80/ || exit 1
    image: excalidraw/excalidraw:latest
    ports:
      - 3765:80 # Make sure the port number does not conflict with the original one
    restart: on-failure:5
    stdin_open: true
    environment:
      - NODE_ENV=production
```

1. Select stack.
2. Enter "excalidraw" in the name field.
3. Enter the above code in the editor.
4. Click "deploy."

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305291442842.png "Pic")

## 5. Success

![Alt text](https://mariushosting.com/wp-content/uploads/2023/02/Excalidraw-Synology-NAS-Set-up-3.png "Pic")

## 6. Usage

1. Enter the address in the browser: https://[`nas IP address`]:3765
2. Draw freely.
3. Export (png, svg).

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305291454803.png "Pic")

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305291454150.png "Pic")

## 7. Adding Materials

Excalidraw has a large number of user materials that you can freely add, and they are your own.

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305291455876.png "Pic")

How to add:

1. Click "Browse Materials."
2. Add your favorite materials.

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305291455833.png "Pic")

## Finally

I hope you enjoy this tutorial. If you find it helpful, please remember to like and bookmark it. Feel free to share it with your friends as well.

If you encounter any problems during the setup process or have any suggestions, please leave a comment below. We can discuss and learn together.

If your girlfriend doesn't allow you to buy a NAS, you can tell her that buying a NAS is to love her better 🤣

Follow [Nasdaddy](https://nasdaddy.com) for interesting NAS toys and private cloud deployment.
