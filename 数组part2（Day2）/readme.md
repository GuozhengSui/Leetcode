## 977. 有序数组的平方
```python
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        li = [0] * len(nums)
        left, right = 0, len(nums) - 1
        i = len(nums) - 1
        while left <= right:                         #涉及到双指针问题，终止条件设置为左==右
            if nums[left] ** 2 < nums[right] ** 2:
                li[i] = nums[right] ** 2
                right -= 1
                i -= 1
            else:
                li[i] = nums[left] ** 2
                left += 1
                i -= 1
        return li
```
## 209. 长度最小的子数组
···python
class Solution:
    def minSubArrayLen(self, target: int, nums: List[int]) -> int:
        slow = 0
        ans = 0
        result = float('inf')

        for i in range(len(nums)):
            ans += nums[i]
            while ans>= target:
                ans -= nums[slow]
                result = min(result, i - slow + 1)
                slow += 1
        return result if result != float('inf') else 0
···
