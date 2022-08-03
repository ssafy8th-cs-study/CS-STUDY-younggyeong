# 스택
한쪽 끝에서만 데이터를 넣고 뺄 수 있는 제한적으로 접근할 수 있는 후입선출(LIFO) 형태의 자료구조이다.
<img src="https://user-images.githubusercontent.com/54929520/182538892-68ce2f44-cdf2-43a2-aa36-1e44ae15f9a5.png" width="300" height="500">


## 스택의 연산
**1. push**

데이터를 스택에 넣는 작업을 push 라고 한다.

<img src="https://user-images.githubusercontent.com/54929520/182538647-9ea4b44d-755e-4177-b80d-1729ed321367.png" width="300" height="500">

**2. Pop**

데이터를 스택에서 제거하는 작업을 Pop이라고 한다.
![image](https://user-images.githubusercontent.com/54929520/182538852-f2bd1fbf-0542-4297-a7c3-a0ebc10620fd.png)

## 스택의 시간복잡도
Operation|Average|Worst
|---|---|---|
Access|O(n)|O(n)|
Search|O(n)|O(n)|
Push|O(1)|O(1)|
Pop|O(1)|O(1)|

## 스택 구현 코드
~~~java
public class MyStack {
  private static class StackNode {
    private T data;
    private StackNode next;

    public StackNode(T data) {
      this.data = data;
    }
  }

  private StackNode top;

  public T pop() {
    if (top == null) throw new NoSuchElementException();
    T item = top.data;
    top = top.next;

    return item;
  }

  public void push(T item) {
    StackNode t = new StackNode(item);
    t.next = top;
    top = t;
  }

  public T peek() {
    if (top == null) throw new NoSuchElementException();
    return top.data;
  }

  public boolean isEmpty() {
    return top == null;
  }
}
~~~

## 스택의 사용사례
1. 재귀알고리즘
2. 웹 브라우저 방문기록 (뒤로가기)
3. 실행 취소
4. 후위표기법 계산

## Java의 스택 관련 메서드
**-push(E item)**  
해당 item을 Stack의 top에 삽입  
Vector의 addElement(item)과 동일  
**-pop()**  
Stack의 top에 있는 item을 삭제하고 해당 item을 반환  
**-peek()**  
Stack의 top에 있는 item을 삭제하지않고 해당 item을 반환  
**-empty()**  
Stack이 비어있으면 true를 반환 그렇지않으면 false를 반환  
**-search(Object o)**  
해당 Object의 위치를 반환  
