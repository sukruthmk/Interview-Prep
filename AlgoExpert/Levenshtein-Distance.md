# Levenshtein Distance

Given two words *word1* and *word2*, find the minimum number of operations required to convert *word1* to *word2*.

You have the following 3 operations permitted on a word:

1. Insert a character
2. Delete a character
3. Replace a character

**Example 1:**

```
Input: word1 = "horse", word2 = "ros"
Output: 3
Explanation: 
horse -> rorse (replace 'h' with 'r')
rorse -> rose (remove 'r')
rose -> ros (remove 'e')
```

**Example 2:**

```
Input: word1 = "intention", word2 = "execution"
Output: 5
Explanation: 
intention -> inention (remove 't')
inention -> enention (replace 'i' with 'e')
enention -> exention (replace 'n' with 'x')
exention -> exection (replace 'n' with 'c')
exection -> execution (insert 'u')
```

### Leetcode

https://leetcode.com/problems/edit-distance/

### Optimal Solution

```js
/**
 * @param {string} word1
 * @param {string} word2
 * @return {number}
 */
var minDistance = function(word1, word2) {
    // create dp array
    const dp = new Array(word1.length + 1).fill(0).map((value) => new Array(word2.length + 1).fill(0));
    
    // generate first row and first column for dp
    for(let i=0; i<dp[0].length; i++) {
        dp[0][i] = i;
    }
    for(let i=0; i<dp.length; i++) {
        dp[i][0] = i;
    }
    
    // iterate over all words
    for(let i=1; i<=word1.length; i++) {
        for(let j=1; j<=word2.length; j++) {
            // no effort required to edit/delete if the character is same
            if(word1[i-1] === word2[j-1]) {
                dp[i][j] = dp[i-1][j-1];
            } else {
                // get the min of three positions and add 1 
                // since we need to put some effort in either deleting or editing the current value
                dp[i][j] = Math.min(dp[i-1][j-1], dp[i-1][j], dp[i][j-1]) + 1;
            }
        }
    }
    
    return dp[word1.length][word2.length];
};
```

### Explanation

https://www.youtube.com/watch?v=We3YDTzNXEk