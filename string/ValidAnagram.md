#   Valid Anagram

`Easy`

### Problem
Given two strings s and t, return true if t is an anagram of s, and false otherwise.
 
```
Example 1:

Input: s = "anagram", t = "nagaram"
Output: true
Example 2:

Input: s = "rat", t = "car"
Output: false
``` 

#### Constraints:

1 <= s.length, t.length <= 5 * 104

s and t consist of lowercase English letters.

### Solution

Time O(n) | Space o(1)
```
class ValidAnagram {
    public boolean isAnagram(String s, String t) {
        char[] sArr = s.toCharArray();
        char[] tArr = t.toCharArray();
        
        if(sArr.length != tArr.length) return false;
        
        int[] map = new int[26];
        
        for(int i= 0; i < sArr.length; i++){
            int val = sArr[i] - 97;
            map[val]++;
            val = tArr[i] - 97 ;
            map[val]--;
        }
        
        for(int i=0; i < map.length;i++){
            
            if(map[i] != 0){
                return false;
            }
        }
        
        return true;
        
    }
}
```
