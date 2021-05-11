```py
class LargerNumKey(str):
    def __lt__(x, y):
        return x+y > y+x
        
class Solution:
    def largestNumber(self, nums):
        largest_num = ''.join(sorted(map(str, nums), key=LargerNumKey))
        return '0' if largest_num[0] == '0' else largest_num
```

```py
def solution(nums):
    i = 1
    # 삽입 정렬 구현
    while i < len(nums):
        j = i
        while j > 0 and to_swap(nums[j - 1], nums[j]):
            nums[j], nums[j - 1] = nums[j - 1], nums[j]
            j -= 1
        i += 1
    # map 함수를 이용하여 nums의 요소를 한번에 문자열로 변환, 그 후 ''.join을 통해 문자열로 변환  
    return str(int(''.join(map(str, nums))))

# 특수 조건 해결 
# 비교 대상 두 개의 문자를 문자열로 합쳐 숫자로 변환 후 비교
def to_swap(n1: int, n2: int) -> bool:
        return str(n1) + str(n2) < str(n2) + str(n1)
```