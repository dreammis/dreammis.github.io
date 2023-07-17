---
title: "Upgrade Your NAS: Set up a Knowledge Sharing Platform with Answer for an Optimal Customer Experience"
date: 2023-06-27T18:38:52+08:00
categories:
- NAS Tutorials
draft: false
toc: true
---
## 1. Introduction

Have you ever wished for a place where you can document your queries?

Or a platform similar to Zhihu (Q&A site) to engage with your friends or clients?

Perhaps you need a platform for discussion, documenting and resolving questions, enhancing communication with friends, and helping customers understand your products or services.

Today, we will create a Zhihu-like platform -- Answer -- on your NAS.

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306301653674.png "Pic")

---

## Introducing Answer

Answer is an open-source knowledge-based community software. With it, you can swiftly build your Q&A community for not only technical support for your product but also customer support and user interaction. If you are looking for a simple way to interact with customers and users, Answer might be the tool you're seeking.

**Key Features:**

1. **Open source**: This means you can use Answer for free, and there's a large community of developers providing support. You can customize it based on your needs.
2. **Knowledge-based community**: Unlike general forums, Answer is born to answer questions. It can help you find the answers you need quickly, enhancing efficiency.
3. **Product technical support**: If your product has technical issues, you can use Answer to provide solutions. This can help your customers understand and use your product better.
4. **Customer support**: You can collect and answer customer questions via Answer. It not only helps you understand your customers better but also improves customer satisfaction.
5. **User interaction**: Answer can also be a platform for user interaction. Your users can help each other, share experiences, and propose suggestions here.
6. **Random Thoughts**: Of course, you can completely treat it as a place for random thoughts (which is how I use it).
7. **Markdown Support**.

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306161511879.png "Pic")

---

Next, we'll walk through the setup steps:

## 1. Key Point

`Hit the free follow button`, don't get lost

## 2. Install Portainer

Tutorial reference: 
[Install the must-have NAS tool Portainer in 30 seconds](/posts/how-to-install-portainer-in-nas/)

##  3. File Station

Open the docker folder in File Station and create the `answer` folder

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306161511165.png "Pic")

## 4. Create a stack

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306061552130.png "Pic")

## 5. Deploy the code

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

1. Choose stack
2. Enter 'answer' in the name field
3. Enter the above code in the editor
4. Click deploy

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306161511349.png "Pic")

## 6. Success

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306061556495.png "Pic")

## 7. Usage

Enter the program in the browser: [ip]:[port]

> The IP is the one of your NAS (mine is 172.16.23.106 here), and the port is defined in the configuration file above. If you follow my tutorial, it's 9080.

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306161512990.png "Pic")

## 8. Configuration

### Configure the database

You can use sqlite. If for company use, it's recommended to use MySQL, pg, etc.

![Alt text](https://img-nasdaddy.liuxingoo.cn/202306301702433.png "Pic")

Next step

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306161513642.png "Pic")

Basic configuration

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306161515259.png "Pic")

## 9. Usage

Create a new question (supports markdown):

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306161516244.png "Pic")

- List page:

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306161516186.png "Pic")

- Detail page

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306161516294.png "Pic")

### Set Theme

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306161518887.png "Pic")

### Backend Management

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306161518719.png "Pic")

## Finally

If you enjoyed this article, please remember to like, bookmark it, and follow "NasDaddy". We will continue to bring more practical guides for setting up your own applications. Together, let's take control of our data and create our digital world!

If you encounter any problems during the setup process or have any suggestions, feel free to leave a comment below. Let's discuss and learn together.
