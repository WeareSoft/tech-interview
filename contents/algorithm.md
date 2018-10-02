# 6. Algorithm
**:book: Contents**
* [BigO](#bigo)
* [DFS와 BFS의 차이](#dfs와-bfs의-차이)
* [Fibonacci에서의 세 가지(Recursion, Dynamic Programming, 반복) 방식에 대한 시간복잡도와 공간복잡도 차이](#fibonacci에서의-재귀-동적프로그래밍-반복의-세-가지-방식에-대한-시간복잡도와-공간복잡도)
* [정렬 알고리즘의 종류와 개념](#정렬-알고리즘의-종류와-개념)

---

### BigO
* BigO의 개념
* BigO의 복잡성 차트 보기
  * <img src="./images/BigO-complexity-chart.png" width="50%" height="50%">
  * -> [http://bigocheatsheet.com/](http://bigocheatsheet.com/)

> :arrow_double_up:[Top](#6-algorithm)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#6-algorithm)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - []()

### DFS와 BFS의 차이
* 깊이 우선 탐색(DFS, Depth-First Search)
  * DFS의 개념: 루트 노드(혹은 다른 임의의 노드)에서 시작해서 다음 분기(branch)로 넘어가기 전에 해당 분기를 완벽하게 탐색하는 방법
    * 미로를 탐색할 때 한 방향으로 갈 수 있을 때까지 계속 가다가 더 이상 갈 수 없게 되면 다시 가장 가까운 갈림길로 돌아와서 이곳으로부터 다른 방향으로 다시 탐색을 진행하는 방법과 유사하다.
    * 즉, 넓게(wide) 탐색하기 전에 깊게(deep) 탐색하는 것이다.
    * 사용하는 경우: **모든 노드를 방문** 하고자 하는 경우에 이 방법을 선택한다.
    * 깊이 우선 탐색(DFS)이 너비 우선 탐색(BFS)보다 좀 더 간단하다.
    * 단순 검색 속도 자체는 너비 우선 탐색(BFS)에 비해서 느리다.
  * DFS의 특징
    * 자기 자신을 호출하는 **순환 알고리즘의 형태** 를 가지고 있다.
    * 전위 순회(Pre-Order Traversals)를 포함한 다른 형태의 트리 순회는 모두 DFS의 한 종류이다.
    * 이 알고리즘을 구현할 때 가장 큰 차이점은, 그래프 탐색의 경우 **어떤 노드를 방문했었는지 여부를 반드시 검사** 해야 한다는 것이다.
      * 이를 검사하지 않을 경우 무한루프에 빠질 위험이 있다.
  * DFS의 과정
    * <img src="./images/dfs-example.png" width="60%" height="60%">
  * DFS의 구현 방법 2가지
    * **1. 순환 호출 이용**
      <!-- * 해당 글에서는 이 방법으로 구현한다. -->
    * **2. 명시적인 스택 사용**
      * 명시적인 스택을 사용하여 방문한 정점들을 스택에 저장하였다가 다시 꺼내어 작업한다.
    * 순환 호출을 이용한 DFS 의사코드(pseudocode)
```java
void search(Node root) {
  if (root == null) return;

  // 1. root 노드 방문
  visit(root);
  root.visited = true; // 1-1. 방문한 노드를 표시

  // 2. root 노드와 인접한 정점을 모두 방문
  for each (Node n in root.adjacent) {
    if (n.visited == false) { // 4. 방문하지 않은 정점을 찾는다.
      search(n); // 3. root 노드와 인접한 정점 정점을 시작 정점으로 DFS를 시작
    }
  }
}
```
* 너비 우선 탐색(BFS, Breadth-First Search)
  * BFS의 개념: 루트 노드(혹은 다른 임의의 노드)에서 시작해서 인접한 노드를 먼저 탐색하는 방법
    * 시작 정점으로부터 가까운 정점을 먼저 방문하고 멀리 떨어져 있는 정점을 나중에 방문하는 순회 방법이다.
    * 즉, 깊게(deep) 탐색하기 전에 넓게(wide) 탐색하는 것이다.
    * 사용하는 경우: **두 노드 사이의 최단 경로** 혹은 **임의의 경로를 찾고 싶을 때** 이 방법을 선택한다.
      * Ex) 지구상에 존재하는 모든 친구 관계를 그래프로 표현한 후 Ash와 Vanessa 사이에 존재하는 경로를 찾는 경우
      * 깊이 우선 탐색의 경우 - 모든 친구 관계를 다 살펴봐야 할지도 모른다.
      * 너비 우선 탐색의 경우 - Ash와 가까운 관계부터 탐색
    * 너비 우선 탐색(BFS)이 깊이 우선 탐색(DFS)보다 좀 더 복잡하다.
  * BFS의 특징
    * 직관적이지 않은 면이 있다.
      * BFS는 시작 노드에서 시작해서 거리에 따라 단계별로 탐색한다고 볼 수 있다.
    * BFS는 **재귀적으로 동작하지 않는다.**
    * 이 알고리즘을 구현할 때 가장 큰 차이점은, 그래프 탐색의 경우 **어떤 노드를 방문했었는지 여부를 반드시 검사** 해야 한다는 것이다.
      * 이를 검사하지 않을 경우 무한루프에 빠질 위험이 있다.
    * BFS는 방문한 노드들을 차례로 저장한 후 꺼낼 수 있는 자료 구조인 **큐(Queue)를 사용한다.**
      * 즉, **선입선출(FIFO)** 원칙으로 탐색
      * 일반적으로 큐를 이용해서 반복적 형태로 구현하는 것이 가장 잘 동작한다.
    * 'Prim', 'Dijkstra' 알고리즘과 유사하다.
  * BFS의 과정
    * 깊이가 1인 모든 노드를 방문하고 나서 그 다음에는 깊이가 2인 모든 노드를, 그 다음에는 깊이가 3인 모든 노드를 방문하는 식으로 계속 방문하다가 더 이상 방문할 곳이 없으면 탐색을 마친다.
    * <img src="./images/bfs-example.png" width="70%" height="70%">
  * BFS의 구현 방법
    * 자료 구조 **큐(Queue)를 이용**
    * 큐(Queue)를 이용한 BFS 의사코드(pseudocode)
```java
void search(Node root) {
  Queue queue = new Queue();
  root.marked = true; // (방문한 노드 체크)
  queue.enqueue(root); // 1-1. 큐의 끝에 추가

  // 3. 큐가 소진될 때까지 계속한다.
  while (!queue.isEmpty()) {
    Node r = queue.dequeue(); // 큐의 앞에서 노드 추출
    visit(r); // 2-1. 큐에서 추출한 노드 방문
    // 2-2. 큐에서 꺼낸 노드와 인접한 노드들을 모두 차례로 방문한다.
    foreach (Node n in r.adjacent) {
      if (n.marked == false) {
        n.marked = true; // (방문한 노드 체크)
        queue.enqueue(n); // 2-3. 큐의 끝에 추가
      }
    }
  }
}
```

> :arrow_double_up:[Top](#6-algorithm)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#6-algorithm)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - [https://gmlwjd9405.github.io/2018/08/14/algorithm-dfs.html](https://gmlwjd9405.github.io/2018/08/14/algorithm-dfs.html)
> - [https://gmlwjd9405.github.io/2018/08/15/algorithm-bfs.html](https://gmlwjd9405.github.io/2018/08/15/algorithm-bfs.html)

### Fibonacci에서의 재귀 동적프로그래밍 반복의 세 가지 방식에 대한 시간복잡도와 공간복잡도
1. 재귀 
2. 동적 프로그래밍 
3. 반복

> :arrow_double_up:[Top](#6-algorithm)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#6-algorithm)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
> - []()

### 정렬 알고리즘의 종류와 개념
* [버블 정렬(Bubble Sort)](https://gmlwjd9405.github.io/2018/05/06/algorithm-bubble-sort.html)
* [삽입 정렬(insertion sort)](https://gmlwjd9405.github.io/2018/05/06/algorithm-insertion-sort.html)
* [선택 정렬(selection sort)](https://gmlwjd9405.github.io/2018/05/06/algorithm-selection-sort.html)
* [합병 정렬(merge sort)](https://gmlwjd9405.github.io/2018/05/08/algorithm-merge-sort.html)
* [퀵 정렬(quick sort)](https://gmlwjd9405.github.io/2018/05/10/algorithm-quick-sort.html)
* [힙 정렬(heap sort)](https://gmlwjd9405.github.io/2018/05/10/algorithm-heap-sort.html)
* [셸 정렬(shell sort)](https://gmlwjd9405.github.io/2018/05/08/algorithm-shell-sort.html)
* 정렬 알고리즘의 애니메이션 보기
  * -> [https://www.toptal.com/developers/sorting-algorithms](https://www.toptal.com/developers/sorting-algorithms)

> :arrow_double_up:[Top](#6-algorithm)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#6-algorithm)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
---

## Reference
> - [https://github.com/tayllan/awesome-algorithms](https://github.com/tayllan/awesome-algorithms)
> - [https://www.cs.usfca.edu/~galles/visualization/Algorithms.html](https://www.cs.usfca.edu/~galles/visualization/Algorithms.html)


## :house: [Home](https://github.com/Do-Hee/tech-interview)
