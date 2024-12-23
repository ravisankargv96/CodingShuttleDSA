# Problem Statement:
Given two integers n and r, find <sup>n</sup>C<sub>r</sub>

## Example 1:
```
Input: n = 3, r = 2
Output: 3
Explanation: 3C2 = 3.
```

## Example 2:
```
Input: n = 4, r = 4
Output: 1
```

## Constraints:
```
1 <= n, r <= 20
```

# Solution
```
public class Solution {
   public static int nCr(int n, int r) {

```
Edge Case: n = 2, r = 4
```      
      if (n < r){
        return 0;
      }
```
To avoid calculating the same value multiple times, we use the identity C(n, r) = C (n, n - r)
```
      if(r > n - r){
        r = n - r;
      }

```
Calculate the binomial coeffiecient directly: (n - r + i)/i
i.e. n * n - 1 * ... n - (r - 1) / 1 * 2 * .. * r
```
      long result = 1;

      for (int i = 1; i <= r; i++){
        result *= n - (r - i);
        result /= i;
      }

```
return **result**
```
      return (int)result;     
    }
}
```
