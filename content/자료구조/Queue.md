# 큐
큐는 먼저 집어넣은 데이터가 먼저 나오는 FIFO(First In Fist Out) 로 저장하는 선형구조이다.
![image](https://user-images.githubusercontent.com/54929520/182552151-68152647-9ed3-4349-860f-c36900e7a563.png)

## 큐의 연산
**1. add**  
item을 리스트의 Rear에 추가한다.

**2. remove**  
item을 리스트의 front에서 제거한다.

## 큐의 종류
**1. 선형 큐**  
기본적인 큐 형태로, 위의 사진의 구조와 같다.  
구현시 크기가 제한되어 있고 삽입 및 삭제를 반복하다 보면, rear가 마지막 인덱스를 가리키고, 앞은 비어있지만 이를 꽉 찾다고 인식하는 문제점이 있다.  
![image](https://user-images.githubusercontent.com/54929520/182553299-557caf26-1dc9-4236-a64c-b3b3ff903b00.png)
 
**2. 환형 큐**  
처음과 끝이 원형으로 이어져있다고 가정한 큐이다. 선형 큐의 단점을 보완하였으며 큐를 원형으로 생각하기 때문에 모듈러 연산(나머지 연산)을 해야한다.
![image](https://user-images.githubusercontent.com/54929520/182553856-6d85061d-d9bf-445b-9912-8391a8a18b99.png)


## 큐의 구현 코드
~~~java
public class MyQueue {
  private static class QueueNode {
    private T data;
    private QueueNode next;

    public QueueNode(T data) {
      this.data = data;
    }
  }

  private QueueNode first;
  private QueueNode last;

  public void add(T item) {
    QueueNode t = new QueueNode(item);

    if (last != null) last.next = t;
    last = t;
    if (first == null) first = last;
  }

  public T remove() {
    if (first == null) throw new NoSuchElementException();
    T data = first.data;
    first = first.next;

    if (first == null) last = null;
    return data;
  }

  public T peek() {
    if (first == null) throw new NoSuchElementException();
    return first.data;
  }

  public boolean isEmpty() {
    return first == null;
  }
}
~~~

## 큐의 시간복잡도 
Operation|Average|Worst
|---|---|---|
Access|O(n)|O(n)|
Search|O(n)|O(n)|
Push|O(1)|O(1)|
Pop|O(1)|O(1)|

## 큐의 사용사례
1. CPU 스케쥴링
2. 우선순위가 같은 작업 예약
3. 티켓 카운터
4. 프린터의 출력처리
