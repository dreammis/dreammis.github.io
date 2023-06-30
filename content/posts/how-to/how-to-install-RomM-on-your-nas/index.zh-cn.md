---
title: "让你的游戏收藏飞起来：如何搭建你的RomM游戏图书馆？"
date: 2023-06-27T18:47:37+08:00
categories:
- Nas教程
draft: false
toc: true
---

## 1. 前言

如果你和我一样，是一个复古游戏迷，又收藏了许多古老的游戏ROM，又苦于无法很好的在自己的NAS上整理这些资料。

那么RomM也许能解决你的问题

它可以管理和组织你的所有游戏，并且通过网页浏览器来实现。与此同时，你还可以通过RomM来丰富你的游戏信息

![Alt text](https://github.com/zurdi15/romm/raw/master/.github/screenshots/gallery.png "Pic")

---

## 介绍RomM

RomM是一个专注于复古游戏的游戏库管理器，你可以通过网页浏览器来管理和组织你的所有游戏。它受到了Jellyfin的启发，允许你通过一个现代化的界面来管理你的所有游戏，同时利用IGDB的元数据来丰富你的游戏信息。

RomM的特点和功能非常强大：

- 它可以扫描你的游戏库（全部或者按平台）并利用IGDB元数据来丰富它。
- 你可以通过你的网页浏览器来访问你的游戏库。

![Alt text](https://github.com/zurdi15/romm/raw/master/.github/screenshots/home.png "Pic")

- 如果扫描的结果不准确，你还可以选择匹配的IGDB结果。

![Alt text](https://github.com/zurdi15/romm/raw/master/.github/screenshots/search.png "Pic")

- RomM兼容EmuDeck文件结构。
- RomM支持多文件游戏。
- 你可以直接从你的网页浏览器下载游戏。
- 你可以直接从你的网页浏览器编辑你的游戏文件。
- RomM支持区域，修订/版本和额外标签。
- RomM可以使用SQLite或MaridDB（默认为SQLite）
- 手机端

![Alt text](https://github.com/zurdi15/romm/raw/master/.github/screenshots/m_gallery.png "Pic")

---

搭建步骤：

## 1. 重点

`点个免费关注`，不迷路

## 2. 安装Portainer

教程参考：
[30秒安装Nas必备神器 Portainer](/how-to-install-portainer-in-nas/)

##  3. File Station

File Station 打开docker 文件夹，创建`romm`文件夹

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306262345210.png "Pic")



1. 在docker 目录下创建romm
2. 在romm目录下依次创建database（我选择的是sqlite）
3. resources（romm下载的静态资源，如封面，介绍等）
4. library(你的游戏目录)

作者给出了支持的两种`目录结构`，我这里选择的是`第一种`：

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306262345528.png "Pic")

## 4. 创建IGDB账号

1. 注册 [Twitch](https://dev.twitch.tv/login) 
2. 开启两步验证，这里可以用google 的Authenticator [enabled](https://www.twitch.tv/settings/security)

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306262345720.png "Pic")

1. 在这个页面注册Twitch的应用 [Twitch Developer Portal](https://dev.twitch.tv/console/apps/create)
2. 创建密钥
3. 复制客户端id与密钥key

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306262345436.png "Pic")





## 5. 创建stack

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306061552130.png "Pic")

## 6.  部署代码

```yaml
version: '3'
services:
  romm:
    image: zurdi15/romm:latest
    container_name: romm
    environment:
      - ROMM_DB_DRIVER=sqlite # 这里我选择的是sqlite，你可以选择mysql
      - CLIENT_ID=XXX  # 填写上一步的客户端id
      - CLIENT_SECRET=XXX  # 填写上一步的客户端密钥
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

1. 选择stack
2. name栏输入romm
3. edditor输入：上面代码
4. 点击deploy

## 7. 成功

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306061556495.png "Pic")



## 8. 使用

浏览器进入程序：[ip]:[端口]

> ip为你nas所在ip（这里我的是172.16.23.106），端口为上面配置文件定义，如果你按照我的教程，则是13280

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306262346663.png "Pic")

## 9. 放入Rom

将rom文件放入刚才设定好的目录，按照格式放入

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306262346631.png "Pic")



## 10. 开始扫描

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306262346339.png "Pic")



如果文件名规范，那么可直接扫描出封面与介绍

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306262347274.png "Pic")





如果不规范，可能需要手动扫描

选择某个rom

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306262347280.png "Pic")



搜索出之后，可以勾选Rename Rom,一并修改文件名

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306262347425.png "Pic")



## 10. 最后食用

当我哪天想要怀旧了，3ds上玩一玩了，就可以直接下载

选择多个文件，dlc，一并下载

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306262347828.png "Pic")



## 最后

Romm目前还不完善，比如只支持英文命名，匹配规则比较死板

但是未来可期，目前正在开发的功能

1. 在线上传
2. 管理存档
3. 自定义封面

我对这个项目也很感兴趣，也有意向为这个项目贡献一波力量，未来我可能会做的

- 中文支持
- rom下载（也许会使用qb， jackett）
- 模拟器介入（这部分作者和很多感兴趣的人，都在建设）



如果你喜欢这篇文章，请记得点赞，收藏，并关注【老爸的数字花园】，我们将会持续带来更多实用的自搭建应用指南。一起，让我们掌握自己的数据，创建自己的数字世界！

如果你在搭建过程中遇到任何问题，或者有任何建议，也欢迎在下方留言，一起探讨和学习。