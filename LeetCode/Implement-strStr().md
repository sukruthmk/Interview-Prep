# Implement strStr()

Implement [strStr()](http://www.cplusplus.com/reference/cstring/strstr/).

Return the index of the first occurrence of needle in haystack, or **-1** if needle is not part of haystack.

**Example 1:**

```
Input: haystack = "hello", needle = "ll"
Output: 2
```

**Example 2:**

```
Input: haystack = "aaaaa", needle = "bba"
Output: -1
```

**Clarification:**

What should we return when `needle` is an empty string? This is a great question to ask during an interview.

For the purpose of this problem, we will return 0 when `needle` is an empty string. This is consistent to C's [strstr()](http://www.cplusplus.com/reference/cstring/strstr/)and Java's [indexOf()](https://docs.oracle.com/javase/7/docs/api/java/lang/String.html#indexOf(java.lang.String)).

 

**Constraints:**

- `haystack` and `needle` consist only of lowercase English characters.



### Leetcode

https://leetcode.com/problems/implement-strstr/



### Optimal Solution

Time Complexity: O(n*m)

Space Complexity: O(1)

```js
/**
 * @param {string} haystack
 * @param {string} needle
 * @return {number}
 */
var strStr = function(haystack, needle) {
    const m = haystack.length;
    const n = needle.length;
    
    // special case if needle is empty it should return 0
    if (needle == null || needle == "") return 0;
    // we can't search if needle is bigger than haystack
    if (m < n) return -1;
    
    // optimization search only in the m-n part of the hystack
    for (let i = 0; i <= m - n; i++) {
        let j = 0;
        // search needle in haystack
        while (j < n) {
            if (haystack[i + j] != needle[j]) break;
            j++;
        }
        // if all characters in needle are match return the ith position
        if (j === n) return i;
    }

    return -1;
};
```



### Explanation

https://www.youtube.com/watch?v=TsxFvVy_5m0