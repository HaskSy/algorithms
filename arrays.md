# Arrays

+ [Two Sum](#two-sum)
+ [3Sum](#3sum)
+ [Subarray Sum Equals k](#subarray-sum-equals-k)

## Two Sum

https://leetcode.com/problems/two-sum/

'''python

    
    from typing import List


    def twoSum(nums: List[int], target: int) -> List[int]:
        start_pointer = 0
        end_pointer = len(nums) - 1
        nums.sort()
        while start_pointer != end_pointer:
            if (nums[start_pointer] + nums[end_pointer] == target):
                return [start_pointer, end_pointer]
            elif (nums[start_pointer] + nums[end_pointer] < target):
                start_pointer += 1
            elif (nums[start_pointer] + nums[end_pointer] > target):
                end_pointer -= 1    
    
    
'''

## 3Sum

https://leetcode.com/problems/3sum/

'''python


    from typing import List


    def threeSum(self, nums: List[int]) -> List[List[int]]:
        result = []
        # nums = list(set(nums))
        nums.sort()
        for i in range(len(nums)):
            if (i != 0) and (nums[i] == nums[i - 1]):
                continue
            start_pointer = i + 1
            end_pointer = len(nums) - 1
            while (start_pointer < end_pointer):
                if (nums[i] + nums[start_pointer] + nums[end_pointer] == 0):
                    result.append([nums[i], nums[start_pointer], nums[end_pointer]])
                    start_pointer += 1
                    while (start_pointer < end_pointer) and (nums[start_pointer] == nums[end_pointer]):
                        start_pointer += 1
                elif (nums[i] + nums[start_pointer] + nums[end_pointer] < 0):
                    start_pointer += 1
                else:
                    end_pointer -= 1
        return result


'''

## Subarray Sum Equals k

https://leetcode.com/problems/subarray-sum-equals-k/

'''python


    from typing import List


    def subarraySum(self, nums: List[int], k: int) -> int:
        hash_sum = {}
        index_sum = 0
        count = 0
        for i in nums:
            index_sum += i
            check_sum = index_sum - k
            if index_sum == k:
                count += 1
            if check_sum in hash_sum:
                count += hash_sum[check_sum]
            if index_sum not in hash_sum:
                hash_sum[index_sum] = 1
            else:
                hash_sum[index_sum] += 1
        return count


'''