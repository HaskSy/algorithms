# Arrays

+ [Two Sum](#two-sum)
+ [3Sum](#3sum)
+ [Subarray Sum Equals k](#subarray-sum-equals-k)

## Two Sum

https://leetcode.com/problems/two-sum/

```python

    def twoSum(nums: List[int], target: int) -> List[int]:
        cache = {}
        for diff, value in enumerate(nums):
            if (target - value) in cache:
                return [cache[target - value], diff]
            if value not in cache:
                cache[value] = diff


    def twoSum(self, nums: List[int], target: int) -> List[int]:
        nums_copy = [(nums[i], i) for i in range(len(nums))]
        nums_copy.sort(key=lambda elem: elem[0])
        left = 0
        right = len(nums) - 1
        while left != right:
            if nums_copy[left][0] + nums_copy[right][0] == target:
                return [nums_copy[left][1], nums_copy[right][1]]
            elif nums_copy[left][0] + nums_copy[right][0] < target:
                left += 1
            else:
                right -= 1

```

## 3Sum

https://leetcode.com/problems/3sum/

```python

```

## Subarray Sum Equals k

https://leetcode.com/problems/subarray-sum-equals-k/

```python

```
