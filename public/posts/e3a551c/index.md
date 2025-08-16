# Leetcode 392.判断子序列


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



---

> Author: Ciao  
> URL: http://localhost:1313/blog/posts/e3a551c/  

