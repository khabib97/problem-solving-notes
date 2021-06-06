# Valid Palindrome

`Easy`

### Problem

Given a string s, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

```
Example 1:

Input: s = "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.
Example 2:

Input: s = "race a car"
Output: false
Explanation: "raceacar" is not a palindrome.
``` 

#### Constraints:

1 <= s.length <= 2 * 105

s consists only of printable ASCII characters.

### Solution

Time O(n) | Space O(n)
```
class ValidPalindrome {
    public boolean isPalindrome(String s) {
        s = s.toLowerCase();
        int len = s.length();
        
        int left = 0;
        int right = len - 1;
        char[] sArr = s.toCharArray();
        
        while(left < right){
            if(!isAlphaNumeric(sArr[left])) left++;
            else if(!isAlphaNumeric(sArr[right])) right--;
            else if(sArr[left] != sArr[right]) return false;
            else{
                left++;
                right--;
            }
            
        }
        return true;
    }
    
    public boolean isAlphaNumeric(int value){
        return ((57 >= value &&  value >= 48 ) || ( 122 >= value && value >= 97));
    }
}
```
