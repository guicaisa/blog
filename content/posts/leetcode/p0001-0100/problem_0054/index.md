---
title: leetcode 54.螺旋矩阵
subtitle:
date: 2026-03-08T18:43:29+08:00
slug: ff3d3ae
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

<h1 align="center">leetcode 54.螺旋矩阵</h1>

### 题目地址
  * https://leetcode.cn/problems/spiral-matrix/

### 解法
  1. 遍历
  * 设定四个边界变量top,bottom,left,right，分别代表当前尚未遍历区域的上,下,左,右边界
  * 按照"左->右","上->下","右->左","下->上"的固定顺序循环遍历当前层，完成当前层的遍历之后，将边界向中心移动一位，++top,--bottom,++left,--right
  * 在遍历每一层的后两个方向"右->左"和"下->上"之前，必须进行二次检查，如果top等于bottom-1或者left等于right-1，则表示最后一层已退化成了一维数组(单行或者单列)，此时应停止后续方向的遍历，否则会导致已访问过的元素被重复计入结果
  * 当左边界超过右边界或者上边界超过下边界时，表示所有层级已处理完，结束遍历，返回结果
    ```C++
    class Solution 
    {
    public:
        vector<int> spiralOrder(vector<vector<int>>& matrix) 
        {
            vector<int> results;
            int top = 0;
            int bottom = matrix.size();
            int left = 0;
            int right = matrix[0].size();

            while (1)
            {
                for (int i = left; i < right; ++i)
                {
                    results.push_back(matrix[top][i]);
                }
                for (int i = top+1; i < bottom; ++i)
                {
                    results.push_back(matrix[i][right-1]);
                }
                //如果当前层退化为了一维数组，则不需要遍历"右->左"和"下->上"两个方向，不然会出现重复的元素
                if (left < right-1 && top < bottom-1) 
                {
                    for (int i = right - 2; i >= left+1; --i)
                    {
                        results.push_back(matrix[bottom-1][i]);
                    }
                    for (int i = bottom - 1; i >= top + 1; --i)
                    {
                        results.push_back(matrix[i][left]);
                    }
                }
              
                if (++top >= --bottom)
                {
                    break;
                }
                if (++left >= --right)
                {
                    break;
                }
            }

            return results;
        }
    };
    ```