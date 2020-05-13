#Intervals

+ [Insert Interval](#insert-interval)
+ [Merge Intervals](#merge-intervals)
+ [Non-overlapping Intervals](#non-overlapping-intervals)

## Insert Interval

https://leetcode.com/problems/insert-interval/

'''python
    
    from typing import List


    def insert(self, intervals: List[List[int]], newInterval: List[int]) -> List[List[int]]:
        i = 0
        while i < len(intervals):
            if (newInterval[0] < intervals[i][0]):
                intervals = intervals[:i] + [newInterval] + intervals[i:]
                break
            i += 1
        else:
            intervals.append(newInterval)
        upd_intervals = intervals[:i]
        for j in range(i, len(intervals)):
            if (intervals[j][0] == upd_intervals[-1][0]):
                upd_intervals[-1][1] = max(intervals[j][-1], upd_intervals[-1][-1])
            elif (intervals[j][0] <= upd_intervals[-1][-1]):
                upd_intervals[-1][1] = max(intervals[j][-1], upd_intervals[-1][-1])
            else:
                upd_intervals.append(intervals[j])
        return upd_intervals
        
        
'''

## Merge Intervals

https://leetcode.com/problems/merge-intervals/

'''python

    from typing import List


    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
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

    from typing import List


    def eraseOverlapIntervals(self, intervals: List[List[int]]) -> int:
        intervals.sort(key=lambda interval: interval[-1])
        count = len(intervals) - 1
        prev_result = intervals[0][-1]
        for i in range(1, len(intervals)):
            if intervals[i][0] >= prev_result:
                count -= 1
                prev_result = intervals[i][-1]
        return count
     
     
'''