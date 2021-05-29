# Algorithm

# 1. SORT

> https://gyoogle.dev/blog/algorithm/Selection%20Sort.html
>
> https://github.com/GimunLee/tech-refrigerator/tree/master/Algorithm/resources

## 1-1. Selection sort

```python
def selectionSort(arr):
    n=len(arr)
    for i in range(n-1):
        temp=i
        for j in range(i+1, n):
            if arr[temp]>arr[j]:
                temp=j

        a[i],a[temp]=a[temp],a[i]
```

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbekAxf%2FbtqBWrh1Sjl%2FAAVyKUtExiy6pdwfbhgR3k%2Fimg.gif)

선택정렬은 우선 위치를 선정하고 그 위치에 들어올 값을 찾는 방식이다. 

시간복잡도 : O(n^2)

공간복잡도 : O(n)

- 장점
  1. 알고리즘이 단순하다.
  2. 제자리 정렬
- 단점 :
  1. 불안정 정렬이다.
  2. 비교적 시간복잡도가 큰 편이다. 

## 1-2. Insertion sort

```python
def insertionSort(arr):
    n=len(arr)

    for i in range(1,n):
        temp=arr[i] 
        for j in range(i-1,-1,-1):
            if arr[j]>temp:
                arr[j+1]=arr[j]
                arr[j]=temp

            else:
                break
```

![](https://github.com/GimunLee/tech-refrigerator/blob/master/Algorithm/resources/insertion-sort-001.gif?raw=true)

삽입정렬은 값을 선정하고 그 값이 들어갈 위치를 선정하는 것이다.

시간복잡도 : O(n^2)

공간복잡도 : O(n)

- 장점
  1. 안정정렬이다.
  2. 이미 정렬이 되어있는 경우(최선시간복잡도) : O(n)
- 단점
  1. 정렬해야하는 배열이 커질경우 비효율적이다.

## 1-3. Bubble sort

```python
def bubbleSort(arr):
    n=len(arr)

    for i in range(1,n):
        for j in range(i):
            if arr[j-1]>arr[j]:
                arr[j-1],arr[j]=arr[j],arr[j-1]
```

![](https://github.com/GimunLee/tech-refrigerator/raw/master/Algorithm/resources/bubble-sort-001.gif)

옆에있는 값이랑 비교하여 교환하는 방식으로 정렬해나가는 방법이다.

처음에 n-1번 비교하면 다음 회차때는 n-2번, n-3번... 비교횟수가 줄어든다.

시간복잡도 : O(n^2)

공간복잡도 : O(n)

- 장점 :
  1. 제자리정렬이다.
  2. 안정정렬이다.
- 단점 : 
  1. swap이 많이 일어난다. 

## 1-4. Quick sort

![](https://github.com/GimunLee/tech-refrigerator/raw/master/Algorithm/resources/quick-sort-002.png)

퀵정렬 과정

1. 배열에서 랜덤하게 pivot을 고른다.
2. pivot을 중심으로 왼쪽에는 작은 수, 오른쪽에는 큰 수로 분할한다. (분할)
3. 분할된 배열에서 1번부터 반복한다. 

퀵정렬은 분할 정복법이다.  

1회차 : n-1번비교  

2회차 : n-2번 비교  

....  

(logn)회차 : 1번 비교  

---

시간복잡도 : O(nlogn)

공간복잡도 : O(n)

---

<pivot에 따른 효율성>

만약 pivot을 최소값이나 최대값으로 잡힌다면 최대 시간복잡도가 O(n^2)번이 나올 수 있다. 

이를 개선하기 위한 방법

1. pivot을 정할 때 가장 앞에있는 값과 중간값을 교환후에 정한다. 
2. pivot을 랜덤한 위치에서 정한다.
3. 첫인덱스, 마지막인덱스, 중간인덱스 중에서 중간값을 pivot으로 정한다.

하지만 이러한 방법들을 한다고해서 반드시 O(n^2)의 시간복잡도를 개선할 수 있는것은 아니다. 

그래서 나온 베스트 방법은 삽입정렬과 함께 사용하는것이다.  삽입정렬은 배열의 크기가 작을 경우 최선으로 O(n)번의 시간복잡도를 낼 수 있다.  그래서 일정 퀵정렬을 수행하다가 일정 배열 크기 아래에서부터는 삽입정렬을 하는 것이 효율적인 방법이라고 할 수 있다. 



- 장점 
  1. 다른 정렬에 비해서 빠른 편이다.
- 단점
  1. pivot 값을 최대값이나 최소값으로 잡을 경우 최악의 시간복잡도가 나온다.
  2. 불안정정렬이다. 



## 1-5. Merge sort

합병정렬은 퀵정렬과 달리 우선 분할한 뒤에 정복을하는 방법이다.

(Devide->Merge) 

1. 분할(divide)
2. 정복(sort)
3. 결합(merge)
4. 복사(copy) 

---

1회차 비교 : 1번  

2회차 비교 : 2번  

...  

(logn)회차 비교 : n-1번

---

시간복잡도 : O(nlogn)  

공간복잡도 : O(n)  

- 장점

  1. linkedlist 정렬시에 효율적이다. (퀵정렬에서는 순차탐색이 필요하기떄문에 비효율적이다.)
  2. 퀵정렬보다 효율적이다. pivot때문에 성능차이가 발생하지 않는다.
  3. 안정정렬이다.

- 단점

  1. 추가적인 메모리가 필요할 수 있다. (병합과정에서 생김) 이럴때는 퀵정렬을 선택하는 편이다. 

  

## 1-6. Heap sort

완전 이진트리를 기본으로하여 정렬한다.  

1.  배열 순서대로 완전 이진트리를 생성한다. 
2. 힙트리를 구성한다. (부모노드가 자식노드보다 값이 크거나 같다)
3. 힙의 마지막 노드와 최대값(루트)와 교환하면서 힙의 사이즈를 줄인다. (정렬) 

다음 유튜브 영상이 힙정렬 과정을 자세히 보여주고있다. 

> https://www.youtube.com/watch?v=aOP81IhPOmw

 <인덱스 참조>

left child = parent * 2 +1

right child = left + 1



시간복잡도 : O(nlogn)



- 장점 
  1. 최대값이나 최소값을 구하기 쉽다.(최대힙, 최소힙의 루트)
- 단점
  1. 불안정 정렬이다. 



# 2. Array

정적으로 할당한 공간

- 장점

  1. 인덱스로 탐색이 빠르다.

- 단점

  1. 삽입,삭제가 느리다.

  2. 고정된 공간이라 메모리 효율성은 linked list보다 떨어진다. 

     

# 3. 배열 회전

## 3-1. 저글링 알고리즘

![](https://cdncontribute.geeksforgeeks.org/wp-content/uploads/arra.jpg)

배열 크기의 최대 공약수로 집합을 묶어서 회전시킨다. 

## 3-2. 역전 알고리즘

배열의 크기가 n이고 회전 횟수가 d일경우

(1,2,3,4,5)

1. d/n-d로 쪼갠다. : (1,2 / 3,4,5) 
2. reverse(d), reverse(n-d) : (2,1/ 5,4,3)
3. merge : (2,1,5,4,3)
4. revers() : (3,4,5,1,2)



# 4. Linked List

![](https://www.geeksforgeeks.org/wp-content/uploads/gq/2013/03/Linkedlist.png)

- 장점 
  1. 동적으로 생성할 수 있다.
  2. 삽입, 삭제가 편하다.
- 단점
  1. 배열의 인덱스 검색보다 느리다. (순차적 검색 필요)
  2. 포인터를 저장할 추가적인 공간이 필요하다. 



# 5. Stack / Queue

- Stack : LIFO (Last In First Out)
- Queue : FIFO (First In First Out)

---

- Stack : DFS 탐색
- Queue : BFS 탐색

---

- Stack : push(), pop()
- Queue : enqueue(), dequeue()

---

- Stack : 함수 콜스택, 역순 출력
- Queue : 버퍼

### 5-1. Queue 구현

큐를 array로 구현하면 문제가 생긴다. 왜냐하면 front/rear(dequeue 위치/enqueue 위치)는 -1로 초기화가 된다.  

만약 enqueue가 생기면 rear를 +1하고 값을 삽입한다.  

dequeue가 생기면 front를 +1하고 값을 얻은뒤 그 공간을 삭제한다.  

isEmpty : front=rear이면 비어졌다.  

isFull : rear=queueSize-1이면 가득찼다.   

하지만, front를 +1해왔기때문에 사실상 앞에 공간이 생겼음에도 불구하고 queue가 꽉찼다고 착각할 수 있다. 이를 개선한 것이 원형 큐이다. 

## 5-2. 원형 Queue

논리적으로 배열의 처음과 끝이 같다고 생각한다. 

front/rear의 초기값 = 0  

front/rear를 배열 순환시키면서 탐색한다. 

- 장점 :
  1. 메모리 공간 효율이 좋다.
- 단점 : 
  1. 배열이기때문에 어쩔수없이 큐의 크기가 한정되어있다.

단점을 개선하기 위해서 연결리스트 큐를 사용한다. 공간의 제약이 없으며 삽입,삭제가 편리하다. (O(1))

