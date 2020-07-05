# Basic Calculator

Implement a basic calculator to evaluate a simple expression string.

The expression string may contain open `(` and closing parentheses `)`, the plus `+` or minus sign `-`, **non-negative**integers and empty spaces ``.

**Example 1:**

```
Input: "1 + 1"
Output: 2
```

**Example 2:**

```
Input: " 2-1 + 2 "
Output: 3
```

**Example 3:**

```
Input: "(1+(4+5+2)-3)+(6+8)"
Output: 23
```

**Note:**

- You may assume that the given expression is always valid.
- **Do not** use the `eval` built-in library function.



### Leetcode

https://leetcode.com/problems/basic-calculator/



### Optimal Solution

Time Complexity: *O(n)*

Space Complexity: *O(n)*

```js
/**
 * @param {string} s
 * @return {number}
 */
var calculate = function(s) {
    const stack = [];
    let sign = 1;
    let output = 0;
    let i = 0;
    
    while(i < s.length) {
        const char = s[i];
        
        // since in arithmetic operations left side number takes more precedence
        // we keep track of previous sign and ongoing sum
        if(isDigit(char)) {
            // extract the number and add it to the output
            let num = "";
            while(i < s.length && isDigit(s[i])) {
                num = num + s[i];
                i++;
            }
            output = output + parseInt(num) * sign;
            continue;
        } else if(char === "+") {
            sign = 1;
        } else if(char === "-") {
            sign = -1;
        } else if (char === "(") {
            stack.push(output);
            stack.push(sign);
            output = 0;
            sign = 1;
        } else if (char === ")") {
            const prevSign = stack.pop();
            const prevNum = stack.pop();
            output = prevNum + output*prevSign;
        }
        
        i++;
    }
    
    return output;
};

// helper function to check if the char is a digit or not
const isDigit = (char) => {
    return char >= '0' && char <= '9'
}
```



### Explanation

https://www.youtube.com/watch?v=081AqOuasw0