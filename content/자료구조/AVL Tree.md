# AVL Tree
AVL 트리는 이진 탐색트리가 편향 트리로 구성될 경우 특정 값을 찾을 때 최악의 경우, O(N)의 시간이 걸리는것을 해결하기 위한 트리이다.  
![image](https://user-images.githubusercontent.com/54929520/184641003-24ac3fc3-b6dd-4dc5-805a-a8b6b7755af3.png)  
예를 들어, 해당 이미지에서 6을 찾으려면 모든 노드를 참색해야 찾을 수 있다.  
![image](https://user-images.githubusercontent.com/54929520/184641042-c765f7f1-080c-4e55-aec3-a95b83bb46eb.png)  
이를 위 그림처럼 균형을 유지하는 AVL 트리로 재구성 하면 어떤 노드든 O(log N)에  탐색 할 수 있다.  
### Balance Factor(BF)
AVL트리는 균형이 무너졌는지에 대해 판단할 때 BF를 사용한다. BF의 공식은 다음과 같다.  
BF = K의 왼쪽 서브트리 높이 - K의 오른쪽 서브트리 높이.  
![image](https://user-images.githubusercontent.com/54929520/184641834-d134e75a-c0e0-409f-9221-c402eb705906.png)  
AVL트리의 **모든 노드의 BF는 -1,0,1 중 하나**여야 한다.

## AVL트리의 특징
1. **이진 탐색 트리**의 속성을 갖는다.
2. 왼쪽, 오른쪽 서브 트리의 **높이 차이가 최대 1**이다.
3. 높이 차이가 1보다 커지면 **회전**을 통해 균형을 맞춘다.
4. 삽입, 검색, 삭제의 시간복잡도가 **O(log N)**이다.

## AVL 트리의 회전 과정

### 우회전
![image](https://user-images.githubusercontent.com/54929520/184642116-d0dc6d4f-56da-4d8e-97a8-ab36868e49a7.png) 
1. y노드의 오른쪽 자식 노드를 z노드로 변경한다.  
2. z노드 왼쪽 자식 노드를 y노드의 오른쪽 서브트리(T2)로 변경한다.  

### 좌회전
![image](https://user-images.githubusercontent.com/54929520/184643272-56b1a3ed-c35d-470e-8626-a02fb7216239.png)  
1. y노드의 왼쪽 자식 노드를 z노드로 변경한다.  
2. z노드 오른쪽 자식노드를 y노드의 왼쪽 서브트리(T2)로 변경한다.  

### LL(LEFT LEFT) CASE
![image](https://user-images.githubusercontent.com/54929520/184643698-d731146c-035d-462b-acc5-36b36ae76987.png)  
y는 z의 왼쪽 자식 노드이고, x는 y의 왼쪽 자식 노드인 경우 우회전을 수행하여 균형을 맞춘다.  

### RR(RIGHT RIGHT) CASE
![image](https://user-images.githubusercontent.com/54929520/184643806-67996adb-1e63-4c74-8abb-187421de5672.png)  
y는 z의 오른쪽 자식 노드이고, x는 y의 오른쪽 자식 노드인 경우 left rotation을 수행하여 균형을 맞춘다.  

### LR(LEFT RIGHT) CASE
![image](https://user-images.githubusercontent.com/54929520/184646188-6a5ee1c0-fe51-4205-a535-26133d82c57d.png)  
B를 기준으로 좌회전을 한 후 A를 기준으로 우회전을 한다.

### RL(RIGHT LEFT) CASE
![image](https://user-images.githubusercontent.com/54929520/184646321-9f1a4fe6-abc7-4479-b241-2538cb0620e5.png)  
B를 기준으로 우회전을 한 후 A를 기준으로 좌회전을 한다.

## AVL 트리의 삽입, 삭제 
AVL트리의 삽입 삭제 방식은 이진 탐색 트리와 같다. 하지만 높이 균형을 유지하기 위한 회전과정이 추가된다.
