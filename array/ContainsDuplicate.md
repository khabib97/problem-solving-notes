# Contains Duplicate
`Easy`

### Problem
Given an integer array nums, return true if any value appears at least twice in the array, and return false if every element is distinct.
```
Example 1:

Input: nums = [1,2,3,1]
Output: true

Example 2:

Input: nums = [1,2,3,4]
Output: false
```

### Solution

Time O(nlogn) | Space O(1)
```
class ContainsDuplicate {
    public boolean containsDuplicate(int[] nums) {
        if(nums.length == 0) return false;
        
        Arrays.sort(nums);
        for(int i = 0; i < nums.length - 1; i++){
            if(nums[i] == nums[i+1]){
                return true;
            }
        }
        return false;
    }
}
```


