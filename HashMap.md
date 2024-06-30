Q--> Valid Anagram

Anagram ouse khete jab 2 string ke letters same houte hai for example->

s = silent

t = listen

ye dono ke letters same hai isliye ye anagram hai..


Solution->
* Length of 2 -> equal
* Frequency of each char must be the same
* No character should be extra or different


```
Sure, here is the revised text:

```java
import java.util.HashMap;

public class AnagramChecker {

    public static HashMap<Character, Integer> makeFreqMap(String str) {
        HashMap<Character, Integer> map = new HashMap<>();
        for (int i = 0; i < str.length(); i++) {
            char ch = str.charAt(i);
            map.put(ch, map.getOrDefault(ch, 0) + 1);
        }
        return map;
    }

    public boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) {
            return false;
        }
        HashMap<Character, Integer> map1 = makeFreqMap(s);
        HashMap<Character, Integer> map2 = makeFreqMap(t);
        return map1.equals(map2);
    }
}
```

I made the following changes:
- Renamed the class to `AnagramChecker`.
- Made the `makeFreqMap` method static and fixed the loop and map logic.
- Fixed the `isAnagram` method by adding missing brackets and correcting method parameter types.
  




# Q--> Two Sum
arr = 3,5,4,7

target = 6

output = false


arr = 14,7,10,4,5,9,1,2

target = 13

output = true




```
public int[] twoSum(int[] nums, int target) {
    int n = nums.length;
    int[] ans = {-1};
    for (int i = 0; i < n; i++) {
        for (int j = i + 1; j < n; j++) {
            if (nums[j] == target - nums[i]) {
                ans = new int[]{i, j};
                return ans;
            }
        }
    }
    return ans;
}
```

T.C = O(n2)



Using Map



```
public int[] twoSum(int[] nums, int target) {
    int n = nums.length;
    int[] ans = {-1};
    // value, index
    HashMap<Integer, Integer> map = new HashMap<>();
    
    for (int i = 0; i < n; i++) {
        int partner = target - nums[i];
        if (map.containsKey(partner)) {
            ans = new int[]{i, map.get(partner)};
            return ans;
        }
        map.put(nums[i], i);
    }
    return ans;
}
```

T.C = O(N)




# Q--> Largest subarray with 0 sum.
```
input:
n = 8
arr[] = {15,-2,2,-8,1,7,10,23}
output 5

1-> -2,2 --> length 2
2-> -8,1,7 --> length 3
3-> -2,2-8,1,7 --> length 5 ans

```

```
code
public class LargestSubarray {
    int zeroSumLargestSubarray(int[] arr, int n) {
        HashMap<Integer, Integer> mp = new HashMap<>();
        int maxLen = 0, prefSum = 0;
        mp.put(0, -1);
        for (int i = 0; i < arr.length; i++) {
            prefSum += arr[i];
            if (mp.containsKey(prefSum)) {
                maxLen = Math.max(maxLen, i - mp.get(prefSum));
            } else {
                mp.put(prefSum, i);
            }
        }
        return maxLen;
    }
}
```

T.C = O(N)


```

King
