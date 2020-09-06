# Minimum Window Substring

Given a string S and a string T, find the minimum window in S which will contain all the characters in T in complexity O(n).

**Example:**

```
Input: S = "ADOBECODEBANC", T = "ABC"
Output: "BANC"
```

**Note:**

- If there is no such window in S that covers all characters in T, return the empty string `""`.
- If there is such window, you are guaranteed that there will always be only one unique minimum window in S.



### Leetcode

https://leetcode.com/problems/minimum-window-substring/



### Optimal Solution

Time Complexity: 

Space Complexity: 

```js
/**
 * @param {string} s
 * @param {string} t
 * @return {string}
 */
var minWindow = function(s, t) {
  const charMap = new Map();
  for(const char of t) {
    mapIncrement(charMap, char);
  }
  
  let min = "";
  let left = 0;
  let right = -1;
  let count = charMap.size;
  
  while(right <= s.length) {
    if(count === 0) {
      const char = s[left];
      
      // if the left char exists in the map then we need to increment the counter
      if(charMap.has(char)) mapIncrement(charMap, char);
      
      // this is to avoid negative values
      // because for case like "BBBA...", count for B could be negative
      if(charMap.get(char) > 0) count++;
      
      const string = s.substring(left, right);
      if(min == "") {
        min = string;
      } else if(string.length < min.length) {
        min = string;
      }
      left++;
    } else {
      const char = s[right];
      // if character exists in out map then decrement the frequency count
      if(charMap.has(char)) {
        charMap.set(char, charMap.get(char) - 1);
      }
      
      // decrement the count once we have found all the repition of character 
      // i.e if t has AA in it then we need to find A twice
      if(charMap.get(char) === 0) {
        count--;
      }
      
      right++;
    }
  }
  
  return min;
};

const mapIncrement = (map, key) => {
  const count = map.get(key) ? map.get(key) + 1 : 1;
  map.set(key, count);
}
```



### Explanation

https://leetcode.com/problems/minimum-window-substring/discuss/411388/JavaScript-Solution-w-Detailed-Comments