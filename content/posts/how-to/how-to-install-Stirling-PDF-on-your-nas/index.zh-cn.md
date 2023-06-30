---
title: "NAS爱好者福音，最强PDF处理工具，让你的NAS更有价值！"
date: 2023-06-27T18:30:40+08:00
categories:
- Nas教程
draft: false
toc: true
---

## 1. 前言

大家都有过这样的经历，面对一堆PDF文档，或者需要合并几个PDF，或者需要将一份PDF文件拆分，又或者需要调整PDF中的页面顺序，找到的线上工具`要么广告满天飞`，要么`需要付费使用`，再不然就是`担心隐私泄露`的问题。如果你也对此感到困扰，那么自建的PDF处理工具`Stirling-PDF`或许是你需要的解决方案。

---

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306121301570.png "Pic")

## 介绍Stirling-PDF

Stirling-PDF 是一个强大的本地托管的基于Web的PDF操作工具，通过Docker运行，允许您对PDF文件执行各种操作，如分割、合并、转换、重组、添加图片、旋转、压缩等等。可以处理你所有的PDF需求。

所有的文件和PDF只存在于客户端，任何已被用户下载的文件在那个时候已经从服务器上删除

>  不需要担心这个服务越来越大，它是你`最省心最不占地方的PDF助手

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306121302070.gif "Pic")



#### 主要特性：

- 完整的web-GUI，用于合并/分割/旋转/移动PDF及其页面。

- 将PDF分割为多个文件
- 将多个PDF合并为一个
- 将PDF转换为图片，以及将图片转换为PDF
- 修复PDFs
- 检测并删除空白页
- 比较2个PDF并显示文本差异
- 向PDF中添加图片
- 以90度为单位旋转PDF。
- 压缩PDF以减少它们的文件大小
- 添加和移除密码
- 添加水印
- 将任何常见文件转换为PDF
- 将PDF转换为Word/Powerpoint/其他格式
- 从PDF中提取图片
- 对PDF进行OCR

---

好了，废话不多说，接下来是具体搭建步骤：

## 1. 重点

`点个免费关注`，不迷路

## 2. 安装Portainer

教程参考：
[30秒安装Nas必备神器 Portainer](/how-to-install-portainer-in-nas/)

##  3. File Station

File Station 打开docker 文件夹，创建`stirling-pdf`文件夹

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306121329615.png "Pic")

## 4. 创建stack

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306061552130.png "Pic")

## 5.  部署代码

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
     APP_HOME_NAME: NasDaddy PDF # web界面主标题
     APP_HOME_DESCRIPTION: 老爸的PDF百宝箱 # 网站描述
     APP_NAVBAR_NAME: NasDaddy PDF # 导航页标题
     APP_ROOT_PATH: /
```

1. 选择stack
2. name栏输入stirling-pdf
3. edditor输入：上面代码
4. 点击deploy

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306121254282.png "Pic")

## 6. 成功

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306061556495.png "Pic")



## 7. 使用

浏览器进入程序：[ip]:[端口]

> ip为你nas所在ip（这里我的是172.16.23.106），端口为上面配置文件定义，如果你按照我的教程，则是13260

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306121255093.png "Pic")

## 8. OCR中文支持

Stiring-PDF有非常强大的OCR功能

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306121320624.gif "Pic")



将pdf中的图像运用ocr，将文本提取，就像

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306121321938.png "Pic")





OCR，默认是英语字库，我们想要支持中文，就需要自行下载中文的训练包：

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306121322707.png "Pic")



1. 下载地址：

stirling-pdf-traindata：[提取码：xztp](https://pan.baidu.com/s/1_LguqxLBqWxn5fHJq_IWwQ)

2. 这里有两个训练包：

3. normal（更大，更全，识别速度慢）
4. fast（更小，更精简，识别速度快）

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306121340441.png "Pic")

3. 将训练文件放入

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306121331819.png "Pic")







## 最后

通过搭建自己的Stirling-PDF，你不仅可以随时随地处理PDF，而且可以确保你的数据始终在自己的掌控之中，不会被不必要的第三方所获取。

如果你喜欢这篇文章，请记得点赞，收藏，并关注【老爸的数字花园】，我们将会持续带来更多实用的自搭建应用指南。一起，让我们掌握自己的数据，创建自己的数字世界！

如果你在搭建过程中遇到任何问题，或者有任何建议，也欢迎在下方留言，一起探讨和学习。