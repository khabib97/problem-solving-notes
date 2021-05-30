# Move Zeroes

`Easy`
### Problem
Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.

Note that you must do this in-place without making a copy of the array.
```
Example 1:

Input: nums = [0,1,0,3,12]
Output: [1,3,12,0,0]
Example 2:

Input: nums = [0]
Output: [0]
``` 

### Constraints:

1 <= nums.length <= 104

-231 <= nums[i] <= 231 - 1
 

**Follow up**: Could you minimize the total number of operations done?

### Solution 1

Time O(n) | Space O(1)
```
class MoveZeros{
    public void moveZeroes(int[] nums) {

        int pointer = 0;
        
        for(int i=0;i<nums.length;i++){
            if(nums[i] != 0){
                nums[pointer] = nums[i];
                pointer++;
            }
        }
        
        for(int i = pointer; i< nums.length; i++){
            nums[i] = 0;
        }
    }
}
```
### Solution 2

Time O(n\*n) | Space O(1)
```
class MoveZeros{
    public void moveZeroes(int[] nums) {

        for(int i=0; i<nums.length-1; i++){
            if(nums[i] == 0){
                int j = i+1;
                while(j < nums.length-1  && nums[j] == 0){
                    j++;
                }
                
                nums[i] = nums[j];
                nums[j] = 0;
            }         
        }
    }
}
```
