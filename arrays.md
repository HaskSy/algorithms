# Arrays

+ [Two Sum](#two-sum)
+ [3Sum](#3sum)
+ [Subarray Sum Equals k](#subarray-sum-equals-k)

## Two Sum

https://leetcode.com/problems/two-sum/

```python

```

## 3Sum

https://leetcode.com/problems/3sum/

```python

    def threeSum(self, nums: List[int]) -> List[List[int]]:
        result = []
        nums.sort()
        for i in range(len(nums)):
            if (i != 0) and (nums[i] == nums[i - 1]):
                continue
            start_pointer = i + 1
            end_pointer = len(nums) - 1
            while (start_pointer < end_pointer):
                if not (nums[i] + nums[start_pointer] + nums[end_pointer]):
                    result.append([nums[i], nums[start_pointer], nums[end_pointer]])
                    start_pointer += 1
                    while (start_pointer < end_pointer) and (nums[start_pointer] == nums[end_pointer]):
                        start_pointer += 1
                elif (nums[i] + nums[start_pointer] + nums[end_pointer] < 0):
                    start_pointer += 1
                else:
                    end_pointer -= 1

        n = []
        for i in result:
            if not n or i != n[-1]:
                n.append(i)
        return n

```

## Subarray Sum Equals k

https://leetcode.com/problems/subarray-sum-equals-k/

```python

```
