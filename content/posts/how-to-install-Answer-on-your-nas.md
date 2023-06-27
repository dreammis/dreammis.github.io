---
title: "升级你的NAS：使用Answer搭建知识共享平台，为客户提供最佳体验"
date: 2023-06-27T18:38:52+08:00
categories:
- Nas教程
draft: false
toc: true
---

## 1. 前言

你想不想拥有一个地方，可以记录自己的问题

你想不想拥有一个类似知乎（问答）的地方，和你的朋友或者客户使用

也许你需要一个平台来交流，记录并解决这些问题，帮助他们更好地和朋友交流，帮助客户理解你的产品或服务。



今天我们在你的NAS上自行搭建一个类知乎平台--Answer

![Alt text](https://noted.lol/content/images/2023/01/answer-self-hosted-screenshots.png "Pic")



---

## 介绍Answer

Answer是一个开源的知识型社区软件。通过它，你可以快速搭建起你的Q&A社区，不仅仅用于产品的技术支持，也可以用于客户支持，用户交流等。如果你正在寻找一个简单的与客户、用户互动的方式，Answer可能就是你正在寻找的工具。

**功能特点：**

1. **开源**：这意味着你可以免费使用Answer，并且有大量的开发者和社区为其提供支持。你可以根据你的需求对其进行定制。
2. **知识型社区**：不同于一般的论坛，Answer是为了解答问题而生的。它可以帮助你快速找到你需要的答案，提高效率。
3. **产品技术支持**：如果你的产品有技术问题，你可以通过Answer来提供解答。这可以使你的客户更好地理解和使用你的产品。
4. **客户支持**：你可以通过Answer来收集和解答客户的问题。这不仅可以帮助你了解你的客户，而且还可以提高客户满意度。
5. **用户交流**：Answer也可以作为你的用户交流的平台。你的用户可以在这里互相帮助，分享经验，提出建议
6. **碎碎念** 当然你可以完全把他当作一个碎碎念的地方(我就是这样用的)
7. **markdown** 支持

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306161511879.png "Pic")



---

接下来是正餐搭建步骤：

## 1. 重点

`点个免费关注`，不迷路

## 2. 安装Portainer

教程参考：
[30秒安装Nas必备神器 Portainer](/posts/install-portainer-in-nas/)

##  3. File Station

File Station 打开docker 文件夹，创建`answer`文件夹

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306161511165.png "Pic")

## 4. 创建stack

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306061552130.png "Pic")

## 5.  部署代码

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

1. 选择stack
2. name栏输入answer
3. edditor输入：上面代码
4. 点击deploy

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306161511349.png "Pic")

## 6. 成功

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306061556495.png "Pic")



## 7. 使用

浏览器进入程序：[ip]:[端口]

> ip为你nas所在ip（这里我的是172.16.23.106），端口为上面配置文件定义，如果你按照我的教程，则是9080

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306161512990.png "Pic")

## 8. 配置

### 配置数据库

使用sqlite即可，如果公司使用，建议mysql，pg这样的

![Alt text](https://noted.lol/content/images/2023/01/answer-self-hosted-database.png "Pic")



下一步

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306161513642.png "Pic")

基本配置

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306161515259.png "Pic")



## 9. 使用

新建问题（支持markdown）：

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306161516244.png "Pic")

- 列表页：

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306161516186.png "Pic")



- 详情页

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306161516294.png "Pic")



### 设置主题

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306161518887.png "Pic")



### 后台管理

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306161518719.png "Pic")



## 最后

如果你喜欢这篇文章，请记得点赞，收藏，并关注【老爸的数字花园】，我们将会持续带来更多实用的自搭建应用指南。一起，让我们掌握自己的数据，创建自己的数字世界！

如果你在搭建过程中遇到任何问题，或者有任何建议，也欢迎在下方留言，一起探讨和学习。