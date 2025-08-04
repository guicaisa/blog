---
title: leetcode 125.验证回文串
subtitle:
date: 2025-08-04T20:55:22+08:00
slug: 17fb0da
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

<h1 align="center">leetcode 125.验证回文串</h1>

### 题目地址
  * https://leetcode.cn/problems/valid-palindrome/

### 解法
  1. 双指针
  * 左右指针相向遍历，判断2个字符即可，只需要判断字母字符和数字字符，其他的都可以忽略，判断字符是否相等时，需要注意如果是2个字母字符，需要判断大小写的情况即可
    ```C++
    class Solution 
    {
    public:
        bool isPalindrome(string s) 
        {
            int left = 0;
            int right = s.size() - 1;
            while (left < right)
            {
                char left_ch = s[left];
                if (!isValidCh(left_ch))
                {
                    ++left;
                    continue;
                }

                char right_ch = s[right];
                if (!isValidCh(right_ch))
                {
                    --right;
                    continue;
                }

                bool equal = (left_ch == right_ch) || 
                    (isCharacter(left_ch) && isCharacter(right_ch) && capitalize(left_ch) == capitalize(right_ch));
                if (!equal)
                {
                    return false;
                }
                ++left;
                --right;
            }

            return true;
        }

        bool isValidCh(char ch)
        {
            return isCharacter(ch) || isDigit(ch);
        }

        bool isCharacter(char ch)
        {
            return ('a' <= ch && ch <= 'z') || ('A' <= ch && ch <= 'Z'); 
        }

        bool isDigit(char ch)
        {
            return '0' <= ch && ch <= '9';
        }

        char capitalize(char ch)
        {
            if ('A' <= ch && ch <= 'Z')
            {
                return ch;
            }
            return ch - 32;
        }
    };
    ```
