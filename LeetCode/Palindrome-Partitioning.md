# Palindrome Partitioning

Given a string *s*, partition *s* such that every substring of the partition is a palindrome.

Return all possible palindrome partitioning of *s*.

**Example:**

```
Input: "aab"
Output:
[
  ["aa","b"],
  ["a","a","b"]
]
```



### Leetcode

https://leetcode.com/problems/palindrome-partitioning/



### Optimal Solution

Time Complexity: O(n^2)

Space Complexity: O(n)

```js
/**
 * @param {string} s
 * @return {string[][]}
 */
var partition = function(s) {
    const result = [];
    generatePalindromes(s, 0, [], result);
    return result;
};

const generatePalindromes = (s, index, currPalindromes, result) => {
    // push to result if we have reached the end
    if(index === s.length) {
        result.push([...currPalindromes]);
    }
    for(let i=index; i<s.length; i++) {
        // validate each substring
        const subString = s.substring(index, i+1);
        if(isPalindrome(subString)) {
            currPalindromes.push(subString);
            generatePalindromes(s, i+1, currPalindromes, result);
            currPalindromes.pop();
        }
    }
}

// helper function to validate if the string is a palindrome or not
const isPalindrome = (s) => {
    let i = 0;
    let j = s.length - 1;
    
    while (i < j) {
        if(s[i] !== s[j]) {
            return false;
        }
        i++;
        j--;
    }
    
    return true;
}
```



### Explanation

https://www.youtube.com/watch?v=4ykBXGbonlA

