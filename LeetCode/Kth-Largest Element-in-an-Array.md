# Kth Largest Element in an Array

Find the **k**th largest element in an unsorted array. Note that it is the kth largest element in the sorted order, not the kth distinct element.

**Example 1:**

```
Input: [3,2,1,5,6,4] and k = 2
Output: 5
```

**Example 2:**

```
Input: [3,2,3,1,2,4,5,5,6] and k = 4
Output: 4
```

**Note:** 
You may assume k is always valid, 1 ≤ k ≤ array's length.



### Leetcode

https://leetcode.com/problems/kth-largest-element-in-an-array/



### Optimal Solution

##### Approach 1 - Sorting

Time Complexity: O(nlogn)

Space Complexity: O(1)

```js
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number}
 */
var findKthLargest = function(nums, k) {
  // sort
  nums.sort((a, b) => a-b);
  return nums[nums.length - k];
};
```



##### Approach 2 - Quick Select

Time Complexity: O(nlogn)

Space Complexity: O(1)

```js
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number}
 */
var findKthLargest = function(nums, k) {
  return quickSelect(nums, 0, nums.length - 1, k);
};

const quickSelect = (nums, low, high, k) => {
  let pivot = low;

  // use quick sort's idea
  // put nums that are <= pivot to the left
  // put nums that are  > pivot to the right
  for (let j = low; j < high; j++) {
    if (nums[j] <= nums[high]) {
      swap(nums, pivot, j);
      pivot++;
    }
  }
  swap(nums, pivot, high);
  
  // count the nums that are > pivot from high
  let count = high - pivot + 1;
  // pivot is the one!
  if (count == k) return nums[pivot];
  // pivot is too small, so it must be on the right
  if (count > k) return quickSelect(nums, pivot + 1, high, k);
  // pivot is too big, so it must be on the left
  return quickSelect(nums, low, pivot - 1, k - count);
}

const swap = (nums, i, j) => {
  const temp = nums[i];
  nums[i] = nums[j];
  nums[j] = temp;
}
```

