# Plus One

`Easy But Not So Easy`

### Problem

Given a non-empty array of decimal digits representing a non-negative integer, increment one to the integer.

The digits are stored such that the most significant digit is at the head of the list, and each element in the array contains a single digit.

You may assume the integer does not contain any leading zero, except the number 0 itself.

 
```
Example 1:

Input: digits = [1,2,3]
Output: [1,2,4]
Explanation: The array represents the integer 123.

Example 2:

Input: digits = [4,3,2,1]
Output: [4,3,2,2]
Explanation: The array represents the integer 4321.

Example 3:

Input: digits = [0]
Output: [1]
```
### Solution 1
`Smart Solution` 
Time O(n) | Space O(n)
```
class OnePlus{
    public int[] plusOne(int[] digits) {
        int size = digits.length;
        //case : 1../ 89../ 889 / 1234/ 8999
        for(int i = size-1; i >= 0; i--){
            if(digits[i] == 9){
                digits[i] = 0;
            }else{
                digits[i]++;
                return digits;
            }
        }
        
        //case: 99 / 999 / 999 ...
        int[] newDigits = new int[size+1];
        newDigits[0] = 1;
        return newDigits;
    }
}
```
### Solution 2
Time O(n)| Space O(n)
```
class OnePlus {
    public int[] plusOne(int[] digits) {
        List<Integer> digitList = new ArrayList<>();
        int extra = 0;
        
        int digit = digits[digits.length-1] + 1;
        if(digit > 9){
            extra = 1;
            digitList.add(0);
        }else{
            digitList.add(digit);
        }
        
        for(int i = digits.length-2; i >= 0; i--){
            digit = digits[i] + extra;
            if(digit > 9){
               extra = 1;
               digitList.add(0); 
            }else{
                extra = 0;
                digitList.add(digit);
            }
        }
               
        if(extra == 1){
            digitList.add(1);
        }

        int size = digitList.size();
        int[] newDigits = new int[size];
        
        int position = size - 1;
        for(int d: digitList){
            newDigits[position--] = d;
        }
        return newDigits;
    }
}
```
