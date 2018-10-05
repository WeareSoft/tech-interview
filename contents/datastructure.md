# 1. Data Structure
**:book: Contents**
* [Array](#array)
* [LinkedList](#linkedlist)
* [HashTable](#hashtable)
* [Stack](#stack)
* [Queue](#queue)
* [Graph](#graph)
* [Tree](#tree)
* [그래프(Graph)와 트리(Tree)의 차이점](#그래프와-트리의-차이점)
* [Binary Heap](#binary-heap)
* [Red-Black Tree](#red-black-tree)
* [B+ Tree](#B+-Tree)

---

### Array

<div align=center>
:arrow_double_up:[Top](#1-data-structure)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#1-data-structure)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
</div>

> - []()

### LinkedList

<div align=center>
:arrow_double_up:[Top](#1-data-structure)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#1-data-structure)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)

</div>
> - []()

### HashTable

<div align=center>
:arrow_double_up:[Top](#1-data-structure)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#1-data-structure)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
</div>

> - []()

### Stack
* 스택(Stack)의 개념
    * 한 쪽 끝에서만 자료를 넣고 뺄 수 있는 LIFO(Last In First Out) 형식의 자료 구조
* 스택(Stack)의 연산
  * 스택(Stack)는 LIFO(Last In First Out) 를 따른다. 즉, 가장 최근에 스택에 추가한 항목이 가장 먼저 제거될 항목이다.
    * pop(): 스택에서 가장 위에 있는 항목을 제거한다.
    * push(item): item 하나를 스택의 가장 윗 부분에 추가한다.
    * peek(): 스택의 가장 위에 있는 항목을 반환한다.
    * isEmpty(): 스택이 비어 있을 때에 true를 반환한다.
* 스택(Stack)의 사용 사례
  * 재귀 알고리즘을 사용하는 경우 스택이 유용하다.
    * 재귀 알고리즘
      * 재귀적으로 함수를 호출해야 하는 경우에 임시 데이터를 스택에 넣어준다.
      * 재귀함수를 빠져 나와 퇴각 검색(backtrack)을 할 때는 스택에 넣어 두었던 임시 데이터를 빼 줘야 한다.
      * 스택은 이런 일련의 행위를 직관적으로 가능하게 해 준다.
      * 또한 스택은 재귀 알고리즘을 반복적 형태(iterative)를 통해서 구현할 수 있게 해준다.
    * 웹 브라우저 방문기록 (뒤로가기)
    * 실행 취소 (undo)
    * 역순 문자열 만들기
    * 수식의 괄호 검사 (연산자 우선순위 표현을 위한 괄호 검사)
      * Ex) 올바른 괄호 문자열(VPS, Valid Parenthesis String) 판단하기
    * 후위 표기법 계산

<div align=center>
:arrow_double_up:[Top](#1-data-structure)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#1-data-structure)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
</div>

> - [https://gmlwjd9405.github.io/2018/08/03/data-structure-stack.html](https://gmlwjd9405.github.io/2018/08/03/data-structure-stack.html)

### Queue
* 큐(Queue)의 개념
  * 컴퓨터의 기본적인 자료 구조의 한가지로, 먼저 집어 넣은 데이터가 먼저 나오는 FIFO(First In First Out)구조로 저장하는 형식
* 큐(Queue)의 연산
  * 큐(Queue)는 FIFO(First-In-First-Out) 를 따른다.
    * add(item): item을 리스트의 끝부분에 추가한다.
    * remove(): 리스트의 첫 번째 항목을 제거한다.
    * peek(): 큐에서 가장 위에 있는 항목을 반환한다.
    * isEmpty(): 큐가 비어 있을 때에 true를 반환한다.
* 큐(Queue)의 사용 사례
  * 데이터가 입력된 시간 순서대로 처리해야 할 필요가 있는 상황에 이용한다.
    * 너비 우선 탐색(BFS, Breadth-First Search) 구현
      * 처리해야 할 노드의 리스트를 저장하는 용도로 큐(Queue)를 사용한다.
      * 노드를 하나 처리할 때마다 해당 노드와 인접한 노드들을 큐에 다시 저장한다.
      * 노드를 접근한 순서대로 처리할 수 있다.
    * 캐시(Cache) 구현
    * 우선순위가 같은 작업 예약 (인쇄 대기열)
    * 선입선출이 필요한 대기열 (티켓 카운터)
    * 콜센터 고객 대기시간
    * 프린터의 출력 처리
    * 윈도우 시스템의 메시지 처리기
    * 프로세스 관리

> :arrow_double_up:[Top](#1-data-structure)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#1-data-structure)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)

> - [https://gmlwjd9405.github.io/2018/08/02/data-structure-queue.html](https://gmlwjd9405.github.io/2018/08/02/data-structure-queue.html)

### Graph
* 그래프(Graph)의 개념
  * 단순히 노드(N, node)와 그 노드를 연결하는 간선(E, edge)을 하나로 모아 놓은 자료 구조
    * 즉, 연결되어 있는 객체 간의 관계를 표현할 수 있는 자료 구조이다.
    * Ex) 지도, 지하철 노선도의 최단 경로, 전기 회로의 소자들, 도로(교차점과 일방 통행길), 선수 과목 등
    * 그래프는 여러 개의 고립된 부분 그래프(Isolated Subgraphs)로 구성될 수 있다.
* 그래프(Graph)의 특징
  * 그래프는 네트워크 모델 이다.
  * 2개 이상의 경로가 가능하다.
    * 즉, 노드들 사이에 무방향/방향에서 양방향 경로를 가질 수 있다.
  * self-loop 뿐 아니라 loop/circuit 모두 가능하다.
  * 루트 노드라는 개념이 없다.
  * 부모-자식 관계라는 개념이 없다.
  * 순회는 DFS나 BFS로 이루어진다.
  * 그래프는 순환(Cyclic) 혹은 비순환(Acyclic)이다.
  * 그래프는 크게 방향 그래프와 무방향 그래프가 있다.
  * 간선의 유무는 그래프에 따라 다르다.

<div align=center>
:arrow_double_up:[Top](#1-data-structure)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#1-data-structure)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
</div>

> - [https://gmlwjd9405.github.io/2018/08/13/data-structure-graph.html](https://gmlwjd9405.github.io/2018/08/13/data-structure-graph.html)

### Tree
* 트리(Tree)의 개념
  * 트리는 노드로 이루어진 자료 구조
    1. 트리는 하나의 루트 노드를 갖는다.
    2. 루트 노드는 0개 이상의 자식 노드를 갖고 있다.
    3. 그 자식 노드 또한 0개 이상의 자식 노드를 갖고 있고, 이는 반복적으로 정의된다.
  * 노드(node)들과 노드들을 연결하는 간선(edge)들로 구성되어 있다.
    * 트리에는 사이클(cycle)이 존재할 수 없다.
    * 노드들은 특정 순서로 나열될 수도 있고 그럴 수 없을 수도 있다.
    * 각 노드는 부모 노드로의 연결이 있을 수도 있고 없을 수도 있다.
    * 각 노드는 어떤 자료형으로도 표현 가능하다.
  * 비선형 자료구조로 계층적 관계를 표현한다. Ex) 디렉터리 구조, 조직도
  * 그래프의 한 종류
    * 사이클(cycle)이 없는 하나의 연결 그래프(Connected Graph)
    * 또는 DAG(Directed Acyclic Graph, 방향성이 있는 비순환 그래프)의 한 종류 이다.
~~~java
class Node {
  public String name;
  public Node[] children;
}
~~~
* 트리(Tree)의 특징
  * 그래프의 한 종류이다. ‘최소 연결 트리’ 라고도 불린다.
  * 트리는 계층 모델 이다.
  * 트리는 DAG(Directed Acyclic Graphs, 방향성이 있는 비순환 그래프)의 한 종류이다.
    * loop나 circuit이 없다. 당연히 self-loop도 없다.
    * 즉, 사이클이 없다.
  * 노드가 N개인 트리는 항상 N-1개의 간선(edge)을 가진다.
    * 즉, 간선은 항상 (정점의 개수 - 1) 만큼을 가진다.
  * 루트에서 어떤 노드로 가는 경로는 유일하다.
    * 임의의 두 노드 간의 경로도 유일하다. 즉, 두 개의 정점 사이에 반드시 1개의 경로만을 가진다.
  * 한 개의 루트 노드만이 존재하며 모든 자식 노드는 한 개의 부모 노드만을 가진다.
    * 부모-자식 관계이므로 흐름은 top-bottom 아니면 bottom-top으로 이루어진다.
  * 순회는 Pre-order, In-order 아니면 Post-order로 이루어진다. 이 3가지 모두 DFS/BFS 안에 있다.
  * 트리는 이진 트리, 이진 탐색 트리, 균형 트리(AVL 트리, red-black 트리), 이진 힙(최대힙, 최소힙) 등이 있다.

<div align=center>
:arrow_double_up:[Top](#1-data-structure)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#1-data-structure)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
</div>

> - [https://gmlwjd9405.github.io/2018/08/12/data-structure-tree.html](https://gmlwjd9405.github.io/2018/08/12/data-structure-tree.html)

### 그래프와 트리의 차이점
<img src="./images/graph-vs-tree.png" width="70%" height="70%">

<div align=center>
:arrow_double_up:[Top](#1-data-structure)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#1-data-structure)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
</div>

### Binary Heap

<div align=center>
:arrow_double_up:[Top](#1-data-structure)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#1-data-structure)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
</div>

> - [https://gmlwjd9405.github.io/2018/05/10/data-structure-heap.html](https://gmlwjd9405.github.io/2018/05/10/data-structure-heap.html)

### Red-Black Tree

<div align=center>
:arrow_double_up:[Top](#1-data-structure)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#1-data-structure)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
</div>

> - []()

### B+ Tree

<div align=center>
:arrow_double_up:[Top](#1-data-structure)    :leftwards_arrow_with_hook:[Back](https://github.com/Do-Hee/tech-interview#1-data-structure)    :information_source:[Home](https://github.com/Do-Hee/tech-interview#tech-interview)
</div>

> - []()

---

## Reference
> - []()


## :house: [Home](https://github.com/Do-Hee/tech-interview)
