### 125. Valid Palindrome

[Valid Palindrome](https://leetcode.com/problems/valid-palindrome)

- Solution:

```javascript
function isPalindrome(s) {
    const noSpecialChars = s.replace(/[^a-zA-Z0-9]/g, "").toLowerCase();
    let forwardIndex = 0;
    let backwardIndex = noSpecialChars.length - 1;

    while (forwardIndex <= backwardIndex) {
        if (noSpecialChars[forwardIndex] !== noSpecialChars[backwardIndex]) {
            return false;
        } else {
            forwardIndex++;
            backwardIndex--;
        }
    }
    return true;
}
```
