# Reverse String

`Easy`

### Problem
Write a function that reverses a string. The input string is given as an array of characters s.

 
```
Example 1:

Input: s = ["h","e","l","l","o"]
Output: ["o","l","l","e","h"]
Example 2:

Input: s = ["H","a","n","n","a","h"]
Output: ["h","a","n","n","a","H"]
``` 

**Constraints**:

1 <= s.length <= 105

s[i] is a printable ascii character.
 

**Follow up**: Do not allocate extra space for another array. You must do this by modifying the input array in-place with O(1) extra memory.

### Solution

Time O(n) | Space O(1)

**Tricky part**: `Loop half array, otherwise ouput will be input string`
```
class ReverseString {
    public void reverseString(char[] s) {
        int j = s.length -1;
        int loop = s.length/2;
        for(int i = 0; i < loop; i++){
            char temp = s[j];
            s[j] = s[i];
            s[i] = temp;
            j--;
        }
    }
}
```
