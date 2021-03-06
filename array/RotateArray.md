# Rotate Array

`Medium`

### Problem:
Given an array, rotate the array to the right by k steps, where k is non-negative.

```
Example 1:

Input: nums = [1,2,3,4,5,6,7], k = 3
Output: [5,6,7,1,2,3,4]
Explanation:
rotate 1 steps to the right: [7,1,2,3,4,5,6]
rotate 2 steps to the right: [6,7,1,2,3,4,5]
rotate 3 steps to the right: [5,6,7,1,2,3,4]
Example 2:

Input: nums = [-1,-100,3,99], k = 2
Output: [3,99,-1,-100]
Explanation: 
rotate 1 steps to the right: [99,-1,-100,3]
rotate 2 steps to the right: [3,99,-1,-100]
```
### Solution 1:

```
supporse, k = 2,
- Data: 1,2,3,4,5,6,7
- Full Reverse: 7,6,5,4,3,2,1
- Reverse 0 to k-1: 6,7 ...
- Reverse k to arr.length-1 : 1,2,3,4,5
- Rotated arr = 6,7,1,2,3,4,5

// Time O(n), Space 0(1)
private void rotateArray(int[] nums, int k) {
	
	k = k % nums.length;
	
	reverse(nums, 0, nums.length-1);
	reverse(nums, 0, k-1);
	reverse(nums, k, nums.length -1);
	
}

private void reverse(int[] nums, int start, int end) {
	int temp = 0;
	while(start < end) {
		temp = nums[start];
		nums[start] = nums[end];
		nums[end] = temp;
		start++;
		end--;
	}	
}
```
### Solution 2:
```
// Time O(n), Space O(n)
    public void rotate(int[] nums, int k) {
        k = k % nums.length;
        int[] _nums = nums.clone();
        int j = nums.length - k;
        for(int i = 0; i < nums.length; i++){
            if(j >= nums.length){
                j = 0;
            }
            nums[i] = _nums[j++];
        }
        
        nums = _nums;
    }

```
