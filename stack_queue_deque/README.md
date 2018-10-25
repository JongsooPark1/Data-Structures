## Stack, Queue, Priority Queue, Deque, Heap


### Stack

선형 자료구조의 일종으로 Last In First Out (LIFO, 후입선출). 즉, 나중에 들어간 원소가 먼저 나온다. 이것은 Stack의 가장 큰 특징이다. 차곡차곡 쌓이는 구조로 먼저 Stack에 들어가게 된 원소는 맨 바닥에 깔리게 된다. 그렇기 때문에 늦게 들어간 녀석들은 그 위에 쌓이게 되고 호출 시 가장 위에 있는 녀석이 호출되는 구조이다

![image0](stack.png)

</br>

### Queue

선형 자료구조의 일종으로 First In First Out (FIFO, 선입선출). 즉, 먼저 들어간 놈이 먼저 나온다. Stack 과는 반대로 먼저 들어간 원소가 맨 앞에서 대기하고 있다가 먼저 나오게 되는 구조이다. 참고로 Java Collection에서 Queue는 인터페이스이다

![image1](queue.png)

</br>

### Priority Queue

일반적인 큐는 FIFO 자료구조 이기 때문에 먼저 들어온 데이터를 먼저 내보냈다면, 우선순위 큐는 우선순위가 높은 데이터를 먼저 내보내는 자료구조

새로운 노드를 삽입하면 우선순위에 맞게 위치에 삽입 (Enqueue)하고, 제거를 할 때는 가장 우선 순위가 높은 맨 앞에 노드를 빼면서 삭제(Dequeue)한다



</br>

### Deque

응용된 Queue. 원소의 삽입 및 삭제가 맨 앞쪽과 뒤쪽에서 둘 다 가능하다. Stack과 Queue의 기능이 합쳐진 형태



</br>

### Heap

- 힙(heap)은 **완전이진트리(Complete binary tree)**를 기본으로 한 자료구조(tree-based structure) (시간복잡도 : O(log N))
- 일반적으로 **배열**을 사용하여 **구현**한다.
- 완전이진트리는 최댓값 및 최솟값을 찾아내는 연산을 빠르게 하기 위해 고안
- 다음과 같은 힙 속성(property)을 만족한다.
  - A가 B의 부모노드(parent node) 이면, A의 키(key)값과 B의 키값 사이에는 대소관계가 성립한다.
  - 형제 노드끼리는 비교 불필요하다.



</br>

참조

https://gmlwjd9405.github.io/2018/05/10/data-structure-heap.html

