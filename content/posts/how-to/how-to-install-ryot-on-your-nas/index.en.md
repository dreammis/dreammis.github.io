---
title: "How to Build Your Own 'Douban' on Nas: Step-by-Step Guide to Building Ryot and Creating a Brand New Digital Life Experience to Record Every Moment"
date: 2023-07-06T15:45:10+08:00
categories:
- Nas Tutorials
draft: false
toc: true
description: Technology Empowers Life - Build Ryot Yourself to Record Your Reading, Watching, Gaming, and Fitness.
---
Technology Empowers Life: Build Ryot Yourself to Record Your Reading, Watching, Gaming, and Fitness.
<!--more-->


## 1. Introduction

I can't wait to introduce my new Nas toy to you and teach you how to build your own "private Douban".

![roty](./roty.gif)

If you meet any of the following criteria:

- Electronic collection enthusiast
- Literature and art lover
- Movie and TV series enthusiast
- Gaming enthusiast
- Manga and anime lover
- Book lover

Then this toy will definitely not disappoint you.

It is a collection of "searching, scraping, movie reviews, book reviews" in one, comprehensively managing your digital life (movies, manga, TV series, books, games).

In addition, it has a great interface. As the saying goes, whether to use it or not is up to me, but "the photo wall must be there".

![image-20230706145254507](image-20230706145254507.png)

Here, I must be able to express my thoughts, write movie reviews, book reviews, and game reviews.

![image-20230706030203072](./image-20230706030203072.png)



---

## Introduction to Ryot

Ryot (Roll Your Own Tracker) helps you track various aspects of your life, including the books you read, the movies you watch, and the games you play.

Ryot has a very user-friendly interface. It provides many beautiful charts and summaries to help you better understand and summarize your life.

The main features of Ryot are as follows:

- Supports recording all your digital media (comics, books, podcasts, movies, TV series, games)
- Like Douban, it has movie reviews, ratings, progress tracking, and more importantly, my favorite games.

![image-20230706024702055](./image-20230706024702055.png)



- Deploy on Nas for private data.
- Extremely fast (Ryot is written in Rust).
- Free and open source.
- The interface is in English, but supports Chinese search (Chinese support will be available in the future).

![image-20230706151701194](image-20230706151701194.png)



---

Setup Steps:

## 1. Key Points

"Click to follow for free" so you won't get lost.

## 2. Install Portainer

Tutorial reference:
[30-Second Installation of Portainer, a Must-Have Tool for Nas](/how-to-install-portainer-in-nas/)

##  3. File Station

Open File Station and create a "Ryot" folder in the docker folder.

![image-20230706143134831](image-20230706143134831.png)

## 4. Create Stack

![1 Synology Portainer Add Stack](https://img-nasdaddy.liuxingoo.cn/img/202306061552130.png)

## 5. Deploy the Code

```yaml
version: '3.9'
services:
  ignisda:
    image: 'ghcr.io/ignisda/ryot:latest'
    volumes:
        - /volume1/docker/ryot/ryot-data:/data
    environment:
        - WEB_INSECURE_COOKIE=true
        - VIDEO_GAMES_TWITCH_CLIENT_ID=xxxx # Optional, your Twitch ID, explained in detail below
        - VIDEO_GAMES_TWITCH_CLIENT_SECRET=xxxx # Optional, your Twitch secret, explained in detail below
        - MOVIES_TMDB_LOCALE=zh
        - SHOWS_TMDB_LOCALE=zh
        # - MOVIES_TMDB_ACCESS_TOKEN=XXX
        # - SHOWS_TMDB_ACCESS_TOKEN=XXX
        - ITUNES_LOCALE=en
        - USERS_ALLOW_REGISTRATION=true
    ports:
        - '18030:8000'
    pull_policy: always
    container_name: ryot
    restart: unless-stopped
```

1. Select stack.
2. Enter "Ryot" in the name field.
3. Enter the above code in the editor.
4. Click on deploy.

### Parameter Explanation

- WEB_INSECURE_COOKIE

Set this to true if you are not using `https`.

- VIDEO_GAMES_TWITCH_CLIENT_ID   VIDEO_GAMES_TWITCH_CLIENT_SECRET

These two parameters are optional. If not set, the "Games" section will not be available. You can refer to this article for setting up these parameters: [30-second installation of Portainer](/how-to-install-romm-on-your-nas/)

- MOVIES_TMDB_LOCALE SHOWS_TMDB_LOCALE 

These two parameters are for selecting the Chinese option in TMDB.

- MOVIES_TMDB_ACCESS_TOKEN  SHOWS_TMDB_ACCESS_TOKEN

These parameters are used for setting up the TMDB token. If left empty, it will not affect the scraping process. However, it is recommended to fill in your own token or fill it in later if it becomes invalid.

- USERS_ALLOW_REGISTRATION

Set this to true for the first time to allow user registration. If you are not using multiple users, you can set it to false later.

## 6. Success

![Excalidraw Synology NAS Set up 3](https://img-nasdaddy.liuxingoo.cn/img/202306061556495.png)

## 7. Usage

Access the program in your browser: [ip]:[port]

> Replace "ip" with the IP address of your NAS (e.g., 172.16.23.106) and "port" with the port defined in the configuration file (e.g., 18030 if you followed the tutorial).

![image-20230706143816983](image-20230706143816983.png)

## 8. Registration

Click on "register" to create an account.

![image-20230706144041905](image-20230706144041905.png)

## 9. Detailed Usage

Next, I will demonstrate the functionality of each module.

### Search Books (Using Google Books)

Search for the best-selling book "长安的荔枝" from last year.

![image-20230706022436912](./image-20230706022436912.png)

Great, all the information is available.

Now, search for "始于极限" by 上野千鹤子 from last year. Unfortunately, there is no cover image.

![image-20230706022205810](./image-20230706022205810.png)

Fortunately, the content is still available. Just paste the cover image manually.

![image-20230706022337739](./image-20230706022337739.png)

### Comics

There are two types of comics: "animes" and "mangas". Let me explain the difference between the two.

`Difference between "animes" and "mangas"`

【Animes - Japanese Animation】

Format: Dynamic visual product, played through TV, movies, etc.

Production: Involves animators, voice actors, etc., with long production cycles and high budgets.

Features: Strong visual effects and sound effects, with strong plot and character development.

Representative works: "Slam Dunk", "Ghost in the Shell", "Death Note", etc.

【Mangas - Japanese Comics】

Format: Static printed material, distributed through books, magazines, etc.

Creation: Mainly completed by one or a few manga artists, with a short production cycle and low cost.

Characteristics: Static images, not as visually and audibly immersive as animes, slightly inferior in plot and character portrayal.

Representative works: "Dragon Ball", "Detective Conan", "One Piece", "Naruto", etc.

### Manga Functionality (Animes)

Search in Chinese: Death Note

![image-20230706022809791](./image-20230706022809791.png)

Not bad, let's check the details page

![image-20230706022855457](./image-20230706022855457.png)

Although it's in English, it fits our photo wall

Here, let's focus on `action`, which is also a major feature of ryot, `track all your media`, track all your progress

![image-20230706022955344](./image-20230706022955344.png)

1. I'm currently watching
2. Add to watched list
3. Write a review
4. Add to collection
5. Update the latest meta information

This way, you can clearly know which ones you haven't finished watching and which ones you have already watched

![image-20230706023304577](./image-20230706023304577.png)

Here you can `write a review`, which is also the biggest reason why I can't give up Douban. There is no good tool to mark and write down the review at that time.

![image-20230706023447810](./image-20230706023447810.png)

Support `multiple reviews`, such as for a specific episode

![image-20230706023544225](./image-20230706023544225.png)

### Movies

Next is the movie section, let's start with a classic: "Gone Girl"

![image-20230706023716999](./image-20230706023716999.png)

tmdb resources are indeed abundant

Now let's take a look at a recent movie similar to it, "Her"

![image-20230706023753489](./image-20230706023753489.png)

For "Her", there are more than ten posters, scraping a large number of posters at once, enough for you to show off

![image-20230706023820249](./image-20230706023820249.png)

![image-20230706023841885](./image-20230706023841885.png)

Same for reviews, standard operation:

![image-20230706023920552](./image-20230706023920552.png)

### Podcasts

Search in English

![image-20230706023945856](./image-20230706023945856.png)

Search for Chinese channels

![image-20230706024001736](./image-20230706024001736.png)

### TV Shows

Search in Chinese

![image-20230706024106001](./image-20230706024106001.png)

![image-20230706024151656](./image-20230706024151656.png)

`All the episodes are scraped`, there are also introductions, and you can also `track the progress of each episode`, each episode has a watched or unwatched status

![image-20230706024322318](./image-20230706024322318.png)

Let's try a less popular one:

![image-20230706024528073](./image-20230706024528073.png)

Try an English one, no problem:

![image-20230706024350559](./image-20230706024350559.png)

![image-20230706024448119](./image-20230706024448119.png)

### Games (My favorite)

That's right, `ryot can also track your game progress`!

Last year's "Elden Ring"

![image-20230706024625522](./image-20230706024625522.png)

My favorite "Arthur Morgan":

![image-20230706024646254](./image-20230706024646254.png)

`Only one game in the US`:

![image-20230706024702055](./image-20230706024702055.png)

On the list page, you can easily `sort` by whether you have played it, release date, and rating:

![image-20230706024750215](./image-20230706024750215.png)

Finally, the homepage:

![image-20230706024923233](./image-20230706024923233.png)

## Finally

There are still some issues with the homepage.

1. The content in the summary section has not been updated. I suspect that I may be using SQLite as the database or there may be a bug.
2. The concept of "collection" is not reflected here. The author has designed a concept called "collection", where you can create your own collection according to your preferences. For example, if you are interested in entrepreneurship, you can gather all the books, TV shows, and movies related to entrepreneurship in this collection.

What can be expected in the future:

1. This project is working hard to integrate with other projects (currently integrated with audiobookshelf, but I have not been able to deploy it successfully), I don't know the reason.

![image-20230706025158329](./image-20230706025158329.png)

2. There are also other projects like Plex, Emby, etc. I believe that in due course, they will catch up with the schedule.
3. If I have time, I will also contribute to the open-source community to improve this project.

For now, although the functionality is not perfect, I think it is sufficient. I will continue to pay attention to this project in the future, and if there are any new features and characteristics, I will synchronize with everyone in a timely manner.

---

Finally, let me introduce my devices: "1 white dress, 1 QNAP, 1 Snail (black dress), 1 PVE server". I do not recommend beginners to tinker with these devices like I do. It is more recommended for novice players to choose a white dress or QNAP.

If you like this article, please remember to like, bookmark, and follow "Dad's Digital Garden". We will continue to bring more practical self-built application guides. Together, let's take control of our own data and create our own digital world!

If you encounter any problems during the setup process or have any suggestions, please feel free to leave a comment below for discussion and learning.