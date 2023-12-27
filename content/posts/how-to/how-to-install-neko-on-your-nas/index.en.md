---
title: "Living in the Nas Browser: How to Create a Secure and Happy Tech Life with Neko"
date: 2023-12-27T11:17:18+08:00
categories:
- Nas Tutorial
draft: false
# url : /posts/xxx  # Specify URL
toc: true
description: n.eko, a virtual browser running in Docker
---

## 1. Introduction

Those who are familiar with me know that I do not write articles for the sake of it, nor do I follow trends. I only share things that I find useful and that may be useful to you.

Today's toy is no exception. Neko is a virtual browser that runs in Docker...

> 

![img](logo.png)

It is not only an essential part of my Nas service, but also a bond between me, my friends, and my family. Let me explain...

For my Nas, I use it to:

1. `Virtual Browser`

This reason alone explains a lot.

You see, many people choose to buy a Nas because of its built-in browser 😄, Synology still doesn't have one...

But now you can have a virtual browser on any device.

2. `Secure Access`

Many times, there are many services within the home network, but I don't want all of them to be exposed to the public network. The more services exposed to the public network, the more potential risks there are.

With Neko set up on the internal network, I can easily manage and access internal services through it.

![image-20231227094106038](image-20231227094106038.png)

3. `Privacy + Never Stops`

I think this doesn't need much explanation. A private, always-on browser can do a lot.

![image-20231227094632304](image-20231227094632304.png)

4. `Happiness in a Group`

Interestingly, Neko is not limited to just a virtual browser. It can even be a multi-functional social collaboration platform.

You can use it to:

- Chat and watch TV shows or anime with family and friends
- Discuss and hold meetings with colleagues and friends
- You can even use it for training and education

The tool is `only as good as how you use it`...

![image-20231227094917201](image-20231227094917201.png)

5. `Double the Happiness`: More than just a browser

Neko is not just a browser. With the help of tools like VLC, it can become your home TV.

![image-20231227095210202](image-20231227095210202.png)

![image-20231227095246937](image-20231227095246937.png)

Alright, let's get to the main course.

Due to limited space, this article does not cover:

- Public network access
- Special networks
- Complex home networks, etc.

It is limited to setting up on the internal network.

If you encounter such problems, you can leave a comment or seek help in the community.

---

## Introduction to Neko

Neko is not just a simple private browser. Its uniqueness lies in:

1. **Multi-user experience**: Supports multiple users online at the same time, allowing family members and colleagues to share and collaborate on the same platform.
2. **Rich application support**: In addition to browsers, various Linux applications such as VLC can also be run to meet entertainment and work needs.
3. **Social and interactive**: Provides real-time communication and collaboration functions, creating a new type of online social experience.
4. **Privacy and security**: All operations are completed in a secure container to protect your data and privacy.
5. **Personalized customization**: Users can customize Neko according to their personal needs, suitable for various scenarios such as personal entertainment, team collaboration, or education and training.

6. **File transfer**: You can transfer files while interacting with friends and family.

![image-20231227100335804](image-20231227100335804.png)

Supported browsers (both familiar and unfamiliar):

![image-20231227100050949](image-20231227100050949.png)

---

Setup steps:

## 1. Key Points

`Follow for free` to avoid getting lost.

## 2. Docker management graphical tool

#### Synology DSM 7.2 or above can directly use *Container Manager*

![container-manager-1](images/container-manager-1.png)

#### QNAP ContainerStation

![container-station-1](images/container-station-1.png)

![container-station-2](images/container-station-2.png)

#### Install Portainer by yourself

Tutorial reference:

[30-second installation of Portainer, a must-have tool for NAS](/how-to-install-portainer-in-nas/)

Next, let's take Synology as an example.

## 3. File Station

Open File Station and create a `neko` folder in the docker folder.

![image-20231227102416933](image-20231227102416933.png)

## 4. Container Manager

I am using Synology's Container Manager for this setup. Portainer is similar to QNAP:

### Upload Configuration

![image-20231227102655009](image-20231227102655009.png)

```yaml
version: "3.4"
services:
  neko:
    image: "m1k1o/neko:google-chrome"
    restart: "unless-stopped"
    shm_size: "2gb"
    ports:
      - "38080:8080"  # changeme
      - "52000-52100:52000-52100/udp"
    environment:
      NEKO_SCREEN: 1920x1080@30 # 1280x720@30
      NEKO_PASSWORD: neko  # changeme
      NEKO_PASSWORD_ADMIN: admin  # changeme
      NEKO_EPR: 52000-52100
      NEKO_FILE_TRANSFER_ENABLED: true  # changeme
      NEKO_ICELITE: 1
      NEKO_NAT1TO1: 172.16.22.22  # changeme
```

Configuration explanation (customizable):

> I have marked the parts in the above file that I think can be modified with `# changeit`. For the rest, it is not recommended for beginners to modify.

- Web server port section: You can change it to another port number, such as "`38080:8080`", `do not modify the 8080 at the end`.
- NEKO_SCREEN: Configure the resolution of Neko, `higher resolution requires better configuration`.
- NEKO_PASSWORD: Visitor login password.
- NEKO_PASSWORD_ADMIN: Administrator login password.
- NEKO_FILE_TRANSFER_ENABLED: Whether to enable file transfer.
- NEKO_NAT1TO1: Configure it to your current internal IP.

### Wait

![image-20231227103027954](image-20231227103027954.png)

### Success

![image-20231227103211897](image-20231227103211897.png)

## 5. Usage

Enter the program in the browser: [ip]:[port]

> The IP is the IP of your NAS (mine is 172.16.22.22), and the port is defined in the configuration file above. If you follow my tutorial, it is 38080.
>
> Enter any username and the password is the one configured in the compose file.

### Access

![image-20231227103250556](image-20231227103250556.png)

![image-20231227105059523](image-20231227105059523.png)

## 6. Special Features Showcase

Let's take a look at "Enter the Giant" together.

![image-20231227105655546](image-20231227105655546.png)

Mobile Display:

Portrait Mode

![image-20231227110008909](image-20231227110008909.png)

Landscape Mode:

![image-20231227110021360](image-20231227110021360.png)

Floating Screen:

![image-20231227110033869](image-20231227110033869.png)

## Finally

As for the IPTV part,

![image-20231227095210202](image-20231227095210202.png)

I don't have time to work on it, and I'm not sure if everyone is interested.

I think this "multi-user shared browser" is enough for everyone to play with for a while. If you have a need for IPTV,

give it a "like, comment, and save," and I will provide relevant tutorials later.

If you like this article, please remember to like, save, and follow "Dad's Digital Garden." We will continue to bring more practical self-built application guides. Together, let's take control of our own data and create our own digital world!

If you encounter any problems or have any suggestions during the setup process, feel free to leave a comment below for discussion and learning.