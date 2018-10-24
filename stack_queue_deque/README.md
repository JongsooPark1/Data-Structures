## Stack, Queue, Deque


### Stack

선형 자료구조의 일종으로 Last In First Out (LIFO, 후입선출). 즉, 나중에 들어간 원소가 먼저 나온다. 이것은 Stack의 가장 큰 특징이다. 차곡차곡 쌓이는 구조로 먼저 Stack에 들어가게 된 원소는 맨 바닥에 깔리게 된다. 그렇기 때문에 늦게 들어간 녀석들은 그 위에 쌓이게 되고 호출 시 가장 위에 있는 녀석이 호출되는 구조이다

![image0](stack.png)

</br>

### Queue

선형 자료구조의 일종으로 First In First Out (FIFO, 선입선출). 즉, 먼저 들어간 놈이 먼저 나온다. Stack 과는 반대로 먼저 들어간 원소가 맨 앞에서 대기하고 있다가 먼저 나오게 되는 구조이다. 참고로 Java Collection에서 Queue는 인터페이스이다

![image1](queue.png)

</br>

### Deque

응용된 Queue. 원소의 삽입 및 삭제가 맨 앞쪽과 뒤쪽에서 둘 다 가능하다. Stack과 Queue의 기능이 합쳐진 형태