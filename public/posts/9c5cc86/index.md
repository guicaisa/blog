# Leetcode 55.跳跃游戏


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



---

> Author: Ciao  
> URL: http://localhost:1313/blog/posts/9c5cc86/  

