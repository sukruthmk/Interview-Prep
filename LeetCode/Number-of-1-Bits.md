# Number of 1 Bits

Write a function that takes an unsigned integer and return the number of '1' bits it has (also known as the [Hamming weight](http://en.wikipedia.org/wiki/Hamming_weight)).

 

**Example 1:**

```
Input: 00000000000000000000000000001011
Output: 3
Explanation: The input binary string 00000000000000000000000000001011 has a total of three '1' bits.
```

**Example 2:**

```
Input: 00000000000000000000000010000000
Output: 1
Explanation: The input binary string 00000000000000000000000010000000 has a total of one '1' bit.
```

**Example 3:**

```
Input: 11111111111111111111111111111101
Output: 31
Explanation: The input binary string 11111111111111111111111111111101 has a total of thirty one '1' bits.
```

 

**Note:**

- Note that in some languages such as Java, there is no unsigned integer type. In this case, the input will be given as signed integer type and should not affect your implementation, as the internal binary representation of the integer is the same whether it is signed or unsigned.
- In Java, the compiler represents the signed integers using [2's complement notation](https://en.wikipedia.org/wiki/Two's_complement). Therefore, in **Example 3** above the input represents the signed integer `-3`.

 

**Follow up**:

If this function is called many times, how would you optimize it?



### Leetcode

https://leetcode.com/problems/number-of-1-bits/



### Optimal Solution

##### Approach 1 - Convert to binary string and perform the count

Time Complexity: 

Space Complexity: 

```js
/**
 * @param {number} n - a positive integer
 * @return {number}
 */
var hammingWeight = function(n) {
  const binaryNumberString = n.toString(2);
  let count = 0;
  
  for(const char of binaryNumberString) {
    if(char == "1") count++;
  }
  
  return count;
};
```



##### Approach 2 - Loop and Flip

Time Complexity: O(1)

Space Complexity: O(1)

```js
/**
 * @param {number} n - a positive integer
 * @return {number}
 */
var hammingWeight = function(n) {
  let bits = 0;
  let mask = 1;
  
  for(let i=0; i<32; i++) {
    if((n & mask) != 0) {
      bits++;
    }
    mask <<=1;
  }
  return bits;
};
```



##### Approach 3 - Bit Manipulation Trick

Time Complexity: O(1)

Space Complexity: O(1)

```js
/**
 * @param {number} n - a positive integer
 * @return {number}
 */
var hammingWeight = function(n) {
  let count = 0;
  while(n != 0) {
    count++;
    n &= (n - 1);
  }
  return count;
};
```

