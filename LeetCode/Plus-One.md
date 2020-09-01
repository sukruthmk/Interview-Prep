# Plus One

Given a **non-empty** array of digits representing a non-negative integer, increment one to the integer.

The digits are stored such that the most significant digit is at the head of the list, and each element in the array contains a single digit.

You may assume the integer does not contain any leading zero, except the number 0 itself.



**Example 1:**

```
Input: digits = [1,2,3]
Output: [1,2,4]
Explanation: The array represents the integer 123.
```

**Example 2:**

```
Input: digits = [4,3,2,1]
Output: [4,3,2,2]
Explanation: The array represents the integer 4321.
```

**Example 3:**

```
Input: digits = [0]
Output: [1]
```

 

**Constraints:**

- `1 <= digits.length <= 100`
- `0 <= digits[i] <= 9`



### Leetcode

https://leetcode.com/problems/plus-one/



### Optimal Solution

Time Complexity: O(n)

Space Complexity: O(n)

```js
/**
 * @param {number[]} digits
 * @return {number[]}
 */
var plusOne = function(digits) {
    // get the last digit sum and add plus one.
    let lastSum = digits.pop() + 1;
    let carry = Math.floor(lastSum/10);
    // use string number to prepend the calculation
    let number = "" + lastSum % 10;
    
    for(let i=digits.length-1; i>=0; i--) {
        const sum = digits[i] + carry;
        carry = Math.floor(sum/10);
        // prepend remainder to number
        number = sum % 10 + number;
    }
    
    if(carry > 0) {
        number = carry + number;
    }
    
    return number.split("");
};
```
