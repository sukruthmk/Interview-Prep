# Maximum Number of Events That Can Be Attended

Given an array of `events` where `events[i] = [startDayi, endDayi]`. Every event `i` starts at `startDayi` and ends at `endDayi`.

You can attend an event `i` at any day `d`where `startTimei <= d <= endTimei`. Notice that you can only attend one event at any time `d`.

Return *the maximum number of events* you can attend.

 

**Example 1:**

![img](https://assets.leetcode.com/uploads/2020/02/05/e1.png)

```
Input: events = [[1,2],[2,3],[3,4]]
Output: 3
Explanation: You can attend all the three events.
One way to attend them all is as shown.
Attend the first event on day 1.
Attend the second event on day 2.
Attend the third event on day 3.
```

**Example 2:**

```
Input: events= [[1,2],[2,3],[3,4],[1,2]]
Output: 4
```

**Example 3:**

```
Input: events = [[1,4],[4,4],[2,2],[3,4],[1,1]]
Output: 4
```

**Example 4:**

```
Input: events = [[1,100000]]
Output: 1
```

**Example 5:**

```
Input: events = [[1,1],[1,2],[1,3],[1,4],[1,5],[1,6],[1,7]]
Output: 7
```

 

**Constraints:**

- `1 <= events.length <= 10^5`
- `events[i].length == 2`
- `1 <= events[i][0] <= events[i][1] <= 10^5`



### Leetcode

https://leetcode.com/problems/maximum-number-of-events-that-can-be-attended/



### Optimal Solution

Time Complexity: O(n^2)

Space Complexity: O(n)

```js
/**
 * @param {number[][]} events
 * @return {number}
 */
var maxEvents = function(events) {
    const set = new Set();
    
    events.sort((a, b) => {
        const [startA, endA] = a;
        const [startB, endB] = b;
        // if end dates are not equal then sort by end date
        // if end dates are equal then sort by start date
        return endA != endB ? endA - endB : startA - startB;
    });
    
    for(const event of events) {
        const [start, end] = event;
        for(let i=start; i<=end; i++) {
            // if the user didn't attend the event on i
            // attend the event
            if(!set.has(i)) {
                set.add(i);
                // break to attend next event
                break;
            }
        }
    }
    
    return set.size;
};
```



### Explanation

https://www.youtube.com/watch?v=stewMnsT31I

Using priority queues

https://leetcode.com/problems/maximum-number-of-events-that-can-be-attended/discuss/516272/JavaScript-Sort-events-%2B-Priority-Queue-when-days-collide-EXPLAINED