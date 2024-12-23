Given a string, write a program to output every non-empty substring of the given string in a lexographically sorted order.

**Note:** Here we will not consider an empty string as the subset of a string.

### Example 1:
```
Input: s = abc
Output: [a, ab, abc, ac, b, bc, c]
```

### Example 2:
```
Input: s = ab
Output: [a, ab, b]
```

### Constraints
```
1 <= s.length <= 10
A <= s[i] <= Z
All the characters of the given String are unique.
```

## Solution

```
import java.util.*;
public class Solution {
    public static List<String> findSubstrings(String s) {
```

Sort the characters = ['a', 'b', 'c']
```
        char[] chars = s.toCharArray();
        Arrays.sort(chars);
```

result = []
```
        List<String> subsets = new ArrayList<>();
```

Generate subsets (using a helper function)
```
        getSubsets(chars, 0, new StringBuilder(), subsets);
```

To Match expected output **(as per problem)** ["a", "ab", "abc", "ac", "b", "bc", "c"] 
```
		Collections.sort(subsets);
        return subsets;

    }
```

**Generate subsets**
###### Approach:
```
					f( [**'a'**, 'b', 'c'], "", [] )
									/\
						   include /  \ exclude
  f( ['a', **'b'**, 'c'], "a", [] )   f( ['a', **'b'**, 'c'], "", [] )
```

```
    private static void getSubsets(char[] chars, int index, StringBuilder value, List<String> subsets){
```

Base Case: f (['a', 'b', 'c'])
```
      if (index == chars.length){ 
        //Add the subset, exclude emptyones
```

Excluding empty string **(as per problem)**
```
        if (value.length() > 0){
          subsets.add(value.toString());
        }
```

End of Base Case
```
        return;
      }
```

Include **currentChar**
```
      value.append(chars[index]);
      getSubsets(chars, index + 1, value, subsets);
```

Exclude **currentChar**
```
      value.deleteCharAt(value.length() - 1);
      getSubsets(chars, index + 1, value, subsets);
```

```
    }
}
```