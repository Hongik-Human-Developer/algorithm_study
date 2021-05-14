```js
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
var intersection = function(nums1, nums2) {
    let p1 = 0;
    let p2 = 0;
    let num1 = nums1.sort((a,b)=>a-b);
    let num2 = nums2.sort((a,b)=>a-b);
    let result = [];
    while(p1 < num1.length && p2 < num2.length) {
        if(nums1[p1] === nums2[p2]) {
            result.push(nums1[p1]);
            p1++;
            p2++;
        }else {
            if(num1[p1] < num2[p2]) {
                p1++;
            }else {
                p2++;
            }
        }
    }
    
    return [...new Set(result)];
};
```

**파이썬 브루트포스 풀이**

```py
class Solution:
    def intersection(self, nums1: List[int], nums2: List[int]) -> List[int]:
        result: Set = set()
        for n1 in nums1:
            for n2 in nums2:
                if n1 == n2:
                    result.add(n1)
        
        return result
```

**파이썬 투 포인터 알고리즘 풀이**

```py
class Solution:
    def intersection(self, nums1: List[int], nums2: List[int]) -> List[int]:
        result: Set = set()
        # 양쪽 모두 정렬
        nums1.sort()
        nums2.sort()
        i = j = 0
        
        # 투 포인터 우측으로 이동하며 일치 여부 판별
        while i < len(nums1) and j < len(nums2):
            if nums1[i] > nums2[j]:
                j += 1
            elif nums1[i] < nums2[j]:
                i += 1
            else:
                result.add(nums1[i])
                i += 1
                j += 1
        
        return result
```