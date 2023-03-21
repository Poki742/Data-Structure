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
