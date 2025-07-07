---
title: leetcode 55.跳跃游戏
subtitle:
date: 2025-07-07T16:40:32+08:00
slug: 9c5cc86
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

<h1 align="center">leetcode 55.跳跃游戏</h1>

### 题目地址
  * https://leetcode.cn/problems/jump-game/

### 解法
  1. 遍历
  * 遍历过程中，不断更新当前可以到达的最远位置max_pos，如果max_pos可以到达数组末尾，则返回true，在遍历过程中一旦发现max_pos小于当前遍历的位置，则表示无法到达，返回false
    ```C++
    bool canJump(vector<int>& nums) 
    {
        int max_pos = 0;
        for (int i = 0; i < nums.size(); ++i)
        {
            if (i > max_pos)
            {
                return false;
            }
            //i + nums[i]表示从当前位置上可以到达的最远位置
            max_pos = max(max_pos, i + nums[i]);
            if (max_pos >= nums.size() - 1)
            {
                return true;
            }
        }

        return true;
    }
    ```

