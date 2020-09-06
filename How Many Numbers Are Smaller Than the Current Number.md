```js
/*
Given the array nums, for each nums[i] find out how many numbers in the array are smaller than it. 

Input: nums = [8,1,2,2,3]
Output: [4,0,1,1,3]
Explanation: 
For nums[0]=8 there exist four smaller numbers than it (1, 2, 2 and 3). 
For nums[1]=1 does not exist any smaller number than it.
For nums[2]=2 there exist one smaller number than it (1). 
For nums[3]=2 there exist one smaller number than it (1). 
For nums[4]=3 there exist three smaller numbers than it (1, 2 and 2).
*/

/**
 * @param {number[]} nums
 * @return {number[]}
 */
let smallerNumbersThanCurrent = function(nums) {
    let res = [];
    let count = 0;
    
    nums.forEach((num) => {
        nums.forEach((item) => {
            if(num > item ) {
                count++;
            }
        });    
        
        res.push(count);
        count = 0;
    });
    
    return res;
};

```
