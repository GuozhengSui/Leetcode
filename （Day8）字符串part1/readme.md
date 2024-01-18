## 344. 反转字符串
```python
class Solution:
    def reverseString(self, s: List[str]) -> None:
        """
        Do not return anything, modify s in-place instead.
        """
        # left = 0
        # right = len(s) - 1
        # while left < right:
        #     temp = s[left]
        #     s[left] = s[right]
        #     s[right] = temp
        #     left += 1
        #     right -= 1
        # return s

        n = len(s)
        for i in range(n // 2):
            s[i], s[n - i - 1] = s[n - i - 1], s[i]
        
        return s
```
## 541. 反转字符串 II
```python
class Solution:
    def reverseStr(self, s: str, k: int) -> str:
        
        
        # res = list(s)

        # for cur in range(0, len(s), 2 * k):
        #     res[cur: cur + k] = self.reverse_substring(res[cur: cur + k])
        
        # return ''.join(res)

        res = list(s)

        for i in range(0, len(res), 2*k):
            if i + k <= len(res):
                res[i:i+k] = self.reverse_substring(res[i:i+k])
                continue
            res[i:] = self.reverse_substring(res[i:])
        return ''.join(res)
```
## 151. 反转字符串中的单词
```python
class Solution:
    def reverseWords(self, s: str) -> str:
        words = s.split()
        left = 0
        right = len(words) - 1
        while left < right:
            words[left], words[right] = words[right], words[left]
            left += 1
            right -= 1
        return " ".join(words)
```
