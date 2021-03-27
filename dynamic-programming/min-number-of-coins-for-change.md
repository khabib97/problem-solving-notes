# Min Number Of Coins For Change

Author: Kawser

Type: Dynamic Programming


### Problem
Given an array of positive integers representing coin denominations and a single non-negative integer n representing a target amount of money, 
write a function that returns the smallest number of coins needed to make change for (to sum up to) that target amount using the given coin denominations.

Note that you have access to an unlimited amount of coins. In other words, if the denominations are [1, 5, 10], 
you have access to an unlimited amount of 1 s, 5 s, and 10 s.

If it's impossible to make change for the target amount, return -1.

Sample Input:
```
n = 7
denoms = [1,5,10]
```
Sample Output:
``` 
3 // 2x1 + 1x5
```

### Solution

Best video explanation : [The Change Making Problem - Fewest Coins To Make Change Dynamic Programming](https://www.youtube.com/watch?v=jgiZlGzXMBw&list=PLiQ766zSC5jM2OKVr8sooOuGgZkvnOCTI&index=12)

### 1. Top down approach

We can start from the amount, and build it recursively using this coins, we can cache the result to reduce redundant calculations.   

![Top Down Approach](https://github.com/khabib97/problem-solving-notes/blob/main/dynamic-programming/images/top-down-approach.png)

### 2. Bottom up approach

#### 2.1 Approach 1
```java
import java.util.*;

class Program {
  public static int minNumberOfCoinsForChange(int n, int[] denoms) {
    int[] numOfCoins = new int[n+1];
		Arrays.fill(numOfCoins, Integer.MAX_VALUE);
		numOfCoins[0] = 0;
		
		for(int amount = 1; amount <= n; amount++){
			for(int denom: denoms){
				if(denom <= amount){
					int subAmount = amount - denom;
					//init newWays set Max Value
					int newWays = Integer.MAX_VALUE;
					int subProbWays = numOfCoins[subAmount];
					if(subProbWays !=  Integer.MAX_VALUE){
						newWays = subProbWays + 1;
					}
					numOfCoins[amount] = Math.min(numOfCoins[amount], newWays);
				}
			}
		}
    return numOfCoins[n] != Integer.MAX_VALUE ? numOfCoins[n] : -1;
  }
}
```
#### 2.2 Approach 2
```java
class Program {
  public static int minNumberOfCoinsForChange(int n, int[] denoms) {
    int[] numofCoin = new int[n+1];
		Arrays.fill(numofCoin,Integer.MAX_VALUE);
		numofCoin[0]=0;
    
		int toCompare=0;
		for(int denom:denoms){
			for(int currAmount=1;currAmount<=n;currAmount++){
				if(denom <= currAmount){
					if(numofCoin[currAmount-denom] == Integer.MAX_VALUE){
						toCompare = numofCoin[currAmount-denom];
					}else{
						toCompare = numofCoin[currAmount-denom]+1;
					}
					numofCoin[currAmount] =  Math.min(numofCoin[currAmount], toCompare);
				}
			}
		}
    return numofCoin[n] == Integer.MAX_VALUE ? -1 : numofCoin[n] ;
  }
}

```
### Time and Space Complexity

Both for top down and bottom up approach

|complexity|value|
|----------|-----|
|time      |O(nd)|
|space     |O(n) | 
