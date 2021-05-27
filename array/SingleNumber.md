# Single Number

`Medium`

### Problem

Given a non-empty array of integers nums, every element appears twice except for one. Find that single one.

`You must implement a solution with a linear runtime complexity and use only constant extra space.``

```
Example 1:

Input: nums = [2,2,1]
Output: 1
Example 2:

Input: nums = [4,1,2,1,2]
Output: 4
```

### Solution 1

Not good solution.
Time O(nlogn) | Space(1)
```java
class SingleNumber {
    public int singleNumber(int[] nums) {
        Arrays.sort(nums);
        int single = nums[0];
        for(int i=0;i<nums.length;){
            
            if( (i+1) < nums.length && nums[i] == nums[i+1]){
                i += 2;
                continue;  
            }
            single = nums[i];
            break;
        }
        return single;
    }
}  
```

### Solution 2
Time O(n) | Space(1)
Concept: 
1. If we take XOR of zero and some bit, it will return that bit

- a⊕0=a

2. If we take XOR of two same bits, it will return 0

- a⊕a=0

3. a⊕b⊕a=(a⊕a)⊕b=0⊕b=b

So we can XOR all bits together to find the unique number.
```java
class SingleNumber {
  public int singleNumber(int[] nums) {
    int single = 0;
    for (int i : nums) {
      single = single ˆ i;
    }
    return a;
  }
}
```
