# Intersection of Two Arrays II

`Easy`

[Problem Link](https://leetcode.com/explore/interview/card/top-interview-questions-easy/92/array/674/)

### Problem

Given two integer arrays nums1 and nums2, return an array of their intersection. 
Each element in the result must appear as many times as it shows in both arrays and you may return the result in any order.
```
Example 1:

Input: nums1 = [1,2,2,1], nums2 = [2,2]
Output: [2,2]
Example 2:

Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
Output: [4,9]
Explanation: [9,4] is also accepted.
```

#### Constraints:

1 <= nums1.length, nums2.length <= 1000

0 <= nums1[i], nums2[i] <= 1000

### Solution

Time O(n) | Space O(n)

```
class IntersectTwoArray {
    public int[] intersect(int[] nums1, int[] nums2) {
        
       Map<Integer, Integer> countMap = new HashMap<>(); 
        
       for(int i = 0 ; i < nums2.length ; i++){
           if(countMap.containsKey(nums2[i])){
               int count = countMap.get(nums2[i]);
               countMap.put(nums2[i],++count);
           }else{
               countMap.put(nums2[i], 1);
           }
       }
        
       List<Integer> intersectedList = new ArrayList<>(); 
        
       for(int i = 0; i < nums1.length ; i++){
           if(countMap.containsKey(nums1[i])){
               int count = countMap.get(nums1[i]);
               if(count > 0){
                   intersectedList.add(nums1[i]);
               }
               count--;
               countMap.put(nums1[i],count);
           }
       }
        
       return intersectedList.stream().mapToInt(i->i).toArray();
        
    }
}
```
Note: We can use 1001 length array, instead of map

