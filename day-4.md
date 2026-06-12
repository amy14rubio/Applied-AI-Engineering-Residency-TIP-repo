# Day 4

Keep track of previously seen numbers in a set

- For each number:
  - If it has already been seen, return `True`
  - Otherwise, add it to the set

Return `False` if no duplicates are found

```py
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        seen = set()
        for num in nums:
            if num in seen: return True
            seen.add(num)
        return False
```

- For each string, sort its characters to create a key and store the original string in a hash map under that key
- Strings that are anagrams will have the same sorted key and end up in the same group

Return the values of the hash map

```py
from collections import defaultdict

class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        map = defaultdict(list)
        for str in strs:
            map["".join(sorted(str))].append(str)
        return list(map.values())
```
