# Evaluate Reverse Polish Notation

Evaluate the value of an arithmetic expression in [Reverse Polish Notation](http://en.wikipedia.org/wiki/Reverse_Polish_notation).

Valid operators are `+`, `-`, `*`, `/`. Each operand may be an integer or another expression.

**Note:**

- Division between two integers should truncate toward zero.
- The given RPN expression is always valid. That means the expression would always evaluate to a result and there won't be any divide by zero operation.

**Example 1:**

```
Input: ["2", "1", "+", "3", "*"]
Output: 9
Explanation: ((2 + 1) * 3) = 9
```

**Example 2:**

```
Input: ["4", "13", "5", "/", "+"]
Output: 6
Explanation: (4 + (13 / 5)) = 6
```

**Example 3:**

```
Input: ["10", "6", "9", "3", "+", "-11", "*", "/", "*", "17", "+", "5", "+"]
Output: 22
Explanation: 
  ((10 * (6 / ((9 + 3) * -11))) + 17) + 5
= ((10 * (6 / (12 * -11))) + 17) + 5
= ((10 * (6 / -132)) + 17) + 5
= ((10 * 0) + 17) + 5
= (0 + 17) + 5
= 17 + 5
= 22
```



### Leetcode

https://leetcode.com/problems/evaluate-reverse-polish-notation/



### Optimal Solution

Time Complexity: O(n)

Space Complexity: O(n)

```js
/**
 * @param {string[]} tokens
 * @return {number}
 */
var evalRPN = function(tokens) {
  const stack = [];
  
  for(const token of tokens) {
    if(!isOperator(token)) {
      stack.push(token);
    } else {
      const operand2 = parseInt(stack.pop());
      const operand1 = parseInt(stack.pop());
      const result = operate(operand1, operand2, token);
      stack.push(result);
    }
  }
  
  return stack[0];
};

// helper function to check if token is an operator
const isOperator = (token) => {
  const operators = ["+","-","*","/"];
  return operators.includes(token);
}

const operate = (a, b, operator) => {
  switch(operator) {
    case "+": return a+b;
    case "-": return a-b;
    case "*": return a*b;
    case "/": return a/b >= 0 ? Math.floor(a/b) : Math.ceil(a/b);
  }
  // this should not reach in any case
  return 0;
}
```



### Explanation

https://www.youtube.com/watch?v=qN8LPIcY6K4&app=desktop