
# Caesars Cipher

One of the simplest and most widely known <dfn>ciphers</dfn> is a <dfn>Caesar cipher</dfn>, also known as a <dfn>shift cipher</dfn>. In a shift cipher the meanings of the letters are shifted by some set amount.

A common modern use is the [ROT13](https://en.wikipedia.org/wiki/ROT13) cipher, where the values of the letters are shifted by 13 places. Thus 'A' ↔ 'N', 'B' ↔ 'O' and so on.

Write a function which takes a [ROT13](https://en.wikipedia.org/wiki/ROT13) encoded string as input and returns a decoded string.

All letters will be uppercase. Do not transform any non-alphabetic character (i.e. spaces, punctuation), but do pass them on.

Submit a pull request to the main branch with your solution. Do not modify the tests. Once you have created a PR with passing tests, then you have successfully completed the exercise.

```
module.exports =  function rot13(str) {
  //Write your code here

  // ABCDEFGHIJKLMNOPQRSTUVWXYZ
  str = str.split('');
  const temp = [];
  let alpha = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
  alpha = alpha.split('');

  for (char of str){
    if (alpha.includes(char)){
      const index = alpha.indexOf(char) + 1;
      const distance = index + 13;
      if (distance > 26){
	const leftover = 13 - (26 - index);
	temp.push(alpha[leftover - 1]);
      } else {
	temp.push(alpha[(index + 13) - 1]);
      }
    } else {
      temp.push(char);
    }
  }
  return temp.join('');
}
```
### Test
```
const rot13 = require('./caesars-cipher')
const assert = require('assert')

describe('Tests', function () {
  it('rot13("SERR PBQR PNZC") should decode to FREE CODE CAMP', function () {
    assert(rot13('SERR PBQR PNZC') === 'FREE CODE CAMP')
  })
  it('rot13("SERR CVMMN!") should decode to FREE PIZZA!', function () {
    assert(rot13('SERR CVMMN!') === 'FREE PIZZA!')
  })
  it('rot13("SERR YBIR?") should decode to FREE LOVE?', function () {
    assert(rot13('SERR YBIR?') === 'FREE LOVE?')
  })
  it('rot13("GUR DHVPX OEBJA SBK WHZCF BIRE GUR YNML QBT.") should decode to THE QUICK BROWN FOX JUMPS OVER THE LAZY DOG.', function () {
    assert(
      rot13('GUR DHVPX OEBJA SBK WHZCF BIRE GUR YNML QBT.') ===
	'THE QUICK BROWN FOX JUMPS OVER THE LAZY DOG.'
    )
  })
})
```

