# Intervals

+ [Insert Interval](#insert-interval)
+ [Merge Intervals](#merge-intervals)
+ [Non-overlapping Intervals](#non-overlapping-intervals)

## Insert Interval

https://leetcode.com/problems/insert-interval/

```python
def insert(self, intervals, newInterval):
    """
    :type intervals: List[List[int]]
    :type newInterval: List[int]
    :rtype: List[List[int]]
    """
    middle = [newInterval[0], newInterval[1]]
    left = []
    right = []

    for interv in intervals: 
        if interv[1] < middle[0]: 
            left.append(interv)
        elif interv[0] > middle[1]: 
            right.append(interv)
        else: 
            middle[0] = min(interv[0], middle[0])
            middle[1] = max(interv[1], middle[1])
    return left + [middle] + right


def insert(self, intervals, newInterval):
    """
    :type intervals: List[List[int]]
    :type newInterval: List[int]
    :rtype: List[List[int]]
    """
    intervals.append(newInterval)
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

## Merge Intervals

https://leetcode.com/problems/merge-intervals/

```python

```

## Non-overlapping intervals

https://leetcode.com/problems/non-overlapping-intervals

```python

```
