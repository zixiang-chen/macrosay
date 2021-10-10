tags: leetcode, algorithm, 

date: 2021-10-10 19:17

---

# LeetCode 2035. Partition Array Into Two Arrays to Minimize Sum Difference

I attended LeetCode Contest 262 today, and solved 3 problems. As for [the last problem](https://leetcode.com/problems/partition-array-into-two-arrays-to-minimize-sum-difference/), I first know the `meet-in-the-middle` algorithm.

## Approach 1: meet in the middle

```python
from bisect import insort, bisect
from collections import defaultdict

class Solution:
    def minimumDifference(self, nums: List[int]) -> int:
        N = len(nums)
        n = N // 2
        deltas = defaultdict(list)
        
        # brute force on the left part
        for mask in range(0, 1 << n):
            c, d = 0, 0
            for i in range(0, n):
                if (mask & (1 << i)):
                    c += 1
                    d += nums[i]
                else:
                    d -= nums[i]
            insort(deltas[c], d)
        
        # a potential answer
        ans = abs(sum(nums[:n]) - sum(nums[n:]))
        
        # brute force on the right part
        for mask in range(0, 1 << n):
            c, d = 0, 0
            for i in range(0, n):
                if (mask & (1 << i)):
                    c += 1
                    d += nums[n + i]
                else:
                    d -= nums[n + i]
            
            # meet
            cc = n - c
            p = bisect(deltas[cc], -d)
            if p < len(deltas[cc]):
                ans = min(ans, abs(deltas[cc][p] + d))
            if (p - 1 >= 0):
                ans = min(ans, abs(deltas[cc][p-1] + d))
        
        return ans
```

TLE, in fact 😥

## References

+ [A `meet-in-the-middle` solution explained in Chinese](https://www.bilibili.com/video/BV1ZL41137pU?p=5)
+ 

