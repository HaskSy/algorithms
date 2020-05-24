# Intervals

+ [Insert Interval](#insert-interval)
+ [Merge Intervals](#merge-intervals)
+ [Non-overlapping Intervals](#non-overlapping-intervals)

## Insert Interval

https://leetcode.com/problems/insert-interval/

```python

```

## Merge Intervals

https://leetcode.com/problems/merge-intervals/

```python
def merge(self, intervals: List[List[int]]) -> List[List[int]]:
    if not intervals:
        return intervals
    intervals.sort(key=lambda interval: interval[0])
    result = [intervals[0]]
    for interval in intervals:
        if (interval[0] == result[-1][0]):
            result[-1][1] = max(interval[-1], result[-1][-1])
        elif (interval[0] <= result[-1][-1]):
            result[-1][1] = max(interval[-1], result[-1][-1])
        else:
            result.append(interval)
    return result

```

## Non-overlapping intervals

https://leetcode.com/problems/non-overlapping-intervals

```python
def eraseOverlapIntervals(self, intervals: List[List[int]]) -> int:
    if not intervals:
        return 0
    intervals.sort(key=lambda interval: interval[-1])
    count = len(intervals) - 1
    prev_result = intervals[0][-1]
    for interv in range(1, len(intervals)):
        if intervals[interv][0] >= prev_result:
            count -= 1
            prev_result = intervals[interv][-1]
    return count

```
