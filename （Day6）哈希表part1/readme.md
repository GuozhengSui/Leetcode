# 哈希表

## 242. 有效的字母异位词
```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        from collections import Counter

        a = Counter(s)
        b = Counter(t)
        return a == b
```
## 349. 两个数组的交集
```python
# nums = [0] * 1000
        li = []
        for i in range(len(nums1)):
            nums[nums1[i]] += 1
        
        for i in range(len(nums2)):
            if nums[nums2[i]] != 0:
                li.append(nums2[i])
                nums[nums2[i]] = 0
        
        return li
```
## 202. 快乐数
```python
class Solution:
    def isHappy(self, n: int) -> bool:
        record = set()
        while n not in record:
            record.add(n)
            num_sum = 0
            n_str = str(n)
            for i in n_str:
                num_sum += int(i) ** 2
            if num_sum == 1:
                return True
            else:
                n = num_sum
        
        return False
```
## 1. 两数之和
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:


        # for i in range(len(nums)):
        #     for j in range(i+1, len(nums)):
        #         sum = nums[i] + nums[j]
        #         if sum == target:
        #             return [i, j]

        seen = set()
        for i, x in enumerate(nums):
            component = target - x
            if component in seen:
                return [nums.index(component), i]
            seen.add(nums[i])
```
