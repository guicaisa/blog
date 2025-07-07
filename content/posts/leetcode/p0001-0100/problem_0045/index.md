---
title: leetcode 45.跳跃游戏 II
subtitle:
date: 2025-07-07T16:50:20+08:00
slug: 9fc75a4
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

<h1 align="center">leetcode 45.跳跃游戏 II</h1>

### 题目地址
  * https://leetcode.cn/problems/jump-game-ii/
  
### 解法
  1. 贪心
  * 根据当前所在位置和能到达的最远距离，计算下一次可以达到的最远距离，每计算一段，就自增一次count，最终得到跳跃次数
    ```C++
    int jump(vector<int>& nums) 
    {
        int count = 0;
        int left = 0;
        int right = 0;
        for (; right < nums.size() - 1; )
        {
            int max_pos = 0;
            for (int i = left; i <= right; ++i)
            {
                max_pos = max(max_pos, i + nums[i]);
            }
            ++count;
            left = right + 1;
            right = max_pos;
        }

        return count;
    }
    ```