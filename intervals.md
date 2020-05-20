# Intervals

+ [Insert Interval](#insert-interval)
+ [Merge Intervals](#merge-intervals)
+ [Non-overlapping Intervals](#non-overlapping-intervals)

## Insert Interval

https://leetcode.com/problems/insert-interval/

'''python

'''

## Merge Intervals

https://leetcode.com/problems/merge-intervals/

'''python

  def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        if not intervals:
            return intervals
        intervals.sort(key=lambda interval: interval[0])
        mergeabled = [intervals[0]]
        for interval in intervals:
            if (interval[0] == mergeabled[-1][0]):
                mergeabled[-1][1] = max(interval[-1], mergeabled[-1][-1])
            elif (interval[0] <= mergeabled[-1][-1]):
                mergeabled[-1][1] = max(interval[-1], mergeabled[-1][-1])
            else:
                mergeabled.append(interval)
        return mergeabled

'''

## Non-overlapping intervals

https://leetcode.com/problems/non-overlapping-intervals

'''python

'''
