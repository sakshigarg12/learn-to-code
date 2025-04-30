# learn-to-code
My journey of learning to code try to show up daily here and maintain my consistency .

Day-1 
Source - Leetcode
Problem - Search Insert Position in O(Logn)
In this problem, we are given an array and a target in which we have to search the insert position of target if its present then its position else the position in which it will be inserted if present 
My 1st approach : I tried to solve it with linear search and it is taking time hence solved it using binary search 

Example : array = [1, 2, 3, 6 ,7] target = 8
output : 5

left = 0 right = array.length-1 
i = 0 n = array.length
for(i to n-1)
mid = left + (right-left)/2
arr[i] < target  left = mid+1
else right = mid - 1
return left
//return left as it always be at position where element is or need to be inserted

Day-2
Source - Leetcode
Problem - Plus One
In this problem , element is given in the form of array and we have to return the element by adding one in it means addding one at last position element but main case arrives when there is 9 at last position then we have to make change at two positions like 999 -> 1000

My Approach : if there is element < 9
then add element+ 1
return array 
else store 0 at the positions
create another array with array+1 length
by default all positions initialize with 0
only make newarray[0] = 1
return newarray

means store carry at first position

//Day - 3
Source - Neetcode 
Topic : Binary Search
Problem : Koko Eating Bananas
In this problem, we are giving array of piles of bananas , and given the minimum time to eat those bananas now we have to find that how much banannas koko eat per hour so he can eat all piles of bananas within that given time , and in one hour he can eat only one pile of bananas if finish early then he has to wait that hour to finish to another pile on another hour.

My Approach : 
In this problem, we use binary search to efficiently find the minimum eating speed k (bananas/hour) at which Koko can finish all the bananas in h hours.
We cannot try every value of k from 1 to max(piles) through brute force — it would be too slow.
So we use binary search in the range [1, max(piles)].We define our binary search range:
left = 1 (minimum possible eating speed),
right = max(piles) (maximum speed — if Koko finishes a full pile in 1 hour).
mid = (left + right) / 2 represents the current eating speed (bananas/hour).
The more bananas Koko eats per hour (higher k), the less total time it takes.
This is a monotonic decreasing function, so binary search works.
For each mid (eating speed), we calculate the total hours Koko needs:

for (int pile : piles) {
    totalHours += (pile + mid - 1) / mid;  // ceiling division
}
We compare this totalHours with the given h
if (totalHours <= h) {
    ans = mid;         // possible answer, but maybe we can do better (lower k)
    right = mid - 1;   // try smaller eating speed
} else {
    left = mid + 1;    // speed too slow, try higher
}


//Day- 4
Source - Neetcode
Topic : Binary Search
Problem : Find Minimum in rotated sorted array
In this problem,

My Approach : 
In this problem, we use binary search to efficiently find the minimum element in a rotated sorted array.
We cannot linearly scan the entire array — it would take O(n) time.
Instead, we use binary search to find the rotation point in O(log n) time.
We define our binary search range:

left = 0 (start of the array),
right = nums.length - 1 (end of the array)
We calculate:
mid = (left + right) / 2 → this represents the middle index of our current search window.

Now, based on the sorted + rotated structure, we observe:

If nums[mid] > nums[right], it means the minimum lies in the right half (because the unsorted/rotated part is there)
If nums[mid] <= nums[right], it means the minimum lies in the left half (including mid)
This works because the array is made of two sorted halves, and the minimum is where the order breaks.
We perform binary search as:
while (left < right) {
    int mid = left + (right - left) / 2;
    if (nums[mid] > nums[right]) {
        left = mid + 1;  // minimum is in the right half
    } else {
        right = mid;     // minimum is at mid or in the left half
    }
}
Once left == right, we've found the index of the smallest element, and return nums[left].

Source - Neetcode
Topic : Binary Search
Problem : Searching in Rotated Sorted Arrays
In this problem,

My Approach : 
In this problem, we use binary search to efficiently find the target element in a rotated sorted array.
We cannot use linear search — that would take O(n) time.
So we apply binary search in a smart way by observing how the rotation splits the array into two sorted halves.
We define:

left = 0 (start of the array)
right = nums.length - 1 (end of the array)
mid = (left + right) / 2 → midpoint of current search space
At every step:

Check if nums[mid] == target → return mid
Otherwise, decide which half to search next using the sorted property:

1️⃣ If the left half is sorted:
if (nums[left] <= nums[mid]) {
    if (nums[left] <= target && target < nums[mid]) {
        right = mid - 1;  // Target lies in the sorted left half
    } else {
        left = mid + 1;   // Target lies in the right half
    }
}
2️⃣ Else the right half is sorted:
else {
    if (nums[mid] < target && target <= nums[right]) {
        left = mid + 1;   // Target lies in the sorted right half
    } else {
        right = mid - 1;  // Target lies in the left half
    }
}


//Day -6 
Source - Neetcode
Topic : Binary Search
Problem : Time Based Key-Value Store
