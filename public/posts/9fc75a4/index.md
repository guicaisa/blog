# Leetcode 45.跳跃游戏 II


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

---

> Author: Ciao  
> URL: http://localhost:1313/blog/posts/9fc75a4/  

