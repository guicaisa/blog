---
title: leetcode 12.整数转罗马数字
subtitle:
date: 2025-07-21T06:26:03+08:00
slug: df904fc
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

<h1 align="center">leetcode 12.整数转罗马数字</h1>

### 题目地址
  * https://leetcode.cn/problems/integer-to-roman/

### 解法
  1. 按位处理
  * 从个位数开始处理每个进位上的数字，特殊处理下4和9即可
    ```C++
    class Solution 
    {
    public:
        Solution() {
            unordered_map<int, char> temp = {
                {1, 'I'},
                {5, 'V'},
                {10, 'X'}
            };
            nmap_[1] = temp;

            temp = {
                {1, 'X'},
                {5, 'L'},
                {10, 'C'}
            };
            nmap_[10] = temp;

            temp = {
                {1, 'C'},
                {5, 'D'},
                {10, 'M'}
            };
            nmap_[100] = temp;

            temp = {
                {1, 'M'}
            };
            nmap_[1000] = temp;
        }

        //1. 按位处理
        //从个位数开始处理每个进位上的数字，特殊处理下4和9即可
        string intToRoman(int num) 
        {
            string result;
            int step = 1; //当前进位(个十百千)
            while (num)
            {
                int temp = num % 10;
                switch (temp)
                {
                    case 0:
                    break;
                    case 4: //数字4特殊处理，例如IV
                    result = nmap_[step][5] + result;
                    result = nmap_[step][1] + result;
                    break;
                    case 9: //数字9特殊处理，例如IX
                    result = nmap_[step][10] + result;
                    result = nmap_[step][1] + result;
                    break;
                    default:
                    string t;
                    //先加个5
                    if (temp >= 5)
                    {
                        t += nmap_[step][5];
                        temp %= 5;
                    }
                    //再加剩下的temp个1
                    for (int i = 0; i < temp; ++i)
                    {
                        t += nmap_[step][1];
                    }
                    result = t + result;
                    break;
                }
                //进位
                step *= 10; 
                num /= 10;
            }

            return result;
        }

        unordered_map<int, unordered_map<int, char>> nmap_;
    };
    ```

