# Fraction to Recurring Decimal

Given two integers representing the numerator and denominator of a fraction, return the fraction in string format.

If the fractional part is repeating, enclose the repeating part in parentheses.

If multiple answers are possible, just return any of them.

**Example 1:**

```
Input: numerator = 1, denominator = 2
Output: "0.5"
```

**Example 2:**

```
Input: numerator = 2, denominator = 1
Output: "2"
```

**Example 3:**

```
Input: numerator = 2, denominator = 3
Output: "0.(6)"
```



### Leetcode

https://leetcode.com/problems/fraction-to-recurring-decimal/



### Optimal Solution

Time Complexity: 

Space Complexity: 

```js
/**
 * @param {number} numerator
 * @param {number} denominator
 * @return {string}
 */
var fractionToDecimal = function(numerator, denominator) {
  let result = "";
  
  // 1. Append "-" sign first if the result is negative number
  if((numerator < 0 && denominator > 0) || (denominator < 0 && numerator > 0)) {
    result += "-";
  }
  
  // 2. remove signs from numerator and denominator
  const dividend = Math.abs(numerator);
  const divisor = Math.abs(denominator);
  let remainder = dividend % divisor;
  // 3. Append the front non fractional part to result string
  result += Math.floor(dividend / divisor);
  
  // 4. return result if there is no remainder i.e no fraction
  if(remainder === 0) {
    return result;
  }
  
  // 5. if remainder is positive that means there is a fractional part in the result
  //    so append "."
  result += ".";
  
  // 6. create a hashMap to store the remainder in fraction along with the string position
  //    i.e if same remainder is repeating that means we have repeating divided value 
  //    and we need to add brackets for it.
  const map = new Map();
  
  // 7. iterate over the remainder part
  while(remainder != 0) {
    if(map.has(remainder)) {
      // append brackets at the repeating position
      result = result.substring(0, map.get(remainder)) + "(" + result.substring(map.get(remainder)) + ")";
      break;
    }
    
    map.set(remainder, result.length);    
    remainder *= 10;
    result += Math.floor(remainder / divisor);
    remainder = remainder % divisor;
  }
  
  return result;
};
```



### Explanation

https://www.youtube.com/watch?v=a-62yK1S1O4