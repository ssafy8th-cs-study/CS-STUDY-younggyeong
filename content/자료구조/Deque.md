# Deque
![image](https://user-images.githubusercontent.com/54929520/184060282-b0df9416-fb30-417c-906c-544bd51e914a.png)  
일반 큐는 한쪽에서만 삽입과 삭제가 가능하다

![image](https://user-images.githubusercontent.com/54929520/184060314-266df4bc-6224-4809-929d-1b1656ce39a4.png)  
하지만 덱 자료구조는 양방향에서 삽입과 삭제가 가능하다.

## Deque의 특징
1. 크기가 가변적이다.  
2. **양방향**에서 삽입과 삭제가 가능하다.  
3. 그럼에도 불구하고 데이터 중간에 삽입과 삭제가 용이하지 않다.
4. 인덱스를 이용한 랜덤접근이 가능하다.

## Deque의 ADT
addFront(x) : 요소 x를 덱의 맨 앞에 추가  
addRear(x) : 요소 x를 덱의 맨 뒤에 추가  
deleteFront() : 큐의 맨 앞의 요소를 삭제하고 반환  
deleteRear() : 큐의 맨 뒤의 요소를 삭제하고 반환  
getFront() : 큐의 맨 앞의 요소를 삭제하지 않고 반환  
getRear() : 큐의 맨 뒤의 요소를 삭제하지 않고 반환  
isEmpty() : 큐가 비어있으면 true 아니면 false 반환  
isFull() : 큐가 가득 차 있으면 true 아니면 false 반환  
size() : 큐 내의 모든 요소 개수를 반환   
display() : 큐 내의 모든 요소 출력  
![image](https://user-images.githubusercontent.com/54929520/184061135-70c75c72-c16b-4172-9e32-19bf8237996d.png)

## Deque를 사용하는 경우
1. 데이터의 앞,뒤에 삽입,삭제를 하는 경우
2. 저장할 데이터의 개수가 가변적일경우
3. 검색을 하지 않는 경우

## 자바에서의 덱 사용법
~~~java
Deque<String> deque1 = new ArrayDeque<>();
Deque<String> deque2 = new ConcurrentLinkedDeque<>();
Deque<String> deque3 = new LinkedBlockingDeque<>();
Deque<String> deque4 = new LinkedList<>();
~~~
### 덱 값 추가
![image](https://user-images.githubusercontent.com/54929520/184061347-fbd44763-b795-482b-8701-4d96e0926129.png)

### 덱 값 삭제
![image](https://user-images.githubusercontent.com/54929520/184061362-d1836520-ccbf-4fdd-8e50-41fce32e03d9.png)

### 덱 값 출력
![image](https://user-images.githubusercontent.com/54929520/184061379-66d5fcec-3f76-422c-a8e1-0e43b217d9c6.png)


## 예상질문 
**1. 스택 vs 큐**  
스택은 **Last in First out** (LIFO)  
큐는 **First in First out** (FIFO)  
deque는 **양방향** 출입이 자유로운 큐  
원래 queue는 push back pop front만 가능한 것이 원칙  
하지만 deque는 push front, back, pop front, back 모두 가능  

