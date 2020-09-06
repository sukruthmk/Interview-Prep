# Substring with Concatenation of All Words

You are given a string `s` and an array of strings `words` of **the same length**. Return all starting indices of substring(s) in `s` that is a concatenation of each word in `words` **exactly once**, **in any order**, and **without any intervening characters**.

You can return the answer in **any order**.

 

**Example 1:**

```
Input: s = "barfoothefoobarman", words = ["foo","bar"]
Output: [0,9]
Explanation: Substrings starting at index 0 and 9 are "barfoo" and "foobar" respectively.
The output order does not matter, returning [9,0] is fine too.
```

**Example 2:**

```
Input: s = "wordgoodgoodgoodbestword", words = ["word","good","best","word"]
Output: []
```

**Example 3:**

```
Input: s = "barfoofoobarthefoobarman", words = ["bar","foo","the"]
Output: [6,9,12]
```

 

**Constraints:**

- `1 <= s.length <= 104`
- `s` consists of lower-case English letters.
- `1 <= words.length <= 5000`
- `1 <= words[i].length <= 30`
- `words[i]` consists of lower-case English letters.



### Leetcode

https://leetcode.com/problems/substring-with-concatenation-of-all-words/



### Optimal Solution

Time Complexity: 

Space Complexity: 

```js
/**
 * @param {string} s
 * @param {string[]} words
 * @return {number[]}
 */
var findSubstring = function(s, words) {
  const wordLength = words[0].length;
  const noOfWords = words.length;
  const totalConcatenatedLength = wordLength*noOfWords;
  const result = [];
  const wordMap = new Map();
  
  // create a hasMap so that we can compare the frequecy times word is repeated
  for(const word of words) {
    mapInsert(wordMap, word);
  }

  for(let i=0; i <= s.length - totalConcatenatedLength; i++) {
    const substring = s.substring(i, i+totalConcatenatedLength);
    if(validateSubstring(substring, wordMap, wordLength)) {
      result.push(i);
    }
  }
  
  return result;
};

const validateSubstring = (substring, wordMap, wordLength) => {
  let i = 0;
  const currWords = new Map();
  
  while(i < substring.length) {
    const word = substring.substring(i, i+wordLength);
    
    // invalid cases
    // if the word does not exisits in our wordMap
    if(!wordMap.get(word)) return false;
    
    mapInsert(currWords, word);
    
    // if the word exists but count is greater than frequecy of words in wordMap
    if(currWords.get(word) > wordMap.get(word)) return false;
    
    i = i + wordLength;
  }
  
  return true;
}

// helper function to insert a key into map with a counter to increase the frequency
const mapInsert = (map, key) => {
  const count = map.get(key) != null ? map.get(key) + 1 : 1;
  map.set(key, count);
} 
```



### Explanation

https://www.youtube.com/watch?v=Bbu4Qjzf7A0