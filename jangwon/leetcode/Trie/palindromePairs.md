# Trie

## leetcode 336. Palindrome Pairs

### https://leetcode.com/problems/palindrome-pairs/

*브루트 포스 풀이*

- words의 길이가 5000이기 때문에 시간 복잡도 `O(N^2)`의 풀이는 시간 초과가 나온다.
- 시간 복잡도를 줄이기 위해서 `트라이` 구조를 사용하여 풀이 해야한다.

```py
class Solution:
    def palindromePairs(self, words: List[str]) -> List[List[int]]:
        
        def is_palindrome(word):
            return word == word[::-1]
        
        output = []
        for i, word1 in enumerate(words):
            for j, word2 in enumerate(words):
                if i == j:
                    continue
                if is_palindrome(word1 + word2):
                    output.append([i, j])
        
        return output
```