## Queue

</br>

선형 자료구조의 일종으로 First In First Out (FIFO, 선입선출). 즉, 먼저 들어간 놈이 먼저 나온다. Stack 과는 반대로 먼저 들어간 원소가 맨 앞에서 대기하고 있다가 먼저 나오게 되는 구조이다. 참고로 Java Collection에서 Queue는 인터페이스이다

</br>

![image1](./queue.png)

</br>

</br>

### 사용예

* BFS
* 우선순위가 같은 작업 예약(인쇄 대기열)
* 콜센터 고객 대기 시간
* 프로세스 관리

</br>

</br>

### 구현

</br>

* Array 방식으로 Queue 구현 code

```java
class ArrayQueue{
	private int head;
	private int tail;
    private int size;
	private Object arr[];
	private int maxSize;
	
	public ArrayQueue(int maxSize) {
		this.head = 0;
		this.tail = -1;
		this.maxSize = maxSize;
		this.arr = new Object[maxSize];
	}
	
	public ArrayQueue() {
		this.head = 0;
		this.tail = -1;
		this.maxSize = 100;
        this.size = 0;
		this.arr = new Object[maxSize];
	}
	
	public boolean isEmpty() {
		return (head == tail + 1);
	}
	
	public boolean isFull() {
		return (tail == maxSize - 1);
	}
	
	public void add(Object data) {
		if (isFull()) {
			throw new ArrayIndexOutOfBoundsException();
		}
		arr[++tail] = data;
        size++;
	}
	
	public Object peek() {
		if (isEmpty()) {
			throw new ArrayIndexOutOfBoundsException();
		}
		return arr[head];
	}
	
	public Object poll() {
		Object data = peek();
		head++;
        size--;
		return data;
	}
	
	public int size() {
		return size;
	}
}
```

</br>

</br>

* Array 방식으로 Queue 구현 code ver2

```java
class ArrayQueue {
	private int head;
	private int tail;
	private int maxSize;
    private int size;
	private Object arr[];

	public ArrayQueue(int maxSize) {
		this.head = -1;
		this.tail = -1;
		this.maxSize = maxSize;
		this.arr = new Object[maxSize];
	}

	public boolean isEmpty() {
		return (head == tail);
	}

	// 큐가 가득 차있는지 확인
	public boolean isFull() {
		return (tail == maxSize - 1);
	}

	// 큐의 삽입 연산
	public void add(Object item) {
		if (isFull()) {
			throw new ArrayIndexOutOfBoundsException();
		}
        tail++;
		arr[tail] = item;
        size++;
	}

	// 현재 큐의 맨 앞의 값
	public Object peek() {
		if (isEmpty()) {
			throw new ArrayIndexOutOfBoundsException();
		}
		return arr[head + 1];
	}

	// 큐의 삭제 및 반환 연산
	public Object poll() {
		Object data = peek();
		head++;
        size--;
		return data;
	}
	
	public int size() {
		return size;
	}
}
```

<br>

<br>

* LinkedList 방식으로 Queue 구현 code

```java
public class ListQueue {
	// 큐는 head노드와 tail노드를 가진다.
	// 큐는 스택과 다르게 삽입과 삭제가 다른 부분에서 이루어지기 때문에 두개의 node를 갖는다
	private Node head;	// 나가는부분
	private Node tail;	// 들어오는부분
	private int size;

	public ListQueue() {
		this.head = null;
		this.tail = null;
		this.size = 0;
	}

	private class Node {
		// 노드는 data와 다음 노드를 가진다.
		private Object data;
		private Node nextNode;

		Node(Object data) {
			this.data = data;
			this.nextNode = null;
		}
	}

	// 큐가 비어있는지 확인
	public boolean isEmpty() {
		return (head == null);
	}

	// data를 큐의 tail에 넣는다.
	public void add(Object data) {
		Node newNode = new Node(data);
		if (isEmpty()) {
			tail = newNode;
			head = newNode;
		} else {
			// tail(들어오는 부분)만 생각
			tail.nextNode = newNode;
			tail = newNode;
		}
		size++;
	}

	// head의 데이터를 반환한다.
	public Object peek() {
		if (isEmpty())
			throw new ArrayIndexOutOfBoundsException();
		return head.data;
	}

	// head 를 큐에서 제거한다.
	// head(나가는 부분)만 생각
	public Object poll() {
		Object data = peek();
		size--;
		head = head.nextNode;
		// 이 부분 잊지 말기
		if (head == null) {
			tail = null;
		}
		return data;
	}

	public int size() {
		return size;
	}
}
```

