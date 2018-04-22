代码来自： [TstsUgeg](https://blog.csdn.net/tstsugeg/article/details/50417850)

## C++

```C++
class Solution {
public:
    int coinChange(vector<int>& coins, int amount) {  
        if(amount < 0) return -1;  
        vector<int> cnt(amount+1, amount+1);  
        cnt[0] = 0;  
        for(int i=1; i<=amount; ++i)
            for(int j=0; j<coins.size(); ++j)  
                if(i>=coins[j])
                    cnt[i] = min(cnt[i], cnt[i-coins[j]] + 1); 
        return (cnt[amount]==amount+1) ? -1 : cnt[amount];  
    }
};
```

- 动态规划问题
- 思路理解：
    - 从 1 元开始直到第一枚硬币的值，以此类推，可以生成合法解（只要 amount-coin 存在解，则 amount 的解为 amount-coin 的解 +1 ）。
    - 如果算到 amount 没有合法解，则就是无解。
