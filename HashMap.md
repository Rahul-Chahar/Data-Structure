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
```
