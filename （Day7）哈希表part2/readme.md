关键词:不重复，是在一个数组中还是在多个数组中，决定了使用哈希方法还是双指针。
## 454. 四数相加 II
```python
class Solution:
    def fourSumCount(self, nums1: List[int], nums2: List[int], nums3: List[int], nums4: List[int]) -> int:

        hashmap = dict()
        for i in range(len(nums1)):
            for j in range(len(nums2)):
                sum = nums1[i] + nums2[j]
                if sum in hashmap:
                    hashmap[sum] += 1
                else:
                    hashmap[sum] = 1
        
        count = 0
        for i in range(len(nums3)):
            for j in range(len(nums4)):
               if -(nums3[i] + nums4[j]) in hashmap:
                   count += hashmap[-(nums3[i] + nums4[j])]
        return count
```

## 15. 三数之和
```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        result = []
        nums.sort()

        for i in range(len(nums)):
            if i > 0 and nums[i] == nums[i-1]:
                continue
            left = i + 1
            right = len(nums) - 1
            
            while left < right:
                if nums[i] + nums[left] + nums[right] > 0:
                    right -= 1
                elif nums[i] + nums[left] + nums[right] < 0:
                    left += 1
                else:
                    result.append([nums[i], nums[left], nums[right]])
                    while left < right and nums[left] == nums[left+1]:
                        left += 1
                    while left < right and nums[right] == nums[right-1]:
                        right -= 1
                    left += 1
                    right -= 1
        return result
```
## 18. 四数之和
```python
class Solution:
    def fourSum(self, nums: List[int], target: int) -> List[List[int]]:
        nums.sort()
        size = len(nums)
        result = []
        for i in range(size):
            if i > 0 and nums[i] == nums[i-1]:
                continue
            for j in range(i+1, size):
                if j > i + 1 and nums[j] == nums[j-1]:
                    continue
                left = j + 1
                right = size - 1
                while left < right:
                    sum = nums[i] + nums[j] + nums[left] + nums[right]
                    if sum < target:
                        left += 1
                    elif sum > target:
                        right -= 1
                    else:
                        result.append([nums[i], nums[j], nums[left], nums[right]])
                        while left < right and nums[left] == nums[left+1]:
                            left += 1
                        while left < right and nums[right] == nums[right-1]:
                            right -= 1
                        left += 1
                        right -= 1
        return result    
  ```
## 383. 赎金信
```python
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:       
        #哈希
        ransom_count = [0] * 26
        magazine_count = [0] * 26
        for c in ransomNote:
            ransom_count[ord(c) - ord('a')] += 1
        for c in magazine:
            magazine_count[ord(c) - ord('a')] += 1
        return all(ransom_count[i] <= magazine_count[i] for i in range(26))
```
