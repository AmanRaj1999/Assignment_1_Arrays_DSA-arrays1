Q1.
💡 Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

**Example:**
Input: nums = [2,7,11,15], target = 9
Output0 [0,1]

**Explanation:** Because nums[0] + nums[1] == 9, we return [0, 1]

```javascript
function Sum(nums, target) {
  const mapnum = new Map();

  for (let i = 0; i < nums.length; i++) {
    const comp = target - nums[i];
    if (mapnum.has(comp)) {
      return [numMap.get(comp), i];
    }
    mapnum.set(nums[i], i);
  }

  return [];
}
const nums = [2, 7, 11, 15];
const target = 9;

const index = Sum(nums, target);
console.log(`Output: [${index[0]}, ${index[1]}]`);
```

Q2.

```javascript
function removeElement(nums, val) {
  let k = 0; // Number of elements not equal to val

  for (let i = 0; i < nums.length; i++) {
    if (nums[i] !== val) {
      nums[k] = nums[i];
      k++;
    }
  }

  return k;
}

const nums = [3, 2, 2, 3];
const val = 3;

const remain = removeElement(nums, val);
console.log(
  `Output: ${remain}, nums = [${nums.slice(0, remain).join(", ")}, _, _]`
);
```

Q3.

```javascript
function search(nums, target) {
  let left = 0;
  let right = nums.length - 1;

  while (left <= right) {
    const mid = Math.floor((left + right) / 2);

    if (nums[mid] === target) {
      return mid;
    } else if (nums[mid] < target) {
      left = mid + 1;
    } else {
      right = mid - 1;
    }
  }
  return left;
}

const nums = [1, 3, 5, 6];
const target = 5;

const index = search(nums, target);
console.log(`Output: ${index}`);
```

Q4.

```javascript
function plusOne(digits) {
  const n = digits.length;

  for (let i = n - 1; i >= 0; i--) {
    if (digits[i] < 9) {
      digits[i]++;
      return digits;
    } else {
      digits[i] = 0;
    }
  }

  digits.unshift(1);
  return digits;
}

const digits = [1, 2, 3];
const result = plusOne(digits);
console.log("Output:", result);
```

Q5.

```javascript
function merge(nums1, m, nums2, n) {
  let i = m - 1;
  let j = n - 1;
  let k = m + n - 1;

  while (i >= 0 && j >= 0) {
    if (nums1[i] > nums2[j]) {
      nums1[k] = nums1[i];
      i--;
    } else {
      nums1[k] = nums2[j];
      j--;
    }
    k--;
  }

  while (j >= 0) {
    nums1[k] = nums2[j];
    j--;
    k--;
  }
}

const nums1 = [1, 2, 3, 0, 0, 0];
const m = 3;
const nums2 = [2, 5, 6];
const n = 3;

merge(nums1, m, nums2, n);
console.log("Output:", nums1);
```

Q6.

```javascript
function containsDuplicate(nums) {
  let uniqueNums = new Set();

  for (let num of nums) {
    if (uniqueNums.has(num)) {
      return true;
    }

    uniqueNums.add(num);
  }

  return false;
}

let nums = [1, 2, 3, 1];
console.log(containsDuplicate(nums));
```

Q7.

```javascript
function moveZeros(nums) {
  let left = 0;
  for (let right = 0; right < nums.length; right++) {
    if (nums[right] !== 0) {
      [nums[left], nums[right]] = [nums[right], nums[left]];
      left++;
    }
  }
  return nums;
}

const nums = [0, 1, 0, 3, 12];
console.log(moveZeros(nums));
```

Q8.

```javascript
function findErrorNums(nums) {
  const n = nums.length;
  const count = {};

  let duplicate, missing;

  for (let i = 0; i < n; i++) {
    const num = nums[i];

    if (count[num]) {
      duplicate = num;
    } else {
      count[num] = 1;
    }
  }

  for (let i = 1; i <= n; i++) {
    if (!count[i]) {
      missing = i;
      break;
    }
  }

  return [duplicate, missing];
}

const nums = [1, 2, 2, 4];
console.log(findErrorNums(nums)); // Output: [2, 3]
```
