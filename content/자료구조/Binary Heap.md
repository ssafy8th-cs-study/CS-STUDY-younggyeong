# Heap
힙이란 트리 기반 자료구조로, 거의 완전한 트리이다. 힙 속성이란, 최대힙일 경우 부모노드는 반드시 자식노드보다 값이 큰 것이 법칙이다.  
따라서 최상위 노드는 최대값을 갖게 되고 우선순위 큐를 구현하는데 적합한 자료구조이다.  
한 가지 고려해야 할 점은 힙은 부모와 자식 노드간의 관계만이 정의되어 있고, 형제 또는 사촌노드 간의 우선순위는 정해진 것이 없다.

# Binary Heap
이진 힙은 완전 이진트리 형태인 힙이다. 

## 최소 힙
![image](https://user-images.githubusercontent.com/54929520/184638669-d67aa91c-6324-4de9-bd36-3746298eb0bd.png)  
부모 노드 값 < 자식 노드 값 : **루트가 최소값**

## 최대 힙
 ![image](https://user-images.githubusercontent.com/54929520/184638807-2097d9bc-0770-4b76-b49a-0ef958c51c3a.png)  
 부모 노드 값 > 자식 노드 값 : **루트가 최대값**
 
## 힙의 연산

#### 삽입
1. 원소를 힙의 가장 마지막 노드에 추가  
![image](https://user-images.githubusercontent.com/54929520/184639182-f7137f8f-59c3-4f2b-b719-9e581a5855e5.png)  
2. 추가한 원소를 부모와 비교하여 맞지 않으면 위치를 교환. 루트까지 계속 반복.  
![image](https://user-images.githubusercontent.com/54929520/184639410-650ff27b-c7a8-447c-b6b7-0c45f22e354f.png)
![image](https://user-images.githubusercontent.com/54929520/184639431-426f72c2-dc90-4603-90c3-6f2a618896c6.png)

#### 삭제
1. 루트 노드를 삭제  
![image](https://user-images.githubusercontent.com/54929520/184639491-e19b77e4-d8eb-4d56-b994-7e6bd2690570.png)  
2. 마지막 노드를 루트로 이동하고 루트를 자식노드와 비교하며 힙 트리가 완성될까지 이를 반복.  
![image](https://user-images.githubusercontent.com/54929520/184639623-e25c2ce3-169e-4528-859a-62ee56543c8c.png)
![image](https://user-images.githubusercontent.com/54929520/184639640-936cd06f-6c50-4673-9741-fe20a46ff094.png)

