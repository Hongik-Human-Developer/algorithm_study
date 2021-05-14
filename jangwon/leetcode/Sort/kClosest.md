# Sort

## leetcode 973. K Closest Points to Origin

### https://leetcode.com/problems/k-closest-points-to-origin/

```js
/**
 * @param {number[][]} points
 * @param {number} k
 * @return {number[][]}
 */
var kClosest = function(points, k) {
    let result = [];
    
    points.map((el,idx) => {
        let num = Math.sqrt(Math.pow(el[0], 2) + Math.pow(el[1], 2));
        result.push([idx,num]);
    })
    
    result.sort((a,b) => (a[1] - 1) - (b[1] - 1));
    
    let answer = [];
    
    for(let i=0; i<k; i++){
        let idx = result[i][0];
        answer.push(points[idx]);
    }
    
    return answer;
};
```

```py
class Solution:
    def kClosest(self, points: List[List[int]], k: int) -> List[List[int]]:
        heap = []
        
        for x, y in points:
            dist = math.sqrt((0 - x) ** 2 + (0 - y) ** 2)
            heapq.heappush(heap,(dist, x, y))
        
        result = []
        for _ in range(k):
            (dist, x, y) = heapq.heappop(heap)
            result.append((x, y))
        
        return result
```