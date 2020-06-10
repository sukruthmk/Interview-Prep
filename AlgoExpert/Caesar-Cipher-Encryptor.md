# Caesar Cipher Encryptor

Given a non-empty string of lowercase letters and a non-negative integer value representing a key, write a function that returns a new string obtained by shifting every letter in the input string by k positions in the alphabet, where k is the key. Note that letters should "wrap" around the alphabet; in other words, the letter "z" shifted by 1 returns the letter "a".

Sample input:"xyz", 2 Sample output:"zab"

### Reference

* https://www.geeksforgeeks.org/caesar-cipher-in-cryptography/
* https://github.com/partho-maple/coding-interview-gym/blob/master/algoexpert.io/questions/Caesar_Cipher_Encryptor.md
* https://www.freecodecamp.org/forum/t/freecodecamp-challenge-guide-caesars-cipher/16003



### Optimal Solution

#### Solution 1

https://jsfiddle.net/sukruthmk/z3tdu2vw/2/

```js
function cipher(str, k) {
  const alphabet = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
  return str
    .split('')
    .map(char => {
      const pos = alphabet.indexOf(char);
      return pos >= 0 ? alphabet[(pos + k) % 26] : char;
    })
    .join('');
}
```

#### Solution 2

https://jsfiddle.net/sukruthmk/bso6r7ap/19/

```js
const cipher = (string, k) => {
  let output = "";
  for (let i = 0; i < string.length; i++) {
    const code = string.charCodeAt(i);
    output += codeToChar(code, k);
  }
  return output;
}

const codeToChar = (code, k) => {
  // Checks if character lies between A-Z
  if (code < 65 || code > 90) {
    return String.fromCharCode(code); // Return un-converted character
  }
  //N = ASCII 78, if the character code is less than 78, shift forward 13 places
  else if (code + k < 91) {
    return String.fromCharCode(code + k);
  }
  // Otherwise shift the character 13 places backward
  return String.fromCharCode(code - k);
}
```

