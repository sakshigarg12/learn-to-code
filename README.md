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
Source - Leetcode
Topic : Array
Problem : Container With Most water 
In this problem , we are given an array of heights of walls and we have to find maximum area among these walls that hold water.
hence , we are using here two pointer approach , using two pointer we find the maximum area as it is very much time consuming to calculate area for every wall one by one .
given height = [1,8,6,2,5,4,8,3,7]
Approach : 
lets take two pointer 
left = 0 //starting index
right = 8 //last index
//we take this maxArea to every time compare it with finding area to get maximum area
while(left < right){
//for finding area we should know height and width of the wall
//height is minimum between the height of two respected walls between them we are calculating area because mimimum height is the bottleneck upto that we can store water
wallheight = Math.min(height[left], height[right])
//width is the distance between two walls
width = right - left
area = wallheight* width
//now find maximumarea
maxArea = Math.max(maxArea, area)
if(height[left] < height[right])
//we always shift from minimum height because it might be possible that after that minimum height we got maximum height and if we shift from maximum height than there is no change in height it will be same
left++
else
right--

Source - Leetcode
Topic: Arrays + Two Pointers
Problem : 3Sum
integer array nums, return all unique triplets [nums[i], nums[j], nums[k]] such that: i!=j, j!=k, i!=k , nums[i] + nums[j] + nums[k] == 0 .The solution must not contain duplicate triplets.
The brute force approach uses 3 nested loops, resulting in O(n³) time complexity — which is too slow for large inputs.
Instead, we can sort the array and use the two-pointer technique to find the remaining two numbers for each nums[i].

Approach:
Sort the array.
Loop through each element i in the array:
Skip duplicates for the fixed element.
For each i, set two pointers:
left = i + 1
right = nums.length - 1
While left < right:
Calculate the sum: nums[i] + nums[left] + nums[right]
If sum is zero, store the triplet and skip duplicates.
If sum < 0 → increase left
If sum > 0 → decrease right

✅ Steps in Code:
public List<List<Integer>> threeSum(int[] nums) {
    List<List<Integer>> res = new ArrayList<>();
    Arrays.sort(nums); // Step 1: Sort the array
    for (int i = 0; i < nums.length - 2; i++) {
        // Step 2: Skip duplicate elements
        if (i > 0 && nums[i] == nums[i - 1]) continue;
        int left = i + 1;
        int right = nums.length - 1;
        while (left < right) {
            int sum = nums[i] + nums[left] + nums[right];
            if (sum == 0) {
                // Found a valid triplet
                res.add(Arrays.asList(nums[i], nums[left], nums[right]));
                // Skip duplicates for left and right
                while (left < right && nums[left] == nums[left + 1]) left++;
                while (left < right && nums[right] == nums[right - 1]) right--;
                left++;
                right--;
            } else if (sum < 0) {
                left++; // Increase the sum
            } else {
                right--; // Decrease the sum
            }
        }
    }
    return res;
}

DATE : 05-07-2025
----------------------------------------------------------------------------LOVE BABBAR DSA SHEET ---------------------------------------------------------------------------
	
Given an array which consists of only 0, 1 and 2. Sort the array without using any sorting algo

approach : brute force
1. we count the number of 0's, 1's, 2's
2. we add them in array in a sorted order according to their count

class Solution {
    public void sortColors(int[] nums) {
        int count0 = 0;
        int count1 = 0;
        int count2 = 0;
        for(int i = 0; i<nums.length; i++){
            if(nums[i] == 0) count0++;
            else if(nums[i] == 1) count1++;
            else count2++;
        }   
        int ind = 0;
        for(int i = 0; i<count0; i++){
            nums[ind++]= 0;
        }
        for(int i = 0; i<count1; i++){
            nums[ind++]= 1;
        }
        for(int i = 0; i<count2; i++){
            nums[ind++]= 2;
        }
    }
}

approach optimal  : DNF Algorithm (Dutch national flag algorithm)
here we solve the problem in one way only
1.3 pointers we use namely low, mid and high
2. while low, mid point at 0 high point at last position 
basically , according to vision array divides into 3 parts low, mid and high if we get 0 it inserts in between 0 to low-1
1 is in low to mid-1 and our unsorted array left between mid to high part which become empty and from high third value is present

code : 
class Solution {
    public void sortColors(int[] nums) {
        int low = 0;
        int mid= 0;
        int high = nums.length - 1;
        while(mid <= high){
            if(nums[mid] == 0){
                swap(nums, mid, low);
                mid++;
                low++;
            }
            else if(nums[mid] == 1) mid++;
            else{
                swap(nums, mid, high);
                high--;
            }
        }
    }
    public void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}

Maximum Subarray Sum (Kadane's Algorithm)

Given an integer array nums, find the subarray with the largest sum, and return its sum
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: The subarray [4,-1,2,1] has the largest sum 6.

Approach:
--------
1. Brute force : 
we used two loops o(n^2) approach in which we are using two for loops and checking the sum of each and every subarray and return the maximum subarray sum
like [-2,1,-3,4,-1,2,1,-5,4]
let start = 0
cursum = 0 maxsum = 0
-2 -2+1 -2+1+-3  -2+1+-3+4  -2+1+-3+4+-1 -2+1+-3+4+-1+2+1+-5 -2+1+-3+4+-1+2+1+-5+4  
so lets cursum = 0 
currsum = -2 maxsum = math.max(-2, 0)= 0
here maxsum= 1 for [-2,1,-3,4,-1,2,1,-5,4]
then start = 1 , here we start from 1 to end 
same for all subarrays 

code : 
 int maxSubarraySum(int[] arr) {
        // Code here
        int n = arr.length;
        int maxsum = 0;
        for(int start = 0; start < n;start++){
            int cursum = 0;
            for(int end  = start; end < n ;end++){
                cursum += arr[end];
                maxsum = Math.max(cursum, maxsum);
            }
        }
        return maxsum;
    }

2. Optimal Approach :

Kadane's Algoirthm : In this algo , we optimised our approach as we know our array may contain both the numbers negative and positive and in brute approach we are adding all elements of all the subarrays without bothering about positive and negative but in optimised approach when we get any bigger negative we donot add it because it decrease the number or make it negative that's why atlast we add a condition that if sum of the subarray is less than 0 then sum becomes 0 or we reinitialize it then continue till end with same process until we get maximum sum and maximum sum we maintain also till the end we initialize it with minimum integer value and return it with maximum value at end

code : 
public int maxSubArray(int[] nums) {
        int maxsum = Integer.MIN_VALUE;
        int currsum = 0;
        for(int i = 0; i<nums.length; i++){
            currsum += nums[i];
            maxsum = Math.max(currsum, maxsum);
            if(currsum < 0){
                currsum = 0;
            }
        }
        return maxsum;
}

Move all negative elements to end

code:
public void segregateElements(int[] arr) {
        // Your code goes here
        int[] temp = new int[arr.length];
        int index = 0;
        for(int i=0; i<arr.length; i++){
            if(arr[i] >= 0){
                temp[index++] = arr[i];
            }
        }
        for(int i=0; i<arr.length; i++){
            if(arr[i] < 0){
                temp[index++] = arr[i];
            }
        }
        for(int i=0; i<arr.length; i++){
            arr[i] = temp[i];
        }
    }
	
Find the maximum and minimum element in an array

code: 
public Pair<Integer, Integer> getMinMax(int[] arr) {
        // Code Here
        // if(arr.length == 0 || arr == null) return 0;
        int min = arr[0];
        int max = arr[0];
	for(int i = 1; i<arr.length; i++){
            if(arr[i] < min) min = arr[i];
            if(arr[i] > max) max = arr[i];
        }
        return new Pair<>(min, max);
    }
	
Find the "Kth" max and min element of an array

Concept : Using Priority Queues we find maximum kth element in an array using min heap and we find minimum kth element in an array using max heap and maxheap we initialize using priority queue from collections using reverseOrder method because bydefalult priority queue initialize minheap

public static int kthSmallest(int[] arr, int k) {
        // Your code here
       PriorityQueue<Integer> maxheap = new PriorityQueue<>(Collections.reverseOrder());
       for(int i = 0; i<arr.length; i++){
          maxheap.add(arr[i]);
	  if(maxheap.size() > k){
              maxheap.poll();
          }
      }
      return maxheap.peek();
    }


date : 17-07-2025

Learnt about shell sort through problem Merge two sorted arrays without using extra space 
Actually in this question we sort the array with variable gap and gap we defined as the distance between two elements to compare them for sorting 

if we apply brute force approach we require extra space or extra array where we store two arrays together after sorting them then transefer them in their respective spaces 
hence it is not valid as question demands no extra space

optimised approach : gap method or shell sort 

code : 
    public void mergeArrays(int a[], int b[]) {
        // code here
        int n = a.length;
        int m = b.length;
        int gap = nextGap(n+m);
        while(gap > 0){
            int i = 0;
            int j = gap;
        	while(j < (n+m)){
                int first = get(a, b, n, i);
                int second = get(a, b, n, j);
                if(first > second){
                    set(a,b,n,i,second);
                    set(a,b,n,j,first);
                }
                i++;
                j++;
            }
            gap = nextGap(gap);
        }
    }  
    **it is the method where we find the gap**
    public int nextGap(int gap){
        if(gap <= 1) return 0;
        return (gap/2) + (gap%2);
    }
    **Using this method we get the element from index**
    public int get(int[] a, int[] b, int n, int index){
        if(index < n) return a[index];
        return b[index - n];
    } 
    **Using this method we set the element at the index after sorting**
    public void set(int[] a, int[] b, int n, int index, int value){
        if(index < n) a[index] = value;
        else b[index - n] = value;
        
    }

date : 21-07-25

Find the duplicate without using extra space

using slow and fast pointer approach because as we use set it take space hence , by using slow and fast pointer approach which is commonly used in linkedlist to find the cycle here in array we used it as imagining array as linkedlist

Approach : In this approach , we use two pointer starting from same initial index in this question as we have array we treat index as node and element as next node we increment slow pointer by one and fast pointer by two and repeat this until slow equals fast then again initialize slow with initial index and here slow and fast increment by one until slow equals fast , atlast they both were pointing at the element where the cycle starts or which is duplicate

basically let array : 3,1,3,2,4 
slow = fast = 3 at index 0
slow = arr[3] = 2 -> arr[2] = 3
fast = arr[arr[3]] = arr[2] = 3 -> arr[arr[3]] = arr[2] = 3
till slow != fast
now slow = fast = 3

2. slow = arr[0]  = 3
while(slow != fast)
slow = arr[3] = 2
fast = arr[fast] = 2


public int findDuplicate(int[] nums) {
        int slow = nums[0];
        int fast = nums[0];
	do{
            slow = nums[slow];
            fast = nums[nums[fast]];
        }
        while(slow != fast);
        slow = nums[0];
]
        while(slow != fast){
            slow = nums[slow];
            fast = nums[fast];
        }
        return slow;
    }
