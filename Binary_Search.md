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


### Lower bound
Q-> Given a sorted integer array and an integer 'x', find the lower bound of x.

**Smallest idx such that arr[idx]>=x**

arr={10,20,30,40,50,60,70}

* x=40 => lb =4
* x=30 => lb =2
* x=35 => lb =4
* x=25 => lb =2
* x=80 => lb =8
* x=5  => lb =0


### Upper bound
Q-> Given a sorted integer array and an integer 'x', find the upper bound of x.

**Ub is the minimum idx such that arr[idx] > x**

arr = {10,20,30,30,40,50,60,70}

* x =30 || lb = 2 || ub = 4
* x =35 || lb = 4 || ub = 4
* x =5  || lb = 0 || ub = 0
* x =80 || lb = 8 || lb = 8


Q-> Find the first and last position of the element in a sorted array.

arr = {10,10,20,20,20,20,30,30,30,40,40}

x = 20

fp = 2

lp = 6 

Method -1st---
* Step's ->
* Check if the element is present or not
* find lb
* find up



Q-> Peak index in a Mountain Array

arr = {10,20,30,50,40,20,,4}

**Note --> first or last element toh kabhi peak hou nahi sakte**

peak = 3

1st Method --> Linear Search
```
if(arr[i] > arr[i-1] && arr[i]> arr[i+1]
return i
```

2nd Method ---> Binary Search
```
int lo = 1, hi = n-2;

if(arr[mid] > arr[mid-1] && arr[mid] > arr[mid+1] return mid;
else if(arr[mid] > arr[mid-1] && arr[mid] < arr[mid+1]   lo = mid+1;
else if (arr[mid] < arr[mid-1] && arr[mid] > arr[mid+1]  hi = mid-1;
```


## Search in rotated array
arr = 3,4,5,6,7,0,1,2

Method -1 --> Find the pivot index.

p -> pivot --> pivot largest element hi houga.

* Hint
  ```
  int p;
  if(arr[m] > arr[m-1] && arr[m] > arr[m+1]) p = mid; break;
   else if(arr[m] < arr[m-1] && arr[m] < arr[m+1]) p = mid-1; break;
   else if(arr[m] > arr[m-1] && arr[m] < arr[m+1]){
     if(arr[m] > arr[n-1]) lo = mid+1;
  else hi = mid -1;
```

11🕚
11:11
```

## Find the first and last occurrence
```
class Solution {
    public int[] element_search(int[] nums, int target) {
        int low = 0;
        int high = nums.length-1;
        int arr[] = {-1,-1};

        // first ocurrence
        while(low<=high){
            int mid = (low+high)/2;
            if(nums[mid]==target){
              arr[0] = mid;
              high = mid-1;
            }
            else if(nums[mid]<target){
                low = mid+1;
            }
            else high = mid-1;
        }
        low = 0;
        high = nums.length-1;
        while(low<=high){
            int mid =(low+high)/2;
            if(nums[mid]==target){
               arr[1] = mid;
               low = mid+1;
            }
            else if(nums[mid]<target){
                low = mid+1;
            }
            else high = mid-1;
        }
        return arr;
    }
}
```

## Count the Zeros
```
class Solution {
    public int countZeros(int[] nums) {
        int low = 0;
        int high = nums.length - 1;

        // Binary search to find the first occurrence of 0
        while (low <= high) {
            int mid = (low + high) / 2;
            if (nums[mid] == 0) {
                high = mid - 1;  // continue searching on the left side
            } else {
                low = mid + 1;  // move to the right side
            }
        }

        // At this point, 'low' should be the index of the first 0
        // If 'low' is out of bounds or the element at 'low' is not 0, return 0
        if (low < nums.length && nums[low] == 0) {
            return nums.length - low;
        } else {
            return 0;  // No 0s found in the array
        }
    }
}
```
