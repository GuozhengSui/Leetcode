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
```python
class Solution:
    def minSubArrayLen(self, target: int, nums: List[int]) -> int:
        slow = 0
        ans = 0
        result = float('inf')

        for i in range(len(nums)):  #我的理解是i代表了快指针fast，fast走到停止条件，慢指针再走
            ans += nums[i]
            while ans>= target:
                ans -= nums[slow]
                result = min(result, i - slow + 1)
                slow += 1
        return result if result != float('inf') else 0
```
## 59. 螺旋矩阵 II
```python
class Solution:
    def generateMatrix(self, n: int) -> List[List[int]]:
        matrix = [[0 for i in range(n)] for j in range(n)]
        count = 1
        loop = n // 2
        startx, starty = 0, 0
        offset = 1
        mid = n // 2
        while loop:
            for j in range(starty, n - offset):
                matrix[startx][j] = count
                count += 1
            for i in range(startx, n - offset):
                matrix[i][n-offset] = count
                count += 1
            for j in range(n-offset, starty, -1):
                matrix[n-offset][j] = count
                count += 1
            for i in range(n-offset, startx, -1):
                matrix[i][starty] = count
                count += 1
            startx += 1
            starty += 1
            offset += 1
            loop -= 1
        if n % 2:
            matrix[mid][mid] = n ** 2
        return matrix
```
