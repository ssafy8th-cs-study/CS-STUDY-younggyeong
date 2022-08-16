# RedBlack Tree
![image](https://user-images.githubusercontent.com/54929520/184868042-6630e128-18f9-4366-b676-047c98990ece.png)

레드-블랙트리는 AVL트리와 마찬가지로, 이진탐색트리의 편향의 문제점을 해결하기 위해 고안된 트리이다. 레드-블랙트리는 자가균형 이진 탐색 트리로 다음과 같은 조건을 만족한다.  

1. 모든 노드는 **빨간색 혹은 검은색**이다.
2. **루트노드는 검은색**이다.
3. 모든 **리프노드(NIL)들은 검은색**이다.
4. **빨간색 노드의 자식은 검은색**이다. == NO DOUBLE RED
5. 모든 리프노드에서 **BLACK DEPTH는 같다**. BLACK DEPTH란 루트노드 까지 가는 경로에서 만나는 검은색 노드의 개수이다.  

## 레드-블랙트리 용어
1) NIL node
실제 코드에서 구현하지 않는 **완전 가상의 노드**이다.
2) internal nodes
NIL이 아닌 모든 나머지노드.

## 삽입
노드를 삽입할 때에는 무조건 레드노드로 삽입하게 된다.
![image](https://user-images.githubusercontent.com/54929520/184868567-31478d7b-1963-4af6-89a2-ba91343aa371.png)

에서 6을 삽입하면
![image](https://user-images.githubusercontent.com/54929520/184868598-86dcf357-596a-403a-930b-44eb82b7d611.png)

이진트리의 성질로 인해 위 그림처럼 삽입이 된다. 하지만 위에 말한 **3번조건(Double red)를 위반**하므로 기술이 필요하다.

### 1. 삽입된 노드의 삼촌노드가 검정이면 **Restructing**.
![image](https://user-images.githubusercontent.com/54929520/184869687-3bde628c-25a7-4bcc-b1f1-f27eda059fed.png)

1) 삽입된 노드와 그 부모, 그 조부모 노드를 오름차순으로 정렬합니다.
2) **가운데 값을 부모**로 만든 뒤, 나머지 둘을 자식으로 만들어줍니다.
![image](https://user-images.githubusercontent.com/54929520/184869851-04015129-907a-4e6f-aeb0-9752560aef75.png)
3) 이때 **부모는 검은색 노드, 두 자식들은 빨간색 노드**로 만듭니다.
![image](https://user-images.githubusercontent.com/54929520/184869889-d0a57cb9-0a11-4245-bdc0-590e422a23e1.png)

### 2. 삽입된 노드의 삼촌노드가 빨간색이면 **Recoloring**.
![image](https://user-images.githubusercontent.com/54929520/184870301-16d96e52-c747-45fe-8d99-a18937554863.png)
**노드 17이 삽입되었다고 가정하자.**

1) 현재 삽입된 노드의 부모와 삼촌을 검은색으로 만든 후, 조부모를 빨간색으로 만들어줍니다.
![image](https://user-images.githubusercontent.com/54929520/184870364-ca2f5acc-64f1-4b92-a6a0-67c95c45559e.png)


2) 만약 조부모가 루트 노드가 아니라면, 조부모의 부모가 빨간색일 수 있고, 이는 다시 Double Red가 발생할 수 있다. 이를 해결해준다.
![image](https://user-images.githubusercontent.com/54929520/184870420-48a2b784-46d8-4b8b-9eb6-58ca96899f7e.png)

## 삭제
1. 간단하게 해결할 수 있는 경우
![image](https://user-images.githubusercontent.com/54929520/184870819-c40c7f93-2a8b-47ff-9ad4-b5c8cec5fab4.png)  
- **m이 레드인 경우** 그냥 삭제한다.
- **m이 블랙이고 자식이 레드**이면 삭제 후 자식을 블랙으로 바꾸면 된다.

2. 까다로운경우는 **m과 x가 블랙**인경우이다. 이 경우 m을 삭제하면 **5번조건(모든 리프노드의 black depth는 같다)** 을 위반한다.  

![image](https://user-images.githubusercontent.com/54929520/184871109-15b400d0-5520-404d-9031-b1e084605fab.png)  

**Case 1 : p가 레드 (s는 항상 블랙이므로) <l, r의 색상>에 따라**  
- Case 1-1 <블랙, 블랙>
- Case 1-2 <*, 레드>
- Case 1-3 <레드, 블랙>


**Case 2 : p가 블랙 <s, l, r의 색상>에 따라-**
- Case 2-1 <블랙, 블랙, 블랙>
- Case 2-2 <블랙, *, 레드>
- Case 2-3 <블렉, 레드, 블랙>
- Case 2-4 <레드, 블랙, 블랙>

#### case 1-1
![image](https://user-images.githubusercontent.com/54929520/184872206-fb3e8ad5-fd29-4e93-8830-622002841515.png)  
단순히 p와 s의 색상을 맞바꾼다.

#### case *-2
![image](https://user-images.githubusercontent.com/54929520/184872699-3fd980dc-074c-4915-ae6a-3b461f60b9c3.png)  
p를 중심으로 좌회전 후, p와 s의 색상을 바꾼 후 r의 색상을 레드에서 블랙으로 바꾼다.

#### case *-3
![image](https://user-images.githubusercontent.com/54929520/184872785-6f279fcc-9a60-4c0a-bca1-928f358fb79e.png)  
s를 중심으로 우회전 후 l과 s의 색상을 바꾸고 case *-2로 이동.

#### case 2-1
![image](https://user-images.githubusercontent.com/54929520/184872856-3b16ddd4-a799-434b-9858-d09fad78e85a.png)  
s를 레드에서 블랙으로 바꾸면 p의 트리 전체가 블랙노드가 하나 모자라게된다. 이 후에 루트노드까지 이동하며 재귀적으로 문제를 해결한다.

#### case 2-4
![image](https://user-images.githubusercontent.com/54929520/184873162-8136e857-024b-4fde-b681-b2d67b99f4e2.png)  
p를 중심으로 좌회전 후 p와 s의 색상을 바꾼다. 이후 Case 1의 상황이 발생하므로 조건에 맞는 케이스를 해결한다.  

# RedBlack Tree VS AVL Tree
#### 1) 레드-블랙 트리
- 삽입, 삭제 시 균형을 맞추기 위한 작업 횟수가 적다.
- 각 노드당 색깔을 표현하는데 1bit만 필요하다.
#### 2) AVL 트리
- 조회 시 더 빠른 성능
- 노드에 색깔이 없다.
- Balance Factor나 height를 저장하기 위해 integer값을 하나 더 저장해야한다.
