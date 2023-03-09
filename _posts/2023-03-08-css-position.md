---
title: Difference between absolute, relative, static, fixed and static
date: 2023-03-08 23:53:10 -5
categories: [CSS, Position]
tags: [css-position] # TAG names should always be lowercase
---

# [CSS] - Difference between absolute, relative, static, fixed and static

## Static

默認值，忽略 top, right, bottom, left

## Relative

脫離文檔流，但存在于文檔流中（占據空間）， 相對於自身的偏移
![img-description](https://img-blog.csdnimg.cn/20190825171118713.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2NqbTEzMjQ5NDI1Mjgw,size_16,color_FFFFFF,t_70)_box-item2: relative_

## Abolute

脫離文檔流，不存在于文檔流中（不占據空間），相對於有 position（relative, absolute, fixed...）的父元素的偏移
![img-description](https://img-blog.csdn.net/20160304231017219)_son-one: absolute, son-two: static_

## Fixed

相對於瀏覽器窗口（視口），絕對定位

## Sticky

相當於 relative + fixed, 被視爲相對定位， 直到超過指定的閾值，此時視爲 fixed

參考：

- https://blog.csdn.net/Low_Key_Shulman/article/details/50806161?spm=1001.2101.3001.6661.1&utm_medium=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-50806161-blog-100064904.pc_relevant_multi_platform_whitelistv3&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-50806161-blog-100064904.pc_relevant_multi_platform_whitelistv3&utm_relevant_index=1

- https://blog.csdn.net/cjm13249425280/article/details/100064904
