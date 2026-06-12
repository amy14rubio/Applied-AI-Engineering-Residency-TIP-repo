# Day 1

Iterate from 1 to `n` inclusive. For each number:

- If the number is divisible by both 3 and 5, append `"FizzBuzz"` to `answer`
- Else if the number is divisible by 3, append `"Fizz"` to `answer`
- Else if the number is divisible by 5, append `"Buzz"` to `answer`
- Otherwise, append the number as a string

Return `answer`

```py
class Solution:
    def fizzBuzz(self, n: int) -> List[str]:
        answer = []
        for i in range(1,n+1):
            if i % 15 == 0:
                answer.append('FizzBuzz')
            elif i % 3 == 0:
                answer.append('Fizz')
            elif i % 5 == 0:
                answer.append('Buzz')
            else:
                answer.append(str(i))
        return answer
```
