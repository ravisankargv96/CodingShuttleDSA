# Nth fibonacci Number
## Problem Statement
Write a program to find Nth Fibonacci number.
The integers in the following order are the Fibonacci numbers:
0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144.
## Example1:
```
Input:
n = 1
Output:
1
Explanation:
1 is the 1st number of fibonacci series.
```
## Example2:
```
Input:
n = 2
Output:
1
Explanation:
1 is the 2nd number of fibonacci series.
```
## Constraints
```
1 <= n <= 30
```

# Solution
```
public class Solution {
    public int nthFibonacci(int n) {
        
```
Base case
```
        if (n == 0 || n == 1) return n;
```
Initial State
```
        long prev1 = 0;
        long prev2 = 1;
        long current = 0;
```
Each State, Calculate current value
```
        for (int i = 2; i <= n; i++) {
            current = prev1 + prev2;
            prev1 = prev2;
            prev2 = current;
        }
```
return final State **current value**
```

        return (int) current;
```
```

    }
}
```
