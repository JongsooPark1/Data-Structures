## Deque

</br>

응용된 Queue. 원소의 삽입 및 삭제가 앞쪽과 뒤쪽에서 둘 다 가능하다. Stack과 Queue의 기능이 합쳐진 형태



### 구현

</br>

* LinkedList로 Deque구현 code

```java
class ListDeque {
	private Node head;
	private Node tail;
	private int size;

	public ListDeque() {
		this.head = null;
		this.tail = null;
		this.size = 0;
	}

	private class Node {
		private Node left;
		private Node right;
		private Object data;

		private Node(Object data) {
			this.left = null;
			this.right = null;
			this.data = data;
		}
	}

	public boolean isEmpty() {
		return (head == null);
	}

	public void addHead(Object data) {
		Node newNode = new Node(data);
		if (isEmpty()) {
			head = newNode;
			tail = newNode;
		} else {
            // 주의!!!
			newNode.right = head;
			head.left = newNode;
			head = newNode;
		}
		size++;
	}

	public void addTail(Object data) {
		Node newNode = new Node(data);
		if (isEmpty()) {
			head = newNode;
			tail = newNode;
		} else {
            // 주의!!!
			newNode.left = tail;
			tail.right = newNode;
			tail = newNode;
		}
		size++;
	}

	public Object peekHead() {
		if (isEmpty()) {
			throw new ArrayIndexOutOfBoundsException();
		}
		return head.data;
	}

	public Object peekTail() {
		if (isEmpty()) {
			throw new ArrayIndexOutOfBoundsException();
		}
		return tail.data;
	}

	public Object pollHead() {
		Object data = peekHead();
		head = head.right;
		if (head == null) {
			tail = null;
		} else {
            // else 부분 주의 ! head가 null이 되면 null.left는 존재 하지 않기 때문에 null error
			head.left = null;
		}
		size--;
		return data;
	}

	public Object pollTail() {
		Object data = peekTail();
		tail = tail.left;
		if (tail == null) {
			head = null;
		} else {
            // else 부분 주의 ! tail이 null이 되면 null.right는 존재 하지 않기 때문에 null error
			tail.right = null;			
		}
		size--;
		return data;
	}
	
	public int size() {
		return size;
	}
}
```

