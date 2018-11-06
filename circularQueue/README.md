## Circular Queue

</br>

배열을 이용한 큐는 이미 사용한 영역인 head의 앞부분에 대해서 다시 활용을 못하기 때문에 메모리를 낭비한다는 단점이 있다. 그리고 이동 큐를 이용하여 큐가 다 찼을 경우 데이터들을 앞쪽으로 이동시켜 사용하는 방법이 있지만 남아있는 모든 데이터를 다 이동시켜야 한다는 불편한 작업을 수행해야 하기 때문에 그리 효율적으로 동작하지 못한다

tail과 head의 큐의 마지막 index에서 add와 poll이 발생했을 때, 공백과 포화를 막기위해 최초 큐 배열 생성시에 인자로 받은 maxSize+1 크기의 배열을 생성해준다.(배열의 마지막 공간은 임시공간이므로  데이터를 저장하는 큐의 크기는 maxSize-1 로 생각해야 된다는 것을 항상 기억)

</br>

</br>

### 사용예

출발 시간이 얼마 남지 않은 항공편

</br>

</br>

참조

http://hyeonstorage.tistory.com/264?category=578561

</br>

</br>

* 배열로 구현한 Circular Queue

```java
class CircularQueue {
    private int head;
    private int tail;
    private int maxSize;
    private Object[] arr;
    
    public CircularQueue(int maxSize){
        this.head = 0;
        this.tail = -1;
        // 실제 크기보다 하나 크게 지정한다 (공백과 포화를 막기 위함)
        this.maxSize = maxSize + 1;    
        this.arr = new Object[this.maxSize];
    }
    
    public boolean isEmpty(){
        return (head == tail + 1) || (head + maxSize - 1 == tail);
    }
    
    public boolean isFull(){
        return (tail == maxSize - 1) || (head + maxSize - 2 == tail);
    }
    
    public void insert(Object data){
        if(isFull()) {
        		throw new ArrayIndexOutOfBoundsException();
        }
        // tail 가 배열의 마지막이면 tail 포인터를 앞으로 돌린다.
        if(tail == maxSize - 1) {
            tail = -1;
        }
        arr[++tail] = data;
    }
    
    public Object peek(){
        if(isEmpty()) {
        		throw new ArrayIndexOutOfBoundsException();
        }
        return arr[head];
    }
    
    public Object remove(){
        Object data = peek();
        head++;
        // head의 다음 index가 배열크기+1 이면 처음으로 돌아간다
        if(head == maxSize){
            head = 0;
        }
        return data;
    }
}
```

<br>

<br>

* 배열로 구현한 Circular Queue 구현 code ver2

```java
class CircularQueue {
	private int head;
	private int tail;
	private int maxSize;
    private int size;
	private Object arr[];

	public CircularQueue(int maxSize) {
		this.head = 0;
		this.tail = 0;
		this.maxSize = maxSize + 1;
		arr = new Object[this.maxSize];
	}

	// 큐가 비어있는지 확인. 주의 !
	public boolean isEmpty() {
		return (head == tail);
	}

	// 큐가 가득차 있는지 확인
	public boolean isFull() {
		return ((tail + 1) % this.maxSize == head);
	}

	// 큐의 삽입 연산
	public void add(Object data) {
		if (isFull()) {
			throw new ArrayIndexOutOfBoundsException();
		}
		tail = (tail + 1) % (maxSize);
		arr[tail] = data;
        size++;
	}
    
    // 큐의 현재 front값 출력
	public Object peek() {
		if (isEmpty()) {
			throw new ArrayIndexOutOfBoundsException();
		}
		return arr[(head + 1) % maxSize];
	}

	// 큐의 삭제 후 반환 연산
	public Object poll() {
		Object data = peek();
		head = (head + 1) % maxSize;
        size--;
		return data;
	}
	
	public int size() {
		return size;
	}
}
```

