---
title: leetcode 36.有效的数独
subtitle:
date: 2026-03-08T16:24:27+08:00
slug: 61f9188
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

<h1 align="center">leetcode 36.有效的数独</h1>

### 题目地址
  * https://leetcode.cn/problems/valid-sudoku/
  
### 解法
  1. 哈希表
  * 分别构建三个二维哈希表，用于追踪9x9棋盘中每一行、每一列以及每一个3x3宫格内数字1-9的出现情况
  * 直接遍历board的每一个单元格，若当前单元格为数字，则分别检查该数字是否已在对应的行、列或宫格标记位中存在
  * 如果存在，说明违反数独规则，立即返回false，不存在则将该数字对应的标记位设为true
  * 为了将二维坐标(i, j)映射到0-8号宫格索引，通常使用公式cell_id = (i / 3) * 3 + (j / 3)，这能确保棋盘被准确划分为9个独立的区域
  * 由于数字范围固定1-9，使用长度为10的静态数组(或9x9的二维数组)代替哈希表，可以利用内存连续性获得更快的寻址速度，并减少哈希碰撞带来的额外开销
    ```C++
    class Solution 
    {
    public:
        bool isValidSudoku(vector<vector<char>>& board) 
        {
            vector<bool> temp(10, false);
            vector<vector<bool>> row_map(9, temp); //一级数组索引为行号，二级数组索引为数字
            vector<vector<bool>> col_map(9, temp); //一级数组索引为列号，二级数组索引为数字
            vector<vector<bool>> cell_map(9, temp); //一级数组索引为3x3格子号，二级数组索引为数字

            for (int i = 0; i < board.size(); ++i)
            {
                for (int j = 0; j < board[i].size(); ++j)
                {
                    char ch = board[i][j];
                    if (ch == '.')
                    {
                        continue;
                    }
                    int ch_int = ch - '0';
                    int cell_id = i / 3 * 3 + j / 3;
                    if (row_map[i][ch_int] || col_map[j][ch_int] || cell_map[cell_id][ch_int])
                    {
                        return false;
                    }
                    row_map[i][ch_int] = true;
                    col_map[j][ch_int] = true;
                    cell_map[cell_id][ch_int] = true;
                }
            }

            return true;
        }
    };
    ```
