# Reverse Integer

Given a 32-bit signed integer, reverse digits of an integer.

**Example 1:**

```
Input: 123
Output: 321
```

**Example 2:**

```
Input: -123
Output: -321
```

**Example 3:**

```
Input: 120
Output: 21
```

**Note:**
Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−231, 231 − 1]. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.



### Leetcode

https://leetcode.com/problems/reverse-integer/



### Solution

##### Approach 1 - Using array reverse

Time Complexity: O(n)

Space Complexity: O(n)

```js
/**
 * @param {number} x
 * @return {number}
 */
var reverse = function(x) {
    const chars = x.toString().split("");
    let sign = "";
    
    // check for sign operator
    if(chars[0] === "+" || chars[0] === "-") {
        sign = chars.shift(); // take the sign
    }
    
    // limits for out of bound
    const max_positive = Math.pow(2,31) - 1;
    const max_negative = -Math.pow(2,31);
    
    // reverse and remove zero's
    chars.reverse();
    while(chars.length > 0  && chars[0] === 0) {
        chars.shift();
    }
    
    const result = parseInt(sign + chars.join(""));
    
    // return 0 if the result is out of bound
    if(result > max_positive || result < max_negative) {
        return 0;
    }
    
    return result;
};
```



##### Approach 2 - Pop and push digits

Time Complexity: O(log(x))

Space Complexity: O(1)

```js
/**
 * @param {number} x
 * @return {number}
 */
var reverse = function(x) {
    const sign = Math.sign(x);
    let reverse = 0;
    
    // limits for out of bound
    const max_positive = Math.pow(2,31) - 1;
    const max_negative = -Math.pow(2,31);
    
    while(x != 0) {
        // get the digit in unit's place
        const pop = Math.floor(x % 10);
        // remove last digit
        x = Math.floor(x/10);
        // add to reverse
        reverse = reverse * 10 + pop;
    }
    
    const result = reverse * sign;
    // if result is out of bound
    if(reverse > max_positive || reverse < max_negative) {
        return 0;
    }
    
    return reverse;
};
```

