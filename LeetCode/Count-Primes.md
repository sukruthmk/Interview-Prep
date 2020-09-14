# Count Primes

Count the number of prime numbers less than a non-negative number, ***n\***.

**Example:**

```
Input: 10
Output: 4
Explanation: There are 4 prime numbers less than 10, they are 2, 3, 5, 7.
```



### Leetcode

https://leetcode.com/problems/count-primes/



### Optimal Solution

##### Approach 1 - Using loops

Time Complexity: 

Space Complexity: 

```js
/**
 * @param {number} n
 * @return {number}
 */
var countPrimes = function(n) {
  let count = 0;
  for(let i=n-1; i>=2; i--) {
    if(isPrime(i)) {
      count++;
    }
  }
  return count;
};

const isPrime = (num) => {
  for(let i=2; i*i <= num; i++) {
    if(num % i === 0) {
      return false;
    }
  }
  return true;
}
```





##### Approach 2 - Sieve of Eratosthenes

Time Complexity: 

Space Complexity: 

```js
/**
 * @param {number} n
 * @return {number}
 */
var countPrimes = function(n) {
  const primes = new Array(n+1).fill(true);
  
  for(let i=2; i*i<n; i++) {
    if(!primes[i]) continue;
    for(let j=i*i; j<n; j=j+i) {
      primes[j] = false;
    }
  }
  
  let count = 0;
  for(let i=2; i<n; i++) {
    if(primes[i]) count++;
  }
  
  return count;
};
```
