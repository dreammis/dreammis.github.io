---
title: "A New Tool for NAS Users: Create Personalized Resumes with Reactive-Resume to Boost Your Career Competitiveness"
date: 2023-06-27T18:37:01+08:00
categories:
- NAS Tutorials
draft: false
toc: true
---

## 1. Introduction

A resume plays a crucial role in job hunting, applying for schools, or showcasing personal abilities.

Many working individuals may have experienced the frustration of working hard on a resume, only to be rejected by HR due to formatting or template issues.

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306141253235.gif "Pic")

So, how can you create a professional and appealing resume?

In today's tutorial, I will help you build a service that allows you to easily create, update, and share your resume: Reactive-Resume.

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306141252179.png "Pic")

Why do we need to build our own resume generator? There are two main reasons:

- It can meet your personalized resume needs, allowing you to freely adjust layouts, choose colors and templates, and even create resumes with dark mode.

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306141254504.png "Pic")

- No ads, no user tracking, ensuring the integrity and privacy of your data to the greatest extent.

## 2. Reactive-Resume: Your Personalized Resume Generator

Reactive-Resume is an open-source online resume generator with the following main features:

- **Free**: Reactive-Resume is always free, with no ads or user tracking.
- **Real-time Sync**: You can sync your data across different devices without worrying about data loss.
- **Data Import**: You can import data from LinkedIn or JSON resumes, greatly simplifying the resume creation process.
- **Resume Management**: With just one account, you can manage multiple resumes.
- **Share Resumes**: You can share your resume with others through a unique link or export it as a PDF.
- **Customize Resumes**: You can choose any font from Google Fonts and select various templates and colors, including dark mode.

Reactive-Resume is a powerful and user-friendly tool that makes resume creation, updating, and sharing simple and easy.

---

Now let's move on to the steps to build it:

## 1. Key Point

`Follow for free` to avoid getting lost.

## 2. Install Portainer

Tutorial reference:
[30-Second Installation of Portainer, a Must-Have Tool for NAS](/how-to-install-portainer-in-nas/)

## 3. File Station

Open File Station and create a `resume_data` folder in the Docker folder.

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306141256268.png "Pic")

## 4. Create Stack

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306061552130.png "Pic")

## 5. Deployment

```yaml
version: "3.8"

services:
  postgres:
    image: postgres:alpine
    container_name: resume_db
    restart: always
    volumes:
      - /volume1/docker/resume_data:/var/lib/postgresql/data  # Save resumes and important service data
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U postgres"]
      start_period: 15s
      interval: 30s
      timeout: 30s
      retries: 3
    environment:
      - POSTGRES_DB=postgres
      - POSTGRES_USER=postgres
      - POSTGRES_PASSWORD=postgres
```

```markdown
  server:
    image: amruthpillai/reactive-resume:server-latest
    container_name: resume_server
    restart: always
    ports:
      - 3100:3100
    depends_on:
      - postgres
    environment:
      - PUBLIC_URL=http://172.16.23.106:13000  # Replace with your IP, or domain if publicly mapped
      - PUBLIC_SERVER_URL=http://172.16.23.106:3100  # Replace with your IP, or domain if publicly mapped
      - POSTGRES_DB=postgres
      - POSTGRES_USER=postgres
      - POSTGRES_PASSWORD=postgres
      - SECRET_KEY=change-me-to-something-secure
      - POSTGRES_HOST=postgres
      - POSTGRES_PORT=5432
      - JWT_SECRET=change-me-to-something-secure
      - JWT_EXPIRY_TIME=604800
      
  client:
    image: amruthpillai/reactive-resume:client-latest
    container_name: resume_client
    restart: always
    ports:
      - 13000:3000
    depends_on:
      - server
    environment:
      - PUBLIC_URL=http://172.16.23.106:13000  # Replace with your IP, or domain if publicly mapped
      - PUBLIC_SERVER_URL=http://172.16.23.106:3100  # Replace with your IP, or domain if publicly mapped
```

1. Select stack
2. Enter "reactive-resume" in the name field
3. Enter the above code in the editor
4. Click deploy

> Note: Replace PUBLIC_URL and PUBLIC_SERVER_URL with your internal IP address, such as 192.168.1.32:13000, or domain name (public)

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306141300579.png "Pic")

## 6. Success

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306061556495.png "Pic")

## 7. Usage

Open the program in your browser: [ip]:[port]

> Replace ip with the IP address of your NAS (in this case, mine is 172.16.23.106), and port with the one defined in the configuration file (if you followed my tutorial, it would be 13000)

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306141307218.png "Pic")

## 8. Register

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306141302503.png "Pic")

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306141302865.png "Pic")

## 9. Create Resume

Two ways:

1. Import from JSON
2. Create new

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306141308151.png "Pic")

## 10. Edit Resume

### Edit freely, change module names:

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306141311943.png "Pic")

### Export and Share

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306141310799.png "Pic")

### Change layout and DIY

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306141311553.png "Pic")

### Multiple templates to choose from

![Alt text](https://img-nasdaddy.liuxingoo.cn/img/202306141313755.png "Pic")

## Finally

Reactive-Resume will be your helpful assistant, helping you stand out among many applicants.

You can share it with your family, even your wife. I believe this time, your wife will agree to let you buy that NAS you've been longing for 😂

If you like this article, please remember to like, bookmark, and follow "Dad's Digital Garden". We will continue to bring you more practical self-hosted application guides. Together, let's take control of our own data and create our own digital world!

If you encounter any problems during the setup process or have any suggestions, feel free to leave a comment below for discussion and learning.