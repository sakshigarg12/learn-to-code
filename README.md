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

