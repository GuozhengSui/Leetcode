[704 二分查找](https://leetcode.cn/problems/binary-search/description/)
====
```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        left, right = 0, len(nums) - 1
        while left <= right:
            mid = (left + right) // 2
            if target > nums[mid]:
                left = mid + 1
            elif target < nums[mid]:
                right  = mid - 1
            else:
                return mid
        return -1
```
使用双指针进行二分查找，问题的关键在于边界条件。
