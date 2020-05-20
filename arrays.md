# Arrays

+ [Two Sum](#two-sum)
+ [3Sum](#3sum)
+ [Subarray Sum Equals k](#subarray-sum-equals-k)

## Two Sum

https://leetcode.com/problems/two-sum/

'''python

    def twoSum(nums: List[int], target: int) -> List[int]:
        cache = {}
        for diff, value in enumerate(nums):
            if (target - value) in cache:
                return [cache[target - value], diff]
            if value not in cache:
                cache[value] = diff


    def twoSum_2(self, nums: List[int], target: int) -> List[int]:
        nums_copy = sorted(nums)
        start_pointer = 0
        end_pointer = len(nums) - 1
        while start_pointer != end_pointer:
            if nums_copy[start_pointer] + nums_copy[end_pointer] == target:
                start_pointer = nums.index(nums_copy[start_pointer])
                end_pointer = len(nums) - nums[::-1].index(nums_copy[end_pointer]) - 1
                return [start_pointer, end_pointer]
            elif nums_copy[start_pointer] + nums_copy[end_pointer] < target:
                start_pointer += 1
            else:
                end_pointer -= 1

'''

## 3Sum

https://leetcode.com/problems/3sum/

'''python

'''

## Subarray Sum Equals k

https://leetcode.com/problems/subarray-sum-equals-k/

'''python

'''
