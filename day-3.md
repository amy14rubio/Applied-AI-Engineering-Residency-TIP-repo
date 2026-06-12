# Day 3

Two-pointer solution:

- Start with pointers at both ends of `s`
- Swap the characters at the left and right pointers
- Move the pointers toward each other after each swap
- Continue until the pointers meet

The array is reversed in-place

```py
class Solution:
    def reverseString(self, s: List[str]) -> None:
        """
        Do not return anything, modify s in-place instead.
        """
        left = 0
        right = len(s) - 1

        while left < right:
            temp = s[left]
            s[left] = s[right]
            s[right] = temp
            left += 1
            right -= 1
```

Sliding window:

- Keep a dictionary of seen characters and their most recent indices
- Iterate through the string with a right pointer
- When a character is repeated within the current window, move the left pointer to the index after the previous occurrence of that character
- Record the current index of the character
- Calculate the current window length (`right - left + 1`) and update the maximum length if necessary

Return the maximum length found

```py
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        seen = {}
        left = 0
        maxLength = 0
        for right in range(len(s)):
            if s[right] in seen and seen[s[right]] >= left:
                left = seen[s[right]] + 1
            seen[s[right]] = right
            maxLength = max(maxLength, right - left + 1)
        return maxLength
```
