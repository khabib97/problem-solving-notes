# Remove Duplicates from Sorted Array

Given a sorted array nums, remove the duplicates in-place such that each element appears only once and returns the new length.

Do not allocate extra space for another array, you must do this by modifying the input array **in-place with O(1) extra memory**.

#### Clarification:

Confused why the returned value is an integer but your answer is an array?

Note that the input array is passed in by reference, which means a modification to the input array will be known to the caller as well.

#### Example:
```
Input: nums = [0,0,1,1,1,2,2,3,3,4]
Output: 5, nums = [0,1,2,3,4]
Explanation: Your function should return length = 5, with the first five elements of nums 
being modified to 0, 1, 2, 3, and 4 respectively. It doesn't matter what values are set beyond the returned length.
```

## Solution

### 1. Using max value concept
Fastes solution without gc, with gc it will comsume less memory but take some extra time 
```
   //Time = O(n)
   //Space = O(1)
   public int removeDuplicates(int[] nums) {
      int max = Integer.MIN_VALUE;
    	
    	int j = 0;
    	for(int i = 0; i < nums.length; i++) {
    		if(nums[i] > max) {
    			nums[j] = nums[i];
    			j++;
    			max = nums[i];
    		}
    	}
        //Garbale collection, optimized memory.
    	//System.gc();
    	return j;
    }
```

### 2. Check next concept, minimal memory consume 

```
    //Time = O(n)
    //Space = O(1)
    public int removeDuplicates(int[] nums) {
        int n = 1;
        for(int i=0; i<nums.length-1;i++){
            if(nums[i] != nums[i+1]){
                nums[n] = nums[i+1];
                n++;
            }
        }
        System.gc();
    	
    	return n;
    }
```
### 3. Poor approach
```
   //Time = O(n^2)
   //Space = O(1)
   public int removeDuplicates(int[] nums) {
      int totalDuplicate = 0;
    	int outerPointer = 0;
    	while( outerPointer < (nums.length - totalDuplicate)) {
    		
    		int innerPointer = outerPointer;
    		int duplicate = 0;
    		if(nums[innerPointer] == nums[nums.length-1]) break;
    		//marking
    		while(nums[innerPointer] == nums[innerPointer+1]) {
    			duplicate++;
    			innerPointer++;
    		}
    		
    		totalDuplicate += duplicate;
    		//erasing
    		innerPointer = outerPointer+1;
    		int shiftFactor = duplicate;
    		while(shiftFactor > 0 && innerPointer < (nums.length - totalDuplicate)) {
    			nums[innerPointer] = nums[innerPointer+duplicate];
    			innerPointer++;
    		}
    		
    		outerPointer++;
    	}
        
    	return outerPointer + 1;
```

