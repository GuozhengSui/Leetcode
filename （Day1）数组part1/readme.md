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

[27 移除元素](https://leetcode.cn/problems/remove-element/)

```python
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        fast = 0
            slow = 0
            size = len(nums)
            while fast < size:
                if nums[fast] != val:
                    nums[slow] = nums[fast]
                    slow += 1
                fast += 1
            return slow
```
