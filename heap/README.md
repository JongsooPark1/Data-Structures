## Heap

</br>

- 힙(heap)은 **완전이진트리(Complete binary tree)**를 기본으로 한 자료구조(tree-based structure)

- 시간 복잡도 : 삽입 - logN, 삭제 - logN

- 일반적으로 **배열**을 사용하여 **구현**한다.

- 완전이진트리는 최댓값 및 최솟값을 찾아내는 연산을 빠르게 하기 위해 고안

- 다음과 같은 힙 속성(property)을 만족한다.

  - A가 B의 부모노드(parent node) 이면, A의 키(key)값과 B의 키값 사이에는 대소관계가 성립한다.

  - 형제 노드끼리는 비교 불필요하다.

  - 힙에서의 부모 노드와 자식 노드의 관계

    왼쪽 자식의 인덱스 = (부모의 인덱스) * 2

    오른쪽 자식의 인덱스 = (부모의 인덱스) * 2 + 1

    부모의 인덱스 = (자식의 인덱스) / 2



* 우선 순위 큐를 만들기 위해 만들어진 자료 구조

* 최대힙(max heap) : 부모 노드의 키 값이 자식 노드의 키 값보다 크거나 같은 완전 이진 트리

  최소힙(min heap) : 부모 노드의 키 값이 자식 노드의 키 값보다 작거나 같은 완전 이진 트리

</br>



![heapkinds](./heapkinds.jpg)

</br>

참조

https://gmlwjd9405.github.io/2018/05/10/data-structure-heap.html

</br>

* 배열을 이용한 Heap 구현

```java
public class Heap {
	private static final int Max_Size = 101;
	public int arr[];
	private int size;

	public Heap() {
		arr = new int[Max_Size];
		Arrays.fill(arr, Integer.MIN_VALUE);
		size = 0;
	}

	public boolean isEmpty() {
		return (size == 0);
	}

	public boolean isFull() {
		return (size == Max_Size - 1);
	}

	private void swap(int a, int b) {
		int temp = arr[a];
		arr[a] = arr[b];
		arr[b] = temp;
	}

	public void insert(int data) {
        if (isFull()) {
			throw new ArrayIndexOutOfException();
		}
		size++;
		int temp_index = size;
		arr[temp_index] = data;

		while (temp_index > 1) {
			int root = temp_index / 2;
			if (arr[temp_index] > arr[root]) {
				swap(root, temp_index);
				temp_index = temp_index / 2;
			} else {
				break;
			}
		}
	}

	public int delete() {
        if (isEmpty()) {
			throw new ArrayIndexOutOfBoundsException();
		}
		int start = 1;
		int max = arr[start];
		arr[start] = arr[size];
		arr[size] = Integer.MIN_VALUE;
		size--;
		while (size > 0) {
			if ((arr[start] > arr[start * 2]) && arr[start] > arr[start * 2 + 1]) {
				break;
			} else if (arr[start * 2] > arr[start * 2 + 1]) {
				swap(start, start * 2);
				start = start * 2;
			} else {
				swap(start, start * 2 + 1);
				start = start * 2 + 1;
			}
		}
		return max;
	}
	
	public int size() {
		return size;
	}
}
```

