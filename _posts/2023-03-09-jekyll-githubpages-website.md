---
title: Jekyll + Github Pages build a blog website
date: 2023-03-09 01:05:08 -0500
categories: [Personal Website, Blog]
tags: [personal website] # TAG names should always be lowercase
---

## Steps

1. Complete the installation of the basic environment [Jekyll Docs](https://jekyllrb.com/docs/installation/): download **_Ruby & RubyGems_**
2. Using one website theme [jekyll-theme-chirpy](https://github.com/cotes2020/jekyll-theme-chirpy) based on Jekyll
3. Using the [Chirpy Starter](https://github.com/cotes2020/chirpy-starter/) -> **_Use this template_** -> **_Create a new repository_** -> repo name: **_\_username.github.io_**
4. git clone ...
5. Edit the config.yml file
6. Create yyyy-mm-dd-title.md file in \_posts folder
7. Set **_Front Matter_**

```
---
title: 學習秘籍
date: 2023-03-09 01:05:08 -0500
categories: [Thoughts, How to study]
tags: [study tips] # TAG names should always be lowercase
---
```

7. git push
8. Check **_Actions_** to see if build and deployment are successful

[More references](https://chirpy.cotes.page/posts/getting-started/)

## Bugs

### showing "layout: home # index: page" ->

1. set 'Actions -> General -> Workflow permissions' to 'Read and write permissions'
2. re-edit the index.html and push.
