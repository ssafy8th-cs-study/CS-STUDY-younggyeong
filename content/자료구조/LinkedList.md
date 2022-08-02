# 링크드리스트
배열은 순차적으로 연결된 공간에 데이터를 나열하는 자료구조이고, 링크드리스트는 떨어진 곳에 존재하는 데이터를 화살표로 연결해서 관리하는 자료구조이다. 

필요할 때 마다 데이터를 추가할 수 있는 구조이기 때문에 배열의 단점을 극복한 자료구조가 링크드 리스트라고 볼 수 있다.

![image](https://user-images.githubusercontent.com/54929520/182304827-131dd77d-9914-42bb-8c62-57bfc56971b1.png)

링크드 리스트는 연결리스트 혹은 단일 연결리스트 라고 한다.

![image](https://user-images.githubusercontent.com/54929520/182304910-a9fc409c-0bb2-452d-a584-d4463d5fe937.png)

일반적인 링크드 리스트는 위 그림과 같이 데이터값과, 주소값을 하나의 데이터로써 관리한다.

**Node** 는 데이터 저장 단위(Data+Pointer)로 구성되어 있고 **Pointer** 는 다음 연결 node의 정보를 갖고 있는 공간이다.

따라서 첫번째 데이터만 알고 있으면 다음으로 연결된 모든 데이터를 알 수 있다.

## 링크드리스트의 장점
배열과 다르게 미리 데이터 공간을 할당하지 않아도 된다.

## 링크드리스트의 단점
1. 연결을 위한 별도의 데이터공간이 필요하므로 저장공간의 효율이 낮다.
2. 배열과 같이 인덱스로 접근하는 것이 아니기 때문에 데이터 접근 속도가 느리다.
3. 삽입, 혹은 삭제 시 전, 후 데이터의 연결을 재구성해야한다.

## 링크드리스트의 재구성
### 삽입

![image](https://user-images.githubusercontent.com/54929520/182305467-1a3f483d-1e9b-4954-a6e8-790debc5a8ed.png)
새로운 노드를 삽입할 때 새 노드를 생성하고, 찾은 노드의 pointer를 newNode의 주소로 연결해준다. 후에 newNode의 포인터를 node.next의 주소로 연결한다.

### 삭제
![image](https://user-images.githubusercontent.com/54929520/182306102-bf44b247-5e6d-42a1-90cf-a1d36efafafc.png)

삭제할 노드의 이전 노드의 pointer를 삭제한 노드의 next 노드의 주소로 연결한다.

## 이중 연결 리스트(Doubly Linked List)
![image](https://user-images.githubusercontent.com/54929520/182306516-d635adef-04b1-45eb-a480-b49f418c9d11.png)
Node의 포인터가 이전 노드와 다음 노드를 모두 가리키고 있는 것을 **이중 연결 리스트** 라고 한다.

포인터가 양방향으로 연결되어 있기 때문에 마지막노트부터 탐색이 가능하여 더 빠른 시간안에 데이터를 찾을 수 있다.

## ArrayList vs LinkedList 성능 비교
~~~java
import java.util.ArrayList;
import java.util.LinkedList;
import java.util.List;

public class ArrayListLinkedListTest {
    public static void main(String[] args) {
        ArrayList al = new ArrayList(2000000);
        LinkedList ll = new LinkedList();

        System.out.println("= 순차적으로 추가하기 =");
        System.out.println("ArrayList : " + addl(al));
        System.out.println("LinkedList : " + addl(ll));
        System.out.println();
        System.out.println("= 중간에 추가하기 =");
        System.out.println("ArrayList : " + add2(al));
        System.out.println("LinkedList : " + add2(ll));
        System.out.println();
        System.out.println("= 중간에서 삭제하기 =");
        System.out.println("ArrayList : " + remove2(al));
        System.out.println("LinkedList : " + remove2(ll));
        System.out.println();
        System.out.println("= 순차적으로 삭제하기 =");
        System.out.println("ArrayList : " + remove1(al));
        System.out.println("LinkedList : " + remove1(ll));
    }

    public static long addl(List list) {
        long start = System.currentTimeMillis();
        for (int i = 0; i < 1000000; i++) {
            list.add(i+"");
        }

        long end = System.currentTimeMillis();
        return end - start;
    }

    public static long add2(List list) {
        long start = System.currentTimeMillis();

        for (int i = 0; i < 10000; i++) {
            list.add(500, "X");
        }

        long end = System.currentTimeMillis();
        return end - start;
    }

    public static long remove1(List list) {
        long start = System.currentTimeMillis();

        for (int i = list.size() - 1; i >= 0; i--) {
            list.remove(i);
        }

        long end = System.currentTimeMillis();
        return end - start;
    }

    public static long remove2(List list) {
        long start = System.currentTimeMillis();

        for (int i = 0; i < 10000; i++) {
            list.remove(i);
        }

        long end = System.currentTimeMillis();
        return end - start;
    }
}
-------------
= 순차적으로 추가하기 =
ArrayList : 126
LinkedList : 171

= 중간에 추가하기 =
ArrayList : 1695
LinkedList : 10

= 중간에서 삭제하기 =
ArrayList : 1303
LinkedList : 122

= 순차적으로 삭제하기 =
ArrayList : 8
LinkedList : 23
~~~
- 순차적으로 추가/삭제하는 경우에는 ArrayList가 LinkedList보다 빠르다.
- 중간데이터를 추가/삭제 하는 경우에는 LinkedList가 ArrayList보다 빠르다.
### 결론
다루고자 하는 데이터의 개수가  **변하지 않는 경우** 라면 ArrayList가 좋지만, 데이터의 개수의 **변경이 잦다**면 LinkedList를 사용하는것이 더 효율적이다.
