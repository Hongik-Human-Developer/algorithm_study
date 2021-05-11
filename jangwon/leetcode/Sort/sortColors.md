# Sort

## leetcode 75. Sort Colors

### https://leetcode.com/problems/sort-colors/

**파이썬 풀이**

```py
class Solution:
    def sortColors(self, nums: List[int]) -> None:
        red, white, blue = 0, 0, len(nums)
        
        while white < blue:
            if nums[white] < 1:
                nums[red], nums[white] = nums[white], nums[red]
                white += 1
                red += 1
            elif nums[white] > 1:
                blue -= 1
                nums[white], nums[blue] = nums[blue], nums[white]
            else:
                white += 1
```


```js
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var sortColors = function(nums) {
    let r = 0;
    let w = 0;
    let b = nums.length;
    
    while(w < b){
        if(nums[w] < 1){
            let tmp = nums[r];
            nums[r] = nums[w];
            nums[w] = tmp;
            w++;
            r++;
        }
        else if(nums[w] > 1){
            b--;
            let tmp = nums[b];
            nums[b] = nums[w];
            nums[w] = tmp;
        }
        else{
            w++;
        }
    }
};
```