---
title: leetcode 392.判断子序列
subtitle:
date: 2025-08-13T20:41:19+08:00
slug: e3a551c
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

<h1 align="center">leetcode 392.判断子序列</h1>

### 题目地址
  * https://leetcode.cn/problems/is-subsequence/

### 解法
  1. 双指针
  * 很简单，两个指针逐一判断即可
    ```C++
    bool isSubsequence(string s, string t) 
    {
        if (s.size() == 0)
        {
            return true;
        }

        int index = 0;
        for (int i = 0; i < t.size(); ++i)
        {
            if (t[i] == s[index])
            {
                if (++index >= s.size())
                {
                    return true;
                }
            }
        }

        return false;
    }
    ```

