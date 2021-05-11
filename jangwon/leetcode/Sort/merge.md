# Sort

## leetcode. 56. Merge Intervals

### https://leetcode.com/problems/merge-intervals/

```py
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        merged = []
        for i in sorted(intervals, key=lambda x: x[0]):
            if merged and i[0] <= merged[-1][1]:
                merged[-1][1] = max(merged[-1][1], i[1])
            else:
                merged += i,
            
        return merged
```


> 콤마 연산자: 단순이 +=를 했을 경우에는 요소를 이어 붙인다. 콤마를 넣어 연산을 하면 중첩 리스트가 만들어 진다. 콤마는 중첩리스트로 만들어주는 역할을 하며 대괄호 `[]`를 부여 한 것과 동일한 역할을 한다. 