# Binary Search
1-> It is used to seach a given element in a sorted space(array)

2-> imp
It is used to reduce the search space in half after every turn 


**Note-> When**
Usually we apply B.S when it is given that or "It is a sorted array"


```
if(arr[mid] < target) go right
else if (arr[mid] > target) go left
else (arr[mid] == target) done
```

# Binary Search Algorithm
```
arr = {10,15,21,34,81,105,180,500,614}
target = 21
lo = 10;
hi = 614

while(lo<=hi){
int mid = (lo+hi)/2;
if(arr[mid] < target)  lo = mid+1
else if (arr[mid] > target) hi = mid-1
else if(arr[mid] == target) flag = true; break;
}
```


# Time Complexity analysis
T.C = O(log n)

***Note-> mid = lo + (hi-lo)/2;***
