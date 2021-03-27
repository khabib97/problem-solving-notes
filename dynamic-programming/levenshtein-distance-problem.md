# Levenshtein Distance or Edit Distance

Author : Kawser
Type: Dynamic Programming

### Problem

Write a function that takes in two strings and returns the minimum number of edit operations that need 
to be performed on the first string to obtain the second string.

There are three edit operations: `insertion of a character`, `deletion of a character`, and `substitution/replace of a character for another`.

Sample Input
```
str1 = "abc"
str2 = "yabd"
```
Sample Output
```
2 // insert "y"; substitute "c" for "d" 
```

### Solution

Best video lecture to understand and solve this problem: 
[Edit Distance Between 2 Strings - The Levenshtein Distance](https://www.youtube.com/watch?v=MiqoA-yF-0M&list=PLiQ766zSC5jM2OKVr8sooOuGgZkvnOCTI&index=14)

Visualizing before going to the code section:
![Edit Distance](https://github.com/khabib97/problem-solving-notes/blob/main/dynamic-programming/images/edit-distance.png)
```java
import java.util.*;

class Program {
  public static int levenshteinDistance(String str1, String str2) {
    // Write your code here.
		String nStr1 = " "+str1;
		String nStr2 = " "+str2;
		int lenNStr1 = nStr1.length();
		int lenNStr2 = nStr2.length();
		//str2 vartically, str1 horizontally
		int[][] editMatrix = new int[lenNStr2][lenNStr1];
		
		//initialization using property and base case logic
		for(int row = 0; row < editMatrix.length; row++){
			editMatrix[row][0]= row;
		}
		
		for(int col =0; col < editMatrix[0].length; col++){
			editMatrix[0][col] = col;
		}
		//end initialization
		
		
		for(int row = 1; row < editMatrix.length; row++){
			for(int col = 1; col < editMatrix[row].length; col++){
				//When both char are equal we do not need to perform
				//any operation, so cost does not increase, so, cost 
				//will be previous sub-string genaration cost
				if(nStr1.charAt(col) == nStr2.charAt(row)){
					editMatrix[row][col] = editMatrix[row-1][col-1];
				}else{
					int min = Math.min(editMatrix[row][col-1],editMatrix[row-1][col-1]);
					min = Math.min(min,editMatrix[row-1][col]);
					editMatrix[row][col] = min + 1;
				}
			}
		}
    return editMatrix[editMatrix.length-1][editMatrix[0].length-1];
  }
}
```

