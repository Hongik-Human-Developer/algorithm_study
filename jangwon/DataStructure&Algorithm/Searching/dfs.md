# 깊이 우선 탐색(DFS)

**Concept**

* 깊이 우선 탐색(Depth First Search)은 탐색을 함에 있어서 보다 깊은 것을 우선적을 하여 탐색하는 알고리즘 입니다. 이러한 깊이 우선 탐색은 맹목적으로 각 노드를 탐색할 때 주로 사용됩니다. 너비 우선 탐색에서는 **큐**가 가용되었다면 깊이 우선 탐색에서는 **스택**이 사용됩니다. 더불어 사실 스택을 사용하지 않아도 구현이 가능하다는 특징이 있습니다. **컴퓨터는 구조적으로 항상 스택의 원리를 사용** 하기 때문입니다.(재귀함수원리)

<p align="center">
  <img src="https://camo.githubusercontent.com/307023a33368ed02198844a9b3d9b8b7b470f67bbcc0e88574da939b76775c89/68747470733a2f2f75706c6f61642e77696b696d656469612e6f72672f77696b6970656469612f636f6d6d6f6e732f372f37662f44657074682d46697273742d5365617263682e676966" />
</p>

**알고리즘**

1. 스택의 최상단 노드를 확인합니다.
2. 최상단 노드에게 방문하지 않은 인접 노드가 있으면 그 노드를 스택에 넣고 방문처리합니다. 방문하지 않은 인접노드가 없으면 스택에서 최상단 노드를 뺍니다.

**팁**

* 프로그래밍 대회에서 스택을 구현하는 것이 아닌 **재귀로** 푸는것이 더 많이 활용이 됩니다.

--- 

## Pseudocode 

```js

function search(Node root) {
  if(root === null) return;

  // 1. root 노드 방문
  visit(root);
  root.visited = true; // 방문 노드 표시 

  // 2. root 노드와 인접한 정점을 모두 방문

  forEach(Node n in root.adjacent) {

    // 4. 방문하지 않은 정점을 찾는다. 
    if(n.visited === false){
      search(n) // 3. root 노드와 인접한 정점을 시작 정점으로 DFS를 시작
    } 
  }
}

```


### Recursion DFS

```js

function dfs(root) {
  if(root === null) return [];
  return [...dfs(root.left), root.val, ...dfs(root.right)];
}

```

### Stack DFS

```js

function dfs(root) {
  let stack = [];
  let ret = [];
  let node  = root;

  while(node || stack.length) {

    // 스택에 값 넣기 
    while(node !== null) {
      stack.push(node);
      node = node.left;
    }

    node = stack.pop();
    ret.push(node.val);
    node = node.right;
  }
  return ret;
}

```