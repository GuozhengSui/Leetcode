## 977. 有序数组的平方
```python
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        li = [0] * len(nums)
        left, right = 0, len(nums) - 1
        i = len(nums) - 1
        while left <= right:
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
