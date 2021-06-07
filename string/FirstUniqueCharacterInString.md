# First Unique Character in a String

`Easy`

### Problem
Given a string s, return the first non-repeating character in it and return its index. If it does not exist, return -1.
 
```
Example 1:

Input: s = "leetcode"
Output: 0
Example 2:

Input: s = "loveleetcode"
Output: 2
Example 3:

Input: s = "aabb"
Output: -1
``` 
#### Constraints:

1 <= s.length <= 105

s consists of only lowercase English letters.

### Solution
Time O(n)| Space O(1)
```
class FirstUniqueCharacter {
    public int firstUniqChar(String s) {
        
        int[] map = new int[26];
        int len = s.length();
        for(int i = 0 ; i < len ; i++ ){
            map[s.charAt(i)-97]++;
        }
        
        for(int i = 0 ; i < len ; i++ ){
            if(map[s.charAt(i)-97] == 1) return i;
        }
        
        return -1;
    }
}
```
