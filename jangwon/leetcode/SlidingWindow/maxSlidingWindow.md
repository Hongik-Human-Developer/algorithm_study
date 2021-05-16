# Sliding Window

## leetcode 239. Sliding Window Maximum

### https://leetcode.com/problems/sliding-window-maximum/

```py
class Solution:
    def maxSlidingWindow(self, nums: List[int], k: int) -> List[int]:
        if not nums:
            return nums
        
        r = []
        for i in range(len(nums) - k + 1):
            r.append(max(nums[i:i + k]))
            
        return r
```

```py
class Solution:
    def maxSlidingWindow(self, nums: List[int], k: int) -> List[int]:
        results = []
        window = collections.deque()
        current_max = float('-inf')
        for i, v in enumerate(nums):
            window.append(v)
            if i < k - 1:
                continue
            
            # 새로 추가된 값이 기존 최댓값보다 큰 경우 교체
            if current_max == float('-inf'):
                current_max = max(window)
            elif v > current_max:
                current_max = v
            
            results.append(current_max)
            
            # 최대값이 윈도우에서 빠지면 초기화
            if current_max == window.popleft():
                current_max = float('-inf')
        return results
```

```py
class Solution:
    def maxSlidingWindow(self, nums: List[int], k: int) -> List[int]:
        queue = deque() 
        ans = []
        for i, x in enumerate(nums): 
            while queue and queue[-1][1] <= x: queue.pop() 
            queue.append((i, x))
            if queue and queue[0][0] <= i-k: queue.popleft() 
            if i >= k-1: ans.append(queue[0][1])
        return ans 
```