# Data Structure
Java Data Structure<br>
## 1. 선형구조
### 연결 리스트(Linked List)
- 연결 리스트는 자료들을 반드시 연속적으로 배열시키지는 않는다.<br>
- 자료 항복의 순서에 따라 노드의 포인터를 이용하여 다음 자료를 연결시킨다.<br>
- 동적 메모리에 할당된 링크에 의해 연결된 유한 개수의 데이터 원소들<br>
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
### for문
![image](https://user-images.githubusercontent.com/126844692/226522766-cade90b1-af43-4d8a-82e4-8ed5b7700de2.png)<br>
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

### 자바 이클립스
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




