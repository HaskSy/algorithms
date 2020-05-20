# Intervals

+ [Insert Interval](#insert-interval)
+ [Merge Intervals](#merge-intervals)
+ [Non-overlapping Intervals](#non-overlapping-intervals)

## Insert Interval

https://leetcode.com/problems/insert-interval/

```python

    def insert(self, intervals: List[List[int]], newInterval: List[int]) -> List[List[int]]:
        if not intervals:
            return [newInterval]
        if not newInterval:
            return intervals
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
            if not upd_intervals:
                upd_intervals.append(intervals[j])
            elif (intervals[j][0] == upd_intervals[-1][0]):
                upd_intervals[-1][1] = max(intervals[j][-1], upd_intervals[-1][-1])
            elif (intervals[j][0] <= upd_intervals[-1][-1]):
                upd_intervals[-1][1] = max(intervals[j][-1], upd_intervals[-1][-1])
            else:
                upd_intervals.append(intervals[j])
        return upd_intervals

```

## Merge Intervals

https://leetcode.com/problems/merge-intervals/

```python

```

## Non-overlapping intervals

https://leetcode.com/problems/non-overlapping-intervals

```python

```
