---
title: Jekyll + Github Pages build a blog website
date: 2023-03-09 14:58:08 -0500
categories: [Personal Website, Blog]
tags: [personal website] # TAG names should always be lowercase
---

## Steps

1. Complete the installation of the basic environment [Jekyll Docs](https://jekyllrb.com/docs/installation/): download **_Ruby & RubyGems_**
1. Using one website theme [jekyll-theme-chirpy](https://github.com/cotes2020/jekyll-theme-chirpy) based on Jekyll
1. Using the [Chirpy Starter](https://github.com/cotes2020/chirpy-starter/) -> **_Use this template_** -> **_Create a new repository_** -> repo name: **_\_username.github.io_**
1. `git clone ...`
1. Install dependencies

   ```bash
   $ bundle
   ```

1. Serve it out on the local machine

   ```bash
   $ bundle exec jekyll s
   ```

1. Edit the **config.yml** file
1. Create **yyyy-mm-dd-title.md** file in \_posts folder
1. Set **_Front Matter_**

   ```
   ---
   title: 學習秘籍
   date: 2023-03-09 01:05:08 -0500
   categories: [Thoughts, How to study]
   tags: [study tips] # TAG names should always be lowercase
   ---
   ```

1. Deploy
   ```bash
   $ git push
   ```
1. Check **_Actions_** to see if build and deployment are successful

## Reference

[Chirpy Getting Started](https://chirpy.cotes.page/posts/getting-started/)

[Youtube Guider](https://www.youtube.com/watch?v=F8iOU1ci19Q&t=1141s)

{% include embed/youtube.html id='F8iOU1ci19Q' %}

## Bugs

### showing "--- layout: home # index: page ---"

1. set 'Actions -> General -> Workflow permissions' to 'Read and write permissions'
