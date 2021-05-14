# binary_search

## leetcode 240. Search a 2D Matrix II

### https://leetcode.com/problems/search-a-2d-matrix-ii/

```py
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        for nums in matrix:
            for num in nums:
                if num == target:
                    return True
        
        return False
```

```py
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        # 예외 처리
        if not matrix:
            return False
        
        # 첫 행의 맨뒤
        row = 0
        col = len(matrix[0]) - 1
        
        while row <= len(matrix) - 1 and col >= 0:
            if target == matrix[row][col]:
                return True
            # 타겟이 작으면 왼쪽으로
            elif target < matrix[row][col]:
                col -= 1
            # 타겟이 크면 아래로
            elif target > matrix[row][col]:
                row += 1
        return False
```

**any를 사용한 파이썬 다운 풀이**

```py
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        return any(target in row for row in matrix)
```