# B- 트리

모든 **리프노드들이 같은 레벨**을 가질 수 있도록 하는 트리이다. 또한 정렬된 순서를 보장하므로 빠른 검색이 가능하다.
![image](https://user-images.githubusercontent.com/54929520/184877026-10dfe585-a038-4634-875a-2730bfc51840.png)


B-트리는 다음과 같은 특징을 갖는다.
1. node의 key 수가 k개라면, 자식노드의 수는 k+1개이다.
2. 노드에는 최대 M−1개 부터 [M/2]−1개의 키가 포함된다.
3. 자식 node들의 key는 현재 노드의 key를 기준으로 크기순으로 나뉜다.
4. root 노드는 항상 2개 이상의 자식노드를 갖는다.
5. M차 트리일 때, 루트노드와 리프노드를 제외한 모든 노드는 최소 ⌈M/2⌉, 최대 M개의 서브트리를 갖는다.
6. 모든 리프노드의 LEVEL은 같다.

## B- 트리의 검색
![image](https://user-images.githubusercontent.com/54929520/184877734-903f486d-bcc8-42f4-8a37-82bebef9e43a.png)
![image](https://user-images.githubusercontent.com/54929520/184877747-2ba09a0a-1374-4ee9-ac9e-09d21b3aeca3.png)

## B- 트리의 삽입
### case 1 : 분할이 일어나지 않는 경우
![image](https://user-images.githubusercontent.com/54929520/184879154-e73fad23-68c6-4eec-8eec-d3d5779bd032.png)

### case 2 : 분할이 일어나는 경우
노드가 담을 수 있는 key 개수를 초과하는 경우 중앙값에서 분할을 수행하여 부모노드로 병합되거나 생성된다.
![image](https://user-images.githubusercontent.com/54929520/184879331-181c58dc-b4d3-48bf-9d05-ba3ce4093bc9.png)
![image](https://user-images.githubusercontent.com/54929520/184879353-2930f683-ad9d-4d04-a7a4-e812e94e6965.png)
![image](https://user-images.githubusercontent.com/54929520/184879366-ea95ac96-93c8-44a3-9426-69152b189891.png)

## B- 트리의 삭제
## case 1. 삭제할 키가 리프에 있는 경우
### case 1.1 현재 노드의 키 개수가 최소 키 개수보다 크면,
![image](https://user-images.githubusercontent.com/54929520/184880028-54ce6033-9fbb-4355-b085-5b9566ce3a23.png)

### case 1.2 왼쪽 또는 오른쪽 형제 노드에 여유 키가 있다면,
![image](https://user-images.githubusercontent.com/54929520/184880123-ccb858cf-66b1-4bfe-8897-54b4533faa36.png)

### case 1.3 왼쪽, 오른쪽 노드에 최소개수의 키가 있고 부모노드의 키가 최소개수 이상이면,
![image](https://user-images.githubusercontent.com/54929520/184880209-ee7fa644-3d66-48a8-ba96-f4cf9d1ab07a.png)

## case 2. 삭제할 키가 노드 중간에 있고, 노드나 자식의 키가 최소 키 수보다 많다면,
![image](https://user-images.githubusercontent.com/54929520/184881086-5ff4e2d4-c199-4eb7-b5c5-badd9cfbfd32.png)  
이 후 case 1의 조건으로 변환

## case 3. 삭제할 키가 노드 중간에 있고 노드, 자식노드의 키 개수가 모두 최소 키 개수일 경우
모든 노드의 키개수가 최소이므로 트리의 높이가 줄어들어 **재구조화**가 일어나는 케이스이다.
1. k를 삭제하고, k의 양쪽 자식을 병합하여 하나의 노드로 만듭니다.
2. k의 부모key를 인접한 형제 노드에 붙입니다. 이후, 이전에 병합했던 노드를 자식노드로 설정합니다.
3. 해당 과정을 수행하였을 때 부모노드의 개수가 에 따라 이후 수행 과정이 달라집니다.  
   3-1. 만일 새로 구성된 인접 형제노드의 key가 최대 key 개수를 넘어갔다면, 삽입 연산의 노드 분할 과정을 수행합니다.  
   3-2. 만일 인접 형제노드가 새로 구성되더라도 원래 k의 부모 노드가 최소 key의 개수보다 작아진다면, 부모 노드에 대하여 2번 과정부터 다시 수행합니다.  
![image](https://user-images.githubusercontent.com/54929520/184882155-ebac63de-dcf0-45f9-a1b6-a0e58478fa92.png)
(해당 그림에서 10노드는 17이다. 오타임)
![image](https://user-images.githubusercontent.com/54929520/184882848-23398ba8-c1a6-439e-8527-d8e78361e0f6.png)
