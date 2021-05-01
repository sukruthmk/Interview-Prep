# Reverse Vowels of a String

Given a string `s`, reverse only all the vowels in the string and return it.

The vowels are `'a'`, `'e'`, `'i'`, `'o'`, and `'u'`, and they can appear in both cases.

 

**Example 1:**

```
Input: s = "hello"
Output: "holle"
```

**Example 2:**

```
Input: s = "leetcode"
Output: "leotcede"
```

 

**Constraints:**

- `1 <= s.length <= 3 * 105`
- `s` consist of **printable ASCII** characters.



### Leetcode

https://leetcode.com/problems/reverse-vowels-of-a-string/



### Optimal Solution

Time Complexity: 

Space Complexity: 

```js
/**
 * @param {string} s
 * @return {string}
 */
var reverseVowels = function (s) {
  const vowels = {
    a: "a",
    e: "e",
    i: "i",
    o: "o",
    u: "u",
    A: 'A',
    E: "E",
    I: "I",
    O: "O",
    U: "U"
  };
  
  const pos = []
  const stack = []
  const stringArr = [...s];
  
  // 1. first get the positions of vowels and also the vowels in the same order of iteration
  for (let i = 0; i < stringArr.length; i++) {
    const char = stringArr[i];
    if (vowels[char]) {
      pos.push(i)
      stack.push(char)
    }
  }
  
  // 2. reverse the order of vowels
  stack.reverse()
  
  // 3. substitute in the same positions
  for(let i=0; i<stack.length; i++) {
    stringArr[pos[i]] = stack[i];
  }
  
  return stringArr.join("");
};

const swap = (i, j, arr) => {
  const temp = arr[i];
  arr[i] = arr[j];
  arr[j] = temp;
};
```
