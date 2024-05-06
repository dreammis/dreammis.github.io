---
title: "创业者必备工具 更了解你的上帝 如何用Formbricks打造自定义的调查问卷系统 typeform 替代品"
date: 2024-05-06T09:33:40+08:00
categories:
- Nas教程
- 创业
draft: false
toc: true
description: 一款免费的selfhosted 调查问卷，让你更了解你的客户
featuredImage: "markovchainwhisperer_eyes_of_fire_and_volatile_plasma_she_surve_72866bc2-f2c9-4674-80f2-63b67b859426.png"
featuredImagePreview: "markovchainwhisperer_eyes_of_fire_and_volatile_plasma_she_surve_72866bc2-f2c9-4674-80f2-63b67b859426.png"

---
 一款免费的selfhosted 调查问卷，让你更了解你的客户
<!--more-->


## 1. 前言

这一篇并不适合所有人，也不一定适合nas用户，它更适合那些`正在创业`，或者`马上创业`的人。

因为我发现这个工具实在是太棒了，所以忍不住想要分享给大家。

商业一句话来说，其实很简单，就是`交易`，是`价值交换`

发现一个其他人头疼的问题、痛点，设计一个产品/服务来解决这些东西，然后找到适合这个解决方案的人，给出合理的报价

换言之赚钱就是，你`帮助别人`，别人给你一定回报

- 我们打工人，出卖了自己的体力、脑力、时间帮助公司实现更大的价值，公司衡量其价值，给你等价的钱
- 外卖员，用时间和体力帮助商家把外卖送到那个饿肚子的人，帮助了两个人，因此而得到报酬

- 短视频博主，也是帮助别人领悟了道理，跳舞的小姐姐帮助你心情愉悦，这带来了流量，也有人给其估价

再浓缩一下，创业其实很简单：

一个`合理的想法`-> 一个`合理的实现`-> 一个`合理的价格`-> `分析与改进`

如此往复，这就是一个良性的商业项目，不断了解和认识你的客户，深入他们的需求，根据它，不断的调整方向，解决方案，和价格

![img](icetray24_semi_profile_young_confident_entrepreneur_low_angle_s_9a91d63c-2e98-40b8-b8ef-1a08c0d7a2c7.png)



创业的人最头疼的问题，在于，如何能更了解你的客户，如何能找到客户真正需要的，如何带领客户到达他们想要的生活，这至关重要

而这里就有一个非常关键的工具出现：`调查问卷`

我自己有一个小项目，也苦于如何得到用户真正想要的东西，于是我开始搜寻`调查问卷`的解决方案，国内这些

![腾讯问卷](image-20240506183526730.png)

而且最简单的webhook功能都要`收费`

> webhook可以做很多事情，比如调查问卷填写完，发送优惠券到客户的手机或者邮箱等等

![image-20240506184052546](image-20240506184052546.png)



看着就不想填，我理想中的调查问卷是`typeform`这种，简洁，直观，干净

![typeform](formidable-contact-form-example.png)

![Typeform2](Typeform-Blog-SurveySchool1-1.png)



可是奈何，typeform太贵了

![type form价格](image-20240506183950929.png)



于是我开始寻找它的替代品，终于找到了一个我们nas用户最爱的，可以自搭建的**Formbricks**

![Formbricks · GitHub](203262290-3c2bc5b8-839c-468a-b675-e26a369c7fe2.png)

![Formbricks example1](image-20240506184406736.png)

![Formbricks example2](image-20240506184414486.png)

一款自由开源的调查问卷平台，以其卓越的自定义能力和隐私保护，为你提供了一个全新的选择。为什么我们需要自建Formbricks? 让我们深入了解。



## 2. 介绍Formbricks

### 作用

Formbricks提供了一个全面的调查解决方案，能够在用户体验的每一个环节收集反馈，无论是通过应用内调查、网站、链接还是电子邮件。其强大的数据分析能力可以帮助您深入了解用户需求，从而优化产品和服务。

### 特点与功能

- **多样的调查创建工具**：利用无代码编辑器，您可以轻松创建多种类型的调查问卷。
- **最佳实践模板**：提供多种行业最佳实践模板，快速启动项目。

![image-20240506184523173](image-20240506184523173.png)

- **精准的目标用户群**：无需修改应用程序代码，即可启动并定向至特定用户群。
- **分享链接调查**：创建可分享的链接调查，扩大调查的覆盖范围。
- **团队合作**：邀请团队成员共同协作，提高工作效率。
- **丰富的集成选项**（无限量）：支持与Slack、Notion、Zapier、n8n、webhook等多种平台集成。

![image-20240506184601926](image-20240506184601926.png)

- **开源与自托管**：全透明的开源代码，支持自托管，确保数据隐私和安全。

通过这些功能，Formbricks不仅仅是一个调查工具，更是一个体验管理平台，让用户的每次互动都变得更加精准和有价值。



有了它，我能更方便的收集到真实的用户需求，并且将填写问卷的用户奖励，准确的发送给用户

![image-20240506184948062](image-20240506184948062.png)



---

搭建步骤：

## 1. 重点

`点个免费关注`，不迷路

## 2. docker管理图形工具

#### 群晖 DSM 7.2版本以上可以直接使用 *Container Manager*

![container-manager-1](container-manager-1.png)

#### 威联通 ContainerStation 

![container-station-1](container-station-1.png)

![container-station-2](container-station-2.png)



#### 自行安装Portainer

教程参考：
[30秒安装Nas必备神器 Portainer](/how-to-install-portainer-in-nas/)


接下来以Portainer 为例

##  3. File Station

File Station 打开docker 文件夹，创建`formbricks`文件夹，postgres、uploads文件夹

![image-20240506185615511](image-20240506185615511.png)

- postgres 为`formbricks`的数据库文件存放目录
- uploads 为`formbricks`的附件文件存放目录

## 4. 创建stack

![portainer-slack-add](portainer-slack-add.png)

## 5.  部署代码

```yaml
version: "3.3"
x-environment: &environment
  environment:
    # The url of your Formbricks instance used in the admin panel
    WEBAPP_URL: 

    # PostgreSQL DB for Formbricks to connect to
    DATABASE_URL: "postgresql://postgres:postgres@postgres:5432/formbricks?schema=public"

    # NextJS Auth
    # @see: https://next-auth.js.org/configuration/options#nextauth_secret
    # You can use: `openssl rand -hex 32` to generate one
    NEXTAUTH_SECRET: 6ccd890b103017d5ffb36a3f4202d3d95bfd55455e12c31ccf2b5214d78bd229

    # Set this to your public-facing URL, e.g., https://example.com
    # You do not need the NEXTAUTH_URL environment variable in Vercel.
    NEXTAUTH_URL: 

    # Encryption Key is used for 2FA & Single use URLs for Link Surveys
    # You can use: $(openssl rand -hex 32) to generate one
    ENCRYPTION_KEY: 81827cff9f55e4b31879ed5d64e2af0202b7cd027b098d01a7cdcaa9b1f08dcb

    # PostgreSQL password
    POSTGRES_PASSWORD: postgres

    # Enterprise License Key
    # Required to access Enterprise-only features
    # ENTERPRISE_LICENSE_KEY:

    # Email Configuration
    # MAIL_FROM:
    # SMTP_HOST:
    # SMTP_PORT:
    # SMTP_SECURE_ENABLED:
    # SMTP_USER:
    # SMTP_PASSWORD:

    # Set the below value if you have and want to use a custom URL for the links created by the Link Shortener
    # SHORT_URL_BASE:

    # Set the below to 0 to enable Email Verification for new signups (will required Email Configuration)
    EMAIL_VERIFICATION_DISABLED: 1

    # Set the below to 0 to enable Password Reset (will required Email Configuration)
    PASSWORD_RESET_DISABLED: 1

    # Uncomment the below and set it to 1 to disable Signups
    SIGNUP_DISABLED: 0

    # Uncomment the below and set it to 1 to disable logging in with email
    # EMAIL_AUTH_DISABLED: 1

    # Uncomment the below and set it to 1 to disable Invites
    # INVITE_DISABLED:

    # Uncomment the below and set a value to have your own Privacy Page URL on the signup & login page
    # PRIVACY_URL:

    # Uncomment the below and set a value to have your own Terms Page URL on the auth and the surveys page
    # TERMS_URL:

    # Uncomment the below and set a value to have your own Imprint Page URL on the auth and the surveys page
    # IMPRINT_URL:

    # Uncomment the below and set to 1 if you want to enable GitHub OAuth
    # GITHUB_ID:
    # GITHUB_SECRET:

    # Uncomment the below and set to 1 if you want to enable Google OAuth
    # GOOGLE_CLIENT_ID:
    # GOOGLE_CLIENT_SECRET:

    # Uncomment the below to automatically assign new users to a specific team and role within that team
    # Insert an existing team id or generate a valid CUID for a new one at https://www.getuniqueid.com/cuid (e.g. cjld2cjxh0000qzrmn831i7rn)
    # (Role Management is an Enterprise feature)
    # DEFAULT_TEAM_ID:
    # DEFAULT_TEAM_ROLE: admin

    # Uncomment and set to 1 to skip onboarding for new users
    # ONBOARDING_DISABLED: 1

    # The below is used for Next Caching (uses In-Memory from Next Cache if not provided)
    # REDIS_URL:

    # The below is used for Rate Limiting (uses In-Memory LRU Cache if not provided)
    # REDIS_HTTP_URL:

services:
  postgres:
    restart: always
    image: postgres:15-alpine
    volumes:
      - /volume1/docker/formbricks/postgres:/var/lib/postgresql/data
    <<: *environment

  formbricks:
    restart: always
    image: ghcr.io/formbricks/formbricks:latest
    depends_on:
      - postgres
    ports:
      - 32000:3000
    volumes:
      - /volume1/docker/formbricks/uploads:/home/nextjs/apps/web/uploads/
    <<: *environment
```

1. 选择stack
2. name栏输入formbricks
3. edditor输入：上面代码
4. 点击deploy

### 核心参数解释

- WEBAPP_URL 如果你是本地运行不需要填写（一般也不会本地运行吧），如果外网访问，填写你的域名
- NEXTAUTH_SECRET、ENCRYPTION_KEY：加密需要。本质上这俩是应该使用指令生成的，这里简化一下，直接填写这俩值
- SIGNUP_DISABLED： 是否允许注册，这里暂时放开，因为你要注册啊，后期可以关闭。我是关闭的，我不需要其他填写问卷的人来注册😝

其他部分，按需填写

## 6. 成功

![portainer-slack-add-success](portainer-slack-add-success.png)



## 7. 使用

浏览器进入程序：[ip]:[端口]

> ip为你nas所在ip（这里我的是172.16.23.106），端口为上面配置文件定义，如果你按照我的教程，则是32000

![login](image-20240506190104510.png)

由于我这里已经注册过了，并且把SIGNUP_DISABLED已经设置成1，不允许注册，所以正常你在这里看到的是注册页面

登录进去后，介面安静清爽，这里我自己已经有一份问卷收集完成

![image-20240506190243282](image-20240506190243282.png)



可以看到问卷的情况，包括填写时间，开始率，回应率，丢弃率，方便你更好的审视自己的问卷与激励方式

![image-20240506190355501](image-20240506190355501.png)

![image-20240506190415182](image-20240506190415182.png)

## 8. 特殊功能展示

### 创建问卷

![image-20240506190503447](image-20240506190503447.png)



### webhook 设置

![image-20240506190544543](image-20240506190544543.png)

当问卷结束，发送url到该webhook，而我这里是发送承诺给用户的免费优惠券

而接收webhook的api则非常简单，使用fastapi写的一个webserver，不要以为很难，现在借助ai，你也能写出来

![image-20240506190726922](image-20240506190726922.png)



### 团队共享

搭建好后，可以让团队成员使用

![image-20240506190851037](image-20240506190851037.png)

## 最后

认识并使用Formbricks，对于我这种独立开发，自己做项目创业的人来说，真的是省了一大笔钱，而且也多了许多自由度

每一次用户反馈和评价，都至关重要，包括这里也是，你们的每一个留言我都会认真去看，我也在不断的分析、调整自己的方向，目的是希望带给大家更有用的东西，能帮助更多的人。



如果你喜欢这篇文章，请记得点赞，收藏，并关注【老爸的数字花园】，我们将会持续带来更多实用的自搭建应用指南。一起，让我们掌握自己的数据，创建自己的数字世界！

如果你在搭建过程中遇到任何问题，或者有任何建议，也欢迎在下方留言，一起探讨和学习。