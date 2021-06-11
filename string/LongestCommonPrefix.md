# Longest Common Prefix

`Easy`

### Problem
Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

```
Example 1:

Input: strs = ["flower","flow","flight"]
Output: "fl"
Example 2:

Input: strs = ["dog","racecar","car"]
Output: ""
Explanation: There is no common prefix among the input strings.
``` 

#### Constraints:

1 <= strs.length <= 200

0 <= strs[i].length <= 200

strs[i] consists of only lower-case English letters.

### Solution

Time O (nm) | Space O(1)
```
class LongestCommonPrefix {
    public String longestCommonPrefix(String[] strs) {
        String lcp = "";
        int len = strs[0].length();
        boolean flag = true;
        for(int i = 0; i < len; i++){
            
            for(int j = 1; j < strs.length; j++){
                if(flag && i < strs[j].length()  && strs[0].charAt(i) == strs[j].charAt(i)){
                    continue;
                }else{
                    flag = false;
                    break;
                }
            }
            if(flag) lcp += strs[0].charAt(i);
            else break;
        }
        return lcp;
    }
}
```
