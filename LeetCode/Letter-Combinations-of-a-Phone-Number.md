# Letter Combinations of a Phone Number

Given a string containing digits from `2-9` inclusive, return all possible letter combinations that the number could represent.

A mapping of digit to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

![img](https://upload.wikimedia.org/wikipedia/commons/thumb/7/73/Telephone-keypad2.svg/200px-Telephone-keypad2.svg.png)

**Example:**

```
Input: "23"
Output: ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].
```

**Note:**

Although the above answer is in lexicographical order, your answer could be in any order you want.



### Leetcode

https://leetcode.com/problems/letter-combinations-of-a-phone-number/



### Optimal Solution

Time Complexity: 

Space Complexity: 

```js
/**
 * @param {string} digits
 * @return {string[]}
 */
var letterCombinations = function(digits) {
  if(digits == null || digits.length === 0) return [];
  
  const result = [];
  const map = [
    "",
    "",
    "abc",
    "def",
    "ghi",
    "jkl",
    "mno",
    "pqrs",
    "tuv",
    "wxyz"
  ];
  
  generateCombinations(digits, map, 0, "", result);
  
  return result;
};

const generateCombinations = (digits, map, index, combinationString, result) => {
  // if we have generated a combination of same as input digits length
  // then we need to add it to the result
  if(index === digits.length) {
    result.push(combinationString);
    return;
  }
  
  // get the letters mapped to the current digit
  const digit = parseInt(digits.charAt(index));
  const letters = map[digit];
  
  for(const letter of letters) {
    generateCombinations(digits, map, index + 1, combinationString + letter, result);
  }
}
```



### Explanation

https://www.youtube.com/watch?v=21OuwqIC56E