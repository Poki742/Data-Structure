# Data Structure

Java Data Structure<br>

## 1. 선형구조

### 연결 리스트(Linked List)
- 연결 리스트는 자료들을 반드시 연속적으로 배열시키지는 않는다.<br>
- 자료 항복의 순서에 따라 노드의 포인터를 이용하여 다음 자료를 연결시킨다.<br>
- 동적 메모리에 할당된 링크에 의해 연결된 유한 개수의 데이터 원소들<br>
- 
### 특징
- 링크 값을 변화시키는 것 만으로 노드의 삽입 삭제가 용이하다.<br>
- 기억공간이 연속적으로 놓여 있지 않아도 저장이 가능하다.<br>
- 연결을 위한 링크(포인터) 부분이 필요하기 떄문에 순차 리스트에 비해<br>기억 공간 이용 효율이 좋지 않다.<br>
- 중간 노드 연결이 끊어지면 그 다음 노드를 찾지 못한다.<br>
- 희소 행렬을 링크드 리스트로 표현하면 기억장소가 절약된다.<br>
- 트리를 표현할 떄 가장 적합한 자료이다.<br>
![image](https://user-images.githubusercontent.com/126844692/226499753-167c2edc-ce25-4c0f-b523-c93e2d697ade.png)<br>

### 노드(node)
자료와 포인터를 갖고 있는 것을 노드(node)라고 한다.<br>
![image](https://user-images.githubusercontent.com/126844692/226500264-3a170c34-f24b-4b3b-81d2-6519acaa5256.png)<br>

### 희소 행렬
희소 행렬은 요소 중 많은 항들이0(영)으로 되어 있는 형태로 기억 장소를<br>절약하기 위해 링크드 리스트를 이용하여 저장한다.<br><br>
![image](https://user-images.githubusercontent.com/126844692/226500474-9a221ed7-d2a7-4afb-8c91-3c29ba89ae2a.png)<br>

### 자바 이클립스(Java Eclipse)
![image](https://user-images.githubusercontent.com/126844692/226522766-cade90b1-af43-4d8a-82e4-8ed5b7700de2.png)<br>
### 스택(Stack)
리스트의 한쪽 끝으로만 자료의 삽입 및 삭제가 이루어지는 구조로<br>
먼저 삽입된 자료가 맨 나중에 삭제가 되는 후입 선출로 Last In First Out 방식이다.<br>
![image](https://user-images.githubusercontent.com/126844692/226811115-d870bed8-9add-4d7b-8030-9d44fa34b820.png)<br><br>
![image](https://user-images.githubusercontent.com/126844692/226811741-75f4e60e-77e0-4b82-a5da-0dd241062536.png)<br>

### 큐(Queue)
일상생활에서 은행에 들어온 순서대로 번호표를 뽑고 번호표 순서대로<br>
먼저 온 고객부터 처리해 주는 것과 같이 선입선출 형태의 구조<br><br>

큐는 스택과 마찬가지로 삽입과 삭제의 위치와 방법이 제한되어 있는 자료구조이지만<br>
한쪽 끝에서는 삽입 작업이 이루어지고 반대쪽 끝에서는 삭제 작업이 이루어지는 자료구조이다.<br>

### 큐의 특징
1) 데이터가 삽입된 순서대로 삭제되는 선입선출(FIFO, First-In-First-Out)  구조입니다.<br><br>
2) 한쪽 끝을 front로 정하여 삭제 연산만 수행하도록 하고<br>
다른 쪽 끝은 rear로 정하여 삽입 연산만 수행하도록 제한하여 만든 자료구조입니다.<br><br>

front 원소는 가장 먼저 큐에 들어온 첫 번째 원소이고, 리어 원소는 가장 늦게 들어온 마지막 원소입니다.<br>
![image](https://user-images.githubusercontent.com/126844692/226807680-b56779cd-ff8c-4f1f-af70-00d8c30bc6af.png)<br>

### 자바 이클립스(Java Eclipse)

#### 큐 생성<br>
![image](https://user-images.githubusercontent.com/126844692/226807890-7ec895fa-73eb-45ec-acf5-68a22c8568e7.png)<br><br>

#### 공백 상태 검사
![image](https://user-images.githubusercontent.com/126844692/226808078-ac1e9ea0-116c-4fa0-a03c-7288fff148cc.png)<br><br>

#### 포화 상태 검사
![image](https://user-images.githubusercontent.com/126844692/226808190-836d283a-fe19-414e-9118-917d55cfa715.png)<br><br>

#### 삽입 연산(enQueue)
![image](https://user-images.githubusercontent.com/126844692/226808319-831bfdef-8a16-42a1-982d-7af453520d40.png)<br><br>

#### 삭제 연산(deQueue)
![image](https://user-images.githubusercontent.com/126844692/226808407-7851acab-9fc1-44e5-a992-48d582871b3a.png)<br><br>

#### 코딩

package test;<br>

public class IntQueue {<br>
	private int[] que;<br>
	private int capacity;<br>
	private int front;<br>
	private int rear;<br>
	private int num;<br>
	
	public class EmptyIntQueueException extends RuntimeException {
		public EmptyIntQueueException() {
			
		}
	}
	
	public class OverflowIntQueueException extends RuntimeException {
		public OverflowIntQueueException() {
			
		}
	}
	
	public IntQueue(int maxlen) {
		num = front = rear = 0;
		capacity = maxlen;
		try {
			que = new int[capacity];
		} catch (OutOfMemoryError e) {
			capacity = 0;
		}
	}
	
	public int enque(int x) throws OverflowIntQueueException {
		if(num >= capacity)
			throw new OverflowIntQueueException();			// 큐가 가득 찼음
		que[rear++] = x;
		num++;
		if(rear == capacity)
			rear = 0;
		return x;
	}
	
	public int deque() throws EmptyIntQueueException {
		if(num <= 0)
			throw new EmptyIntQueueException();				//큐가 비어있음
		int x = que[front++];
		num--;
		if(front == capacity)
			front = 0;
		return x;
	}
	public static void main(String[] args) {
		// TODO Auto-generated method stub

	}
}

### 이진 트리(binary tree)
이진 트리(Binary Tree)는 노드(Node)들이 부모-자식 관계로 구성된 트리(Tree) 자료구조의 일종입니다.<br>
각 노드는 최대 두 개의 자식 노드를 가지며, 이진 트리는 빠른 탐색을 위해 사용되며, 다양한 문제에 적용될 수 있습니다.<br><br>

![image](https://user-images.githubusercontent.com/126844692/227128141-64131edf-5766-4b69-ac9c-103cfc6ad64c.png)<br>

#### 1) 포화 이진 트리(Perfect binary tree)
1) 모든 레벨의 노드가 가득 차있는 트리이다.<br>
1-1) 노드가 2개의 자식을 가지고 있다.<br>
1-2) 차수(Degree) 가 2 이다.<br><br>
2) 모든 노드가 가득 차있어 단말 노드부터 루트노드까지의 높이가 같다.<br>
2-1) 노드의 개수 n = 2^h - 1, h 는 높이<br>

![image](https://user-images.githubusercontent.com/126844692/227129044-eb0acb73-cea7-41fa-9cb4-645592e723ed.png)<br>

A는 B 와 C를 자식으로 가져 꽉 차있고, B는 D 와 E, C는 F 와 G를 자식으로 가져 꽉 차있어 모든 레벨이 가득 차 있다고 할 수 있다.<br>
따라서 포화 이진 트리가 되는것을 알 수 있다.

#### 2) 완전 이진 트리(Complete binary tree)

1) 완전 이진 트리는 마지막 레벨 바로 전까지는 꽉 차있다 마지막 레벨에서 왼쪽부터 차례대로 채워져 있는 트리이다.<br>
2) 완전 이진 트리의 개념은 힙(heap)과 관련이 있다.<br>
3) 노드의 개수 n < 2^h -1, h 는 높이<br>

![image](https://user-images.githubusercontent.com/126844692/227129694-b9674466-bb78-445d-aa41-3eba787ae665.png)<br>

왼쪽의 트리는 왼쪽부터 노드가 채워져있기 때문에 완전 이진트리라고 할 수 있지만,<br>
오른쪽의 트리는 레벨 3에서 왼쪽부터 노드가 채워져있지 않기 때문에 완전 이진 트리라고 할 수 없다.<br>

#### 3) 편향 이진 트리(Skewed binary tree)

1) 왼쪽 또는 오른쪽으로 편향되게 채워져있는 트리이다.<br>
2) 각각의 높이에서 1개의 노드만 있다.<br>
2-1) 따라서 왼쪽 혹은 오른쪽으로만 편향되게 된다.<br>
3) h <= 노드의 개수 n <= 2^h - 1, h 는 높이<br>
3-1) 편향 이진 트리에서 노드의 개수 n은 위 식의 최솟값 h와 같다.<br>
3-2) 최댓값은 포화 이진 트리와 같다.<br>

![image](https://user-images.githubusercontent.com/126844692/227130102-6702990b-6959-452e-a2da-a37be1e5d178.png)<br>

왼쪽의 트리에서 A는 왼쪽 자식으로 B를 가지고, B는 왼쪽 자식으로 D를 가지고 있어 왼쪽 편향 트리이다.<br>
오른쪽의 트리에서 A는 오른쪽 자식으로 B를 가지고, B는 오른쪽 자식으로 D를 가지고 있어 오른쪽 편향 트리이다.<br>

#### 4) 정 이진 트리(Full binary tree)

1) 정 이진 트리는 모든 노드가 0 개 또는 2개의 자식 노드만을 갖는 트리이다.<br>
2) 2 * height + 1 <= 노드의 개수 n <= 2^(height+1) - 1<br>

![image](https://user-images.githubusercontent.com/126844692/227130767-44289cdc-e1ab-44d9-be6e-8fbf9eea348a.png)<br>

A는 B 와 C로 2개의 자식 노드, B는 D와 E로 2개의 자식 노드,<br>
C는 0개의 자식 노드를 가지고 있기 때문에 정 이진 트리가 된다.<br>

#### 5) 균형 이진 트리(Balanced binary tree)

1) 균형 이진 트리는 모든 노드의 왼쪽과 오른쪽 서브 트리의 높이가 1 이상 차이가 나지 않는 트리이다.

![image](https://user-images.githubusercontent.com/126844692/227130992-c5b5aa40-2b48-4102-b81a-1c617951110f.png)<br>

왼쪽의 트리들은 왼쪽과 오른쪽의 서브 트리의 높이가 1 이상 차이가 나지 않는것을 볼 수 있다.<br>
하지만 오른쪽의 트리들은 왼쪽과 오른쪽의 서브 트리의 높이가 1이상 차이가 나기 때문에 균형 이진 트리라고 할 수 없다.<br>


