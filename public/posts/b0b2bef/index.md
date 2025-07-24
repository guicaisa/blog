# Leetcode 14.最长公共前缀


<!--more-->

<h1 align="center">leetcode 14.最长公共前缀</h1>

### 题目地址
  * https://leetcode.cn/problems/longest-common-prefix/
  
### 解法
  1. 遍历
  * 以数组中第一个字符串为锚，遍历剩下所有字符串，依次对比每个字符，相同的累积到结果字符串中，发现不同的就直接结束
    ```C++
    string longestCommonPrefix(vector<string>& strs) 
    {
        string result;
        for (int i = 0; i < strs[0].size(); ++i)
        {
            char ch = strs[0][i];
            bool end = false;
            for (int j = 1; j < strs.size(); ++j)
            {
                //注意边界情况，strs[0]的长度可能比其他字符串长
                if (i >= strs[j].size() || strs[j][i] != ch)
                {
                    end = true;
                    break;
                }
            }
            if (end)
            {
                break;
            }
            result += ch;
        }

        return result;
    }
    ```C++



---

> Author: Ciao  
> URL: http://localhost:1313/blog/posts/b0b2bef/  

