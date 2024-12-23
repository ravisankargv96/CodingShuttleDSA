## Problem Statement
Given a total of n people and the number k, which means that k-1 people are skipped and the kth person is killed in a predetermined direction in a circle.

The count will begin at the k+1th individual after each operation. The goal is to select a safe location within the circle so that, after performing these actions starting from the first position within the circle, you are the only one left alive.

### Example 1:
```
Input:
n = 3 k = 2
Output: 3
Explanation: There are 3 people, hence the second person will die if the first person is skipped. The safe position is 3.
```

### Example 2:
```
Input:
n = 1 k = 1
Output: 1
```

### Constraints:
```
1 <= k, n <= 20
```


# Solution

### Theory:
1. **Recursive Relation**:
   - The Josephus problem can be solved using a recursive relation:
     \[
     J(n, k) = (J(n-1, k) + k) \% n
     \]
     where:
     - \( J(n, k) \) is the safe position when there are \( n \) people and \( k \)-th person is killed.
     - Base case: \( J(1, k) = 0 \) (0-based index).

2. **Adjust for 1-Based Index**:
   - Since the recursive relation gives a 0-based index, we convert it to a 1-based index by adding 1.

### Code
```
public class Solution
{
   public int josephus(int n, int k)
    {
```
Single person
```
      int safePos = 0;
```

j(i, k) = ( j(i-1, k) + k ) % i
```      
      for (int i = 2; i <= n; i++){
        safePos = (safePos + k) % i;
      }
```
Adjust to 1-based index
```
      return safePos + 1;
    }
}
```
