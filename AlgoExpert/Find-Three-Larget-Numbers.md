# Find Three Larget Numbers

Given a **non-empty** array of integers, return the **third**maximum number in this array. If it does not exist, return the maximum number. The time complexity must be in O(n).

**Example 1:**

```
Input: [3, 2, 1]

Output: 1

Explanation: The third maximum is 1.
```



**Example 2:**

```
Input: [1, 2]

Output: 2

Explanation: The third maximum does not exist, so the maximum (2) is returned instead.
```



**Example 3:**

```
Input: [2, 2, 3, 1]

Output: 1

Explanation: Note that the third maximum here means the third maximum distinct number.
Both numbers with value 2 are both considered as second maximum.
```



### Leetcode

https://leetcode.com/problems/third-maximum-number/



### Optimal Solution

Time Complexity: O(n) - since the sort and index hapens for constant variable times 3 we can ignore it

Space Complexity: O(1) - since we only store max of 3 we can ignore that space

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var thirdMax = function(nums) {
    // will be using this array like a max heap
    const maxValues = [];
    
    for(const num of nums) {
        // check to remove duplicates
        if(maxValues.indexOf(num) === -1) {
            maxValues.push(num);
            // sort descending
            maxValues.sort((a, b) => b - a);
        }
        
        if(maxValues.length > 3) {
            // pop the last element since it can't be a max of 3
            maxValues.pop();
        }
    }
    
    // return last value in array if 3rd maximum exists
    // or else return the first maximum
    return maxValues.length !== 3 ? maxValues.shift() : maxValues.pop();
};
```
