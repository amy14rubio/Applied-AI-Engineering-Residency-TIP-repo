# Day 2

Two-pointer solution:

- Iterate through each number in `nums`
- For each number, check every number that comes after it
- If the sum of the two numbers equals `target`, return their indices

```py
def twoSum(self, nums: List[int], target: int) -> List[int]:
    for i, num in enumerate(nums):
        for j in range(i+1,len(nums)):
            if num + nums[j] == target:
                return [i, j]
```

Set the minimum price to infinity and the maximum profit to 0

- For each price:
  - If the price is less than the current minimum price, update the minimum price
  - Otherwise, calculate the profit from selling at the current price and update the maximum profit if it is larger

Return the maximum profit

```py
def maxProfit(self, prices: List[int]) -> int:
    minPrice = float('inf')
    maxProfit = 0
    for price in prices:
        if price < minPrice:
            minPrice = price
        elif price - minPrice > maxProfit:
            maxProfit = price - minPrice
    return maxProfit
```
