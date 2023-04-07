
### 1. Problem Contains duplicate

[Contains-Duplicate](leetcode.com/problems/contains-duplicate)
- Solution:

```javascript
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var containsDuplicate = function(nums) {
for (let i = 0; i < nums.length; i++) {
    for (let j = i + 1; j < nums.length; j++) {
      if (nums[i] === nums[j]) {
        return true;
      }
    }
  }
  return false;
};
```

### 2. Valid Anagram

[Anagram](https://leetcode.com/problems/valid-anagram)

- Time complexity: 98ms
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: 43.1 Mb
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

- Solution:

```javascript
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var isAnagram = function(s, t) {
        if (s.length !== t.length) {
        return false;
    }
    
    const uniqueS = [...s].sort();
    const uniqueT = [...t].sort();
    
		return uniqueS.every((element, index) => uniqueT[index] === element)
};
```

### 3. Two sum
[Two Sum](https://leetcode.com/problems/two-sum)

# Code
```
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function(nums, target) {
   for (let i = 0; i < nums.length; i++) {
    const valueStartIndex = nums[i];
    const complement = target - nums[i];
    const endIndex = nums.indexOf(complement, i + 1);
    if (endIndex > i) {
      return [i, endIndex];
    }
  }
};
```
