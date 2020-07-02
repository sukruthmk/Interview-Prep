# Height Checker

Students are asked to stand in non-decreasing order of heights for an annual photo.

Return the minimum number of students that must move in order for all students to be standing in non-decreasing order of height.

Notice that when a group of students is selected they can reorder in any possible way between themselves and the non selected students remain on their seats.

 

**Example 1:**

```
Input: heights = [1,1,4,2,1,3]
Output: 3
Explanation: 
Current array : [1,1,4,2,1,3]
Target array  : [1,1,1,2,3,4]
On index 2 (0-based) we have 4 vs 1 so we have to move this student.
On index 4 (0-based) we have 1 vs 3 so we have to move this student.
On index 5 (0-based) we have 3 vs 4 so we have to move this student.
```

**Example 2:**

```
Input: heights = [5,1,2,3,4]
Output: 5
```

**Example 3:**

```
Input: heights = [1,2,3,4,5]
Output: 0
```

 

**Constraints:**

- `1 <= heights.length <= 100`

- `1 <= heights[i] <= 100`

  

### Leetcode

https://leetcode.com/problems/height-checker/



### Optimal Solution

Time Complexity:

Space Complexity:

```js
/**
 * @param {number[]} heights
 * @return {number}
 */
var heightChecker = function(heights) {
    const counts = new Array(101).fill(0);
    
    // create an array with counts for each number
    for(const height of heights) {
        counts[height]++;
    }
    
    let index = 0;
    let output = 0;
    
    // iterate over all 100 numbers
    for(let i = 0; i<counts.length; i++) {
        if(counts[i] === 0) continue;
        while(counts[i] > 0) {
            // since index is sorted
            // we just need to check if the values are not same
            // if not same then we can assume that
            // we have to swap this position to sort the input array.
            if(i != heights[index]) {
                output++;
            }
            index++;
            counts[i]--;
        }
    }
    
    return output;
};
```
