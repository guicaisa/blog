---
title: leetcode 11.盛最多水的容器
subtitle:
date: 2025-08-21T22:33:48+08:00
slug: 05467b9
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

<h1 align="center">leetcode 11.盛最多水的容器</h1>

### 题目地址
  * https://leetcode.cn/problems/container-with-most-water/

### 解法
  1. 双指针
  * 左右指针相向遍历，根据短边计算每次的面积，将较大值保存在结果中，每次遍历时移动短边，在宽度变小的情况下，提高高度才能获得更大的结果
  
    ![](./p1.gif)
    ```C++
    int maxArea(vector<int>& height) 
    {
        int max_area = 0;
        int left = 0;
        int right = height.size() - 1;
        while (left <= right)
        {
            int h = min(height[left], height[right]);
            int w = right - left;
            max_area = max(max_area, h * w);
            if (height[left] < height[right])
            {
                ++left;
            }
            else
            {
                --right;
            }
        }

        return max_area;
    }
    ```
