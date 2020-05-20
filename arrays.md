# Arrays

+ [Two Sum](#two-sum)
+ [3Sum](#3sum)
+ [Subarray Sum Equals k](#subarray-sum-equals-k)

## Two Sum

https://leetcode.com/problems/two-sum/

'''python

'''

## 3Sum

https://leetcode.com/problems/3sum/

'''python

'''

## Subarray Sum Equals k

https://leetcode.com/problems/subarray-sum-equals-k/

'''python

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
