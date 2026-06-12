# Day 5

Two-pointer solution:

- Negative numbers cannot be palindromes, so return `False` if `x` is negative
- Convert the integer to a string
- Initialize a left pointer at the beginning of the string and a right pointer at the end
- Compare the characters at both pointers:
  - If they are different, return `False`
  - Otherwise, move the pointers toward each other
- Continue until the pointers meet

Return `True` if all corresponding characters match

```py
def isPalindrome(self, x: int) -> bool:
    if x < 0: return False
    s = str(x)
    left = 0
    right = len(s) - 1
    while left < right:
        if s[left] != s[right]: return False
        left += 1
        right -= 1
    return True
```

Two-pointer solution:

- Sort the array
- Iterate through the array, treating each number as the first number of a potential triplet
- Skip duplicate values to avoid returning duplicate triplets
- For each number, use two pointers:
  - `left` starts immediately after the current number
  - `right` starts at the end of the array
- Calculate the sum of the three numbers:
  - If the sum is 0, add the triplet to the result and move both pointers while skipping duplicates
  - If the sum is less than 0, move `left` to increase the sum
  - If the sum is greater than 0, move `right` to decrease the sum
- Continue until the pointers meet

Return all unique triplets whose sum is 0

```py
def threeSum(self, nums: list[int]) -> list[list[int]]:
    result = []
    nums.sort()
    for i in range(len(nums) - 2):
        if i > 0 and nums[i] == nums[i-1]: continue
        left = i + 1
        right = len(nums) - 1
        while(left < right):
            sum = nums[i] + nums[left] + nums[right]
            if sum == 0:
                result.append([nums[i], nums[left], nums[right]])
                while left < right and nums[left] == nums[left + 1]: left += 1
                while left < right and nums[right] == nums[right - 1]: right -= 1
                left += 1
                right -= 1
            elif sum < 0:
                left += 1
            else:
                right -= 1
    return result
```
