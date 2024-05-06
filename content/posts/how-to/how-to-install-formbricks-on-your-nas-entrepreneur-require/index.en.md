---
title: "Essential Tools for Entrepreneurs: Understanding Your Customers Better with Formbricks - A Typeform Alternative"
date: May 6, 2024
categories:
- NAS Tutorials
- Entrepreneurship
draft: false
toc: true
description: A free, self-hosted survey questionnaire to get to know your customers better
featuredImage: "markovchainwhisperer_eyes_of_fire_and_volatile_plasma_she_surve_72866bc2-f2c9-4674-80f2-63b67b859426.png"
featuredImagePreview: "markovchainwhisperer_eyes_of_fire_and_volatile_plasma_she_surve_72866bc2-f2c9-4674-80f2-63b67b859426.png"

---
Discover a free, self-hosted survey questionnaire tool to better understand your customers.
<!--more-->


## 1. Introduction

This article might not be for everyone, especially not all NAS users, but it's particularly useful for those who are in the process of starting or about to start a business.

I stumbled upon this tool and couldn't resist sharing it because of its impressive capabilities.

Business, in a nutshell, is about transactions and value exchange. Identifying a problem or pain point, designing a product/service to address it, finding the right audience, and pricing it appropriately.

In other words, making money is about helping others in exchange for compensation.

- Employees help companies achieve greater value through their physical labor, intellect, and time, and are compensated accordingly.
- Delivery personnel use their time and effort to deliver food, assisting both the restaurant and the customer, and receive payment for their service.
- Short video bloggers provide insights or entertainment, attracting traffic, and thus, valuation.

To condense it further, entrepreneurship is simple:

A viable idea -> A feasible implementation -> A reasonable price -> Analysis and improvement

Repeat this cycle for a healthy business project, continuously understanding and catering to your customers' needs, adjusting your direction, solutions, and pricing accordingly.

![img](icetray24_semi_profile_young_confident_entrepreneur_low_angle_s_9a91d63c-2e98-40b8-b8ef-1a08c0d7a2c7.png)

The biggest headache for entrepreneurs is understanding their customers: finding out what they truly need and guiding them to the lifestyle they desire. This is where a crucial tool comes into play: `survey questionnaires`.

I had a small project and struggled to capture what users really wanted, which led me to explore `survey questionnaire` solutions. Domestic options were available, but even basic webhook functionality was `charged`.

> Webhooks can perform numerous tasks, such as sending a coupon to a customer's phone or email after they complete a survey.

![image-20240506184052546](image-20240506184052546.png)

Filling these out felt tedious. I envisioned a survey tool like `typeform`: simple, intuitive, and clean.

![typeform](formidable-contact-form-example.png)

![Typeform2](Typeform-Blog-SurveySchool1-1.png)

However, typeform was too expensive.

![type form pricing](image-20240506183950929.png)

So, I sought alternatives and finally discovered **Formbricks**, a self-hostable favorite among NAS users.

![Formbricks · GitHub](203262290-3c2bc5b8-839c-468a-b675-e26a369c7fe2.png)

![Formbricks example1](image-20240506184406736.png)

![Formbricks example2](image-20240506184414486.png)

Formbricks is a free, open-source survey platform known for its excellent customization capabilities and privacy protection, offering a fresh alternative. Let's delve deeper into why we should self-host Formbricks.


## 2. Introducing Formbricks

### Purpose

Formbricks offers a comprehensive survey solution, collecting feedback at every user interaction point, whether through in-app surveys, websites, links, or emails. Its powerful data analysis capabilities help you understand user needs, optimizing products and services.

### Features and Functions

- **Diverse survey creation tools**: Easily create various types of surveys with a no-code editor.
- **Best practice templates**: Access industry best practice templates for quick project starts.

![image-20240506184523173](image-20240506184523173.png)

- **Precise targeting**: Launch and target specific user groups without modifying app code.
- **Shareable link surveys**: Create shareable link surveys to expand coverage.
- **Team collaboration**: Invite team members to collaborate and improve efficiency.
- **Rich integration options** (unlimited): Supports integration with Slack, Notion, Zapier, n8n, webhook, and more.

![image-20240506184601926](image-20240506184601926.png)

- **Open-source and self-hosted**: Fully transparent open-source code, supporting self-hosting to ensure data privacy and security.

With these features, Formbricks is more than just a survey tool; it's an experience management platform, making every user interaction more precise and valuable.

Having this tool allows me to easily collect genuine user needs and accurately reward survey participants.

![image-20240506184948062](image-20240506184948062.png)

---

Setup Steps:

## 1. Key Points

`Click to follow for free`, and you won't get lost.

## 2. Docker Management Graphic Tool

#### For Synology DSM 7.2 and above, use *Container Manager* directly.

![container-manager-1](container-manager-1.png)

#### For QNAP, use ContainerStation.

![container-station-1](container-station-1.png)

![container-station-2](container-station-2.png)

#### Or install Portainer yourself.

Tutorial reference:
[Install the Essential NAS Tool Portainer in 30 Seconds](/how-to-install-portainer-in-nas/)

Next, we'll use Portainer as an example.

##  3. File Station

Open the docker folder in File Station and create `formbricks`, `postgres`, and `uploads` folders.

![image-20240506185615511](image-20240506185615511.png)

- `postgres` is for storing database files for `formbricks`.
- `uploads` is for storing attachment files for `formbricks`.

## 4. Create a Stack

![portainer-slack-add](portainer-slack-add.png)

## 5. Deploy Code

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

1. Select stack.
2. Enter `formbricks` in the name field.
3. Input the above code in the editor.
4. Click deploy.

### Key Parameter Explanation

- WEBAPP_URL: If you're running locally, you don't need to fill this in. For external access, enter your domain name.
- NEXTAUTH_SECRET, ENCRYPTION_KEY: Needed for encryption. Ideally, these should be generated via command, but for simplicity, use the provided values.
- SIGNUP_DISABLED: Whether to allow registration. Initially set to allow, as you need to register. Can be disabled later.

For other parts, fill in as needed.

## 6. Success

![portainer-slack-add-success](portainer-slack-add-success.png)

## 7. Usage

Access the program in a browser: [IP]:[Port]

> The IP is your NAS's IP (mine is 172.16.23.106), and the port is defined in the configuration file, 32000 if you followed this guide.

![login](image-20240506190104510.png)

Since I've already registered and set SIGNUP_DISABLED to 1, disallowing registration, you would normally see a registration page here.

After logging in, the interface is calm and clean. I've already completed a survey collection here.

![image-20240506190243282](image-20240506190243282.png)

You can see the survey details, including completion time, start rate, response rate, and drop rate, helping you better evaluate your survey and incentives.

![image-20240506190355501](image-20240506190355501.png)

![image-20240506190415182](image-20240506190415182.png)

## 8. Special Features Showcase

### Creating a Survey

![image-20240506190503447](image-20240506190503447.png)

### Webhook Settings

![image-20240506190544543](image-20240506190544543.png)

When a survey ends, the URL is sent to this webhook. Here, I'm sending a promised free coupon to users.

The API receiving the webhook is a simple web server written with FastAPI. Don't think it's difficult; with AI's help, you can write it too.

![image-20240506190726922](image-20240506190726922.png)

### Team Sharing

After setup, team members can use it.

![image-20240506190851037](image-20240506190851037.png)

## Conclusion

Getting to know and using Formbricks has saved me a significant amount of money as an independent developer and entrepreneur. It also provided much more flexibility.

Every piece of user feedback and evaluation is crucial, including here. I carefully consider every comment, constantly analyzing and adjusting my direction to bring more useful content and help more people.

If you liked this article, remember to like, save, and follow "Dad's Digital Garden" for more practical self-hosting application guides. Together, let's take control of our data and create our digital world!

If you encounter any issues during setup or have suggestions, feel free to comment below. Let's discuss and learn together.