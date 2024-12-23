Given a string **S**, check if it is palindrome or not.

### Example 1:
```
Input: S = "racecar"
Output: 1
Explanation: S is a palindrome
```

### Example 2:
```
Input: S = "adr"
Output: 0
Explanation: S is not a palindrome
```

### Constraints:
```
0 <= length of S <= 2*10^5
```

### Solution

```
public class Solution
{
    public static boolean isPalindrome(String str)
    {
```
Initialize Pointers **(at both ends)**; $right = length() - 1 - left;$
```
      int left = 0;
      int right = str.length() - 1;
```
**Palindrome check**
```
      while (left < right){
```
If both are not pointing to same value return **false**
```
		if (str.charAt(left) != str.charAt(right)){
          return false;
        }
```
Move **Inwards** if both pointing to same value.
```
        left++;
        right--;
      }
```
return **true** 
```      
      return true;
    }
}
```