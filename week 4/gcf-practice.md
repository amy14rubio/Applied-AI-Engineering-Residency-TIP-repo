```py
# loop through nums and save to a running sum var
# running_total = 0
# solution = []
# for num in nums
# running_total += num
# solution.append(running_total)

class Solution:
def runningSum(self, nums: List[int]) -> List[int]:
running_total = 0
solution = []
for num in nums:
running_total += num
solution.append(running_total)
return solution
```

```py
# k -> detemines sliding window length
# expected output: maximum # of vowel letters

# freq = {a:0, e:0, i:0, o:0, u:0}
# vowels = [a,e,i,o,u]
# max_count = 0
# l = 0
# for r in range(k, len(s)):
#   sub = s[l:r]
#   count = 0
#   for i in range(len(sub)):
#       if sub[i] in vowels:
#           count += 1
#   max_count = max(max_count, count)

class Solution:
    def maxVowels(self, s: str, k: int) -> int:
        vowels = ['a','e','i','o','u']
        max_count = 0
        count = 0

        for i in range(k):
            if s[i] in vowels:
                count += 1

        max_count = max(max_count, count)

        for i in range(k,len(s)):
            if s[i] in vowels:
                count += 1
            if s[i-k] in vowels:
                count -= 1
            max_count = max(max_count, count)

        return max_count
```

```py
# keep track of running total sum and subtract target sum from running total to see if there was a prev prefix sum
from collections import defaultdict

class Solution:
    def subarraySum(self, nums: List[int], k: int) -> int:
        seen = defaultdict(int)
        seen[0] = 1

        running_total = 0
        count = 0

        for num in nums:
            running_total += num
            if running_total - k in seen:
                count += seen[running_total-k]
            seen[running_total] += 1
        return count

```
