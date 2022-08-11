# Tree
![image](https://user-images.githubusercontent.com/54929520/184080761-d368edb5-7fea-4b82-a882-836739160745.png)

노드로 이루어진 자료구조이다. 컴퓨터의 directory구조가 트리구조의 대표적인 예이다.
![image](https://user-images.githubusercontent.com/54929520/184080800-3b17087a-b8db-4701-a21c-7571051d6831.png)

## 트리 관련 용어
![image](https://user-images.githubusercontent.com/54929520/184080935-945c778a-7240-46d6-a1ed-c9f9420c59a2.png)

- 루트 노드(root node): 부모가 없는 최상위 노드 (A)
- 단말 노드(leaf node): 자식이 없는 노드 (H, I, E, J, G)
- 크기(size): 트리에 포함된 모든 노드의 개수 
- 깊이(depth): 루트 노드로부터의 거리 (A는 0, 그 밑에 B와 C로 나누어지니 B와 C의 깊이는 1, 또 그 아래의 D, E, F, G는 2, ...)
- 높이(height): 깊이 중 최댓값(위의 깊이 0, 1, 2중에 가장 높은 값. 즉, 루트 노드로부터 가장 멀리 있는, 단말 노드 중에 가장 깊은 노드.)
- 차수(degree): 각 노드의 간선 개수(A에서 B와 C로 나눠지니까 A의 차수는 2가 되며, E에서는 단말 노드이므로 차수는 0이 된다.)
- 트리의 차수(degree of tree): 트리의 최대 차수
- 트리의 높이(height): 루트 노드에서 가장 깊숙히 있는 노드의 깊이

## 트리의 특징
1. 그래프의 한 종류로 최소 연결 트리라고도 불린다.
2. 트리는 계층 모델이다.
3. 트리는 비순환그래프의 한 종류이다. 즉, 사이클이 없다.
4. 루트에서 한 노드로 가는 경로는 유일하다.

## 트리의 종류
#### 편향 이진 트리
![image](https://user-images.githubusercontent.com/54929520/184081546-8219df5f-3c69-4d98-bd06-4fc2d8b5ff40.png)

하나의 차수로만 이루어져 있는 트리를 편향이진트리라고 한다.

#### 포화 이진 트리
![image](https://user-images.githubusercontent.com/54929520/184081623-67655bb8-6660-4b8f-b163-bed95790bab4.png)

리프 노드를 제외한 모든 노드의 차수가 2개인 트리이다.

#### 완전 이진 트리
![image](https://user-images.githubusercontent.com/54929520/184081667-6465cac4-8d4f-4d13-a977-e654f0b092b2.png)

마지막 레벨은 꽉 차있지 않아도 되지만 노드가 왼쪽에서부터 채워진다.

#### 이진 탐색 트리
탐색을 위한 이진 트리 기반의 자료구조이다.
left node에는 **부모노드보다 작은 값**이 저장된다.
right node에는 **부모노드와 값이 같거나 큰 값**이 저장된다.
모든 노드는 **중복된 값을 가지지 않는다**.
