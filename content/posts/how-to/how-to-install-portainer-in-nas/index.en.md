---
title: "30-Second Installation of Portainer, a Must-Have Tool for Nas"
date: 2023-05-24T18:32:11+08:00
categories:
- Nas Tutorials
draft: false
---

## Introduction

😒 Have you ever envied others for being able to build so many fun applications while you struggle with "not knowing how to code"?

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305222015365.gif "Pic")

And their so-called "simple tutorials" are like this:

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305221850159.gif "Pic")

Have you ever been intimidated by tutorials that are "too complicated"?

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305221843307.gif "Pic")

Do you wish to make everything "a little simpler"?

Today, I will teach you how to install Portainer, a must-have tool for Nas, in just 30 seconds.

## **How to Build Your Own Weibo**

1. Randomly express your thoughts without worrying about others seeing them.
2. Completely save them on your Nas.
3. Invite your good friends to come and have fun, share funny pictures.

How much trouble do you think this would be? With Portainer, it only takes 2 steps:

## Create a Directory

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305221854783.png "Pic")

## Create a Stack

```yaml
version: "3.0"
services:
  memos:
    image: neosmemo/memos:latest
    container_name: memos
    volumes:
      - /volume1/docker/memos/:/var/opt/memos
    ports:
      - 5230:5230
```

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305221855734.png "Pic")

💕**Done!**

> In the future, this channel will share many interesting and fun private services in Nas, all taught simply using Portainer.

Next, let's get to the point of "how to build Portainer in Synology Nas".

The whole process "does not require any code", just use Synology's ["Task Scheduler"](#task-scheduler).

## Introduction to Portainer
Portainer is a lightweight Docker container management tool.

Its advantages are:

1. UI interface (easy operation)
2. Easy deployment (more useful and fun services will be shared in the future)
3. Multi-platform support (Synology, QNAP, Linux, Windows)
4. Easy management (network, images, containers)

With it, we can easily build various services in Nas. In the future, I will also share various services I have built in Nas, and Portainer is indispensable here.

---

## 1. Key Point

Follow for free, never get lost.

## 2. Install Packages

In Synology Package Center, search for:

1. Docker (for Synology versions below 7.2)
2. Container Manager (for Synology versions 7.2 and above)

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305221520122.png "Pic")

## 3. File Station

Open File Station, go to the "docker" folder, and create a "portainer" folder.

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305221524888.png "Pic")

## 4. Task Scheduler

In Synology "Control Panel", find "Task Scheduler", click on "User-defined script" in "Scheduled Tasks".

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305221525216.png "Pic")

## 5. Installation

First, configure the settings: Schedule Settings -> Task Settings

Paste the code:

```yaml
docker run -d --name=portainer \
-p 8000:8000 \
-p 9000:9000 \
-v /var/run/docker.sock:/var/run/docker.sock \
-v /volume1/docker/portainer:/data \
--restart=always \
portainer/portainer-ce
```

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305221525969.png "Pic")

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305221525125.png "Pic")

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305221525244.png "Pic")

## 6. Run the Script

Click on "Run".

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305221526280.png "Pic")

## 7. Check if it is completed (optional step)

> Due to issues with the domestic network, there may be situations where the image cannot be pulled. Therefore, it is necessary to confirm. If it still doesn't work, you can `set up a domestic source`.

Two verification methods - choose one



![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305221526350.png "Pic")

You can also check if Portainer has been successfully pulled in the `docker suite`

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305221526399.png "Pic")



## 8. Enter Portainer

Set a password

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305221526832.png "Pic")



## 9. Settings

1. Initialize environment variables
2. Set the local IP in the environment variables for easy access (the local IP is the IP address of your local Synology NAS)

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305221527432.png "Pic")

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305221527890.png "Pic")

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305221527142.png "Pic")

## 10. Block ads (optional)

What to do with annoying Business upgrade reminders in Portainer?

Use various browser ad blockers to block them

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305221528554.png "Pic")

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305222008586.png "Pic")

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305221528655.png "Pic")

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202305221528751.png "Pic")



Congratulations, you have entered the brand new NAS world

Follow [Daddy's Digital Garden](https://www.daddycoco.com/)

Share interesting NAS toys and private cloud deployments.