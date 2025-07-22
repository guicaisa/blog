---
title: leetcode 58.最后一个单词的长度
subtitle:
date: 2025-07-22T12:04:39+08:00
slug: a8b0733
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

<h1 align="center">leetcode 58.最后一个单词的长度</h1>

### 题目地址
  * https://leetcode.cn/problems/length-of-last-word/

### 解法
  1. 遍历
  * 非空格字符时，累加字符串长度，遇到空格时记录长度即可
    ```C++
    int lengthOfLastWord(string s) 
    {
        int len = 0;
        int temp = 0;
        for (int i = 0; i < s.size(); ++i)
        {
            if (s[i] == ' ')
            {
                if (temp != 0)
                {
                    len = temp;
                }
                temp = 0;
            }
            else
            {
                ++temp;
            }
        }

        if (temp != 0)
        {
            len = temp;
        }

        return len;
    }
    ```