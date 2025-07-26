---
title: leetcode 28.找出字符串中第一个匹配项的下标
subtitle:
date: 2025-07-27T02:26:32+08:00
slug: 4235705
draft: false
author:
  name: Ciao
  link:
  email:
  avatar:
description:
keywords:
license:
comment: false
weight: 0
tags:
  - leetcode
  - algorithm
categories:
  - leetcode
hiddenFromHomePage: false
hiddenFromSearch: false
hiddenFromRelated: false
hiddenFromFeed: false
summary:
resources:
  - name: featured-image
    src: featured-image.jpg
  - name: featured-image-preview
    src: featured-image-preview.jpg
toc: true
math: false
lightgallery: false
password:
message:
repost:
  enable: true
  url:

# See details front matter: https://fixit.lruihao.cn/documentation/content-management/introduction/#front-matter
---

<!--more-->

<h1 align="center">leetcode 28.找出字符串中第一个匹配项的下标</h1>

### 题目地址
  * https://leetcode.cn/problems/find-the-index-of-the-first-occurrence-in-a-string/

### 解法
  1. 双指针
  * 使用两个指针分别指向haystack和needle同时进行遍历即可，不匹配时就重新定位
    ```C++
    int strStr(string haystack, string needle) 
    {
        int index = 0; //标识haystack中的起始位置
        int j = 0; //表示needle目前遍历的位置
        for (int i = 0; i < haystack.size(); ++i)
        {
            if (haystack[i] == needle[j])
            {
                //needle遍历完了，返回结果
                if (j == needle.size() - 1)
                {
                    return index;
                }
                ++j;
                continue;
            }
            i = index++; //定位到下个起始位置
            j = 0;
            //剩余长度小于needle长度，肯定不匹配，直接返回
            if (haystack.size() - index < needle.size())
            {
                return -1;
            }
        }

        return -1;
    }
    ```
