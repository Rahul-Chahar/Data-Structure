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
static HashMap<Character, Integer> makeFreqMap(String str){
HashMap<Character, Integer>mp = new HashMap<>();
for(int i =0; I< str.length(); i++){
Character ch = str.length(); i++){
if(!mp.containsKey(ch)){
mp.put(ch,1);
}
else{
int currFreq = mp.get(ch);
mp.put(ch, currFreq+1);
}
}
return mp;

public boolean isAnagram(String s, String t){
is(s.length() =! t.length() return false;
HashMap<Charchter, Integer> mp1 = makeFreqMap(s);
HashMap<Charchter, Integer> mp2 = makeFreqMap(t);
return mp1.equals(mp2);
}
}
```
