LinkedList 에는

1. Singly Linked List
2. Circular Linked List
3. Doubly Linked List

가 있다. 

Signly Linked List는 Head와 Tail 두가지를 갖고 있다.
그래서 붙여나가는 건데,

Algorithm add_first(L,e):
newest = Node(e)
newest.next = L.head 
L.head = newest
L.size = L.size+1

// newest를 head로 잡아주고 size를 1더하는 코드
-> 

Algorithm add_last(L,e):
newest = Node(e)
newest.next = None
L.tail.next = newest
L.tail = newest
L.size = L.size+1

next가 None이면 마지막 Node이기에, 현 tail의 Next를 newest로 잡아주면 마지막에 더해주는 것이 된다.

Algirithm remove_first(L):
if L.head is None then
   Indicate an error: the list is empty.
L.head = L.head.next 
L.size = L.size−1 

Head가 None이라면 이미 빈 LinkedList이기에 오류
head를 현재 head의 next로 잡아주고, size를 하나 빼준다.
-> 이러면 Head가 remove됐으니 앞에서 지워짐

그래서 이거로 뭘 할거냐 하면은 Singly Linked List로 Stack을 구현할 수 있다.

class Node:
slots = _element , _next 
def init (self, element, next): 
   self. element = element 
   self. next = next 

이렇게 한 노드를 설정하고

Singly LinkedList는 
def __init__(self):
   self._head = None
   self._size = 0

def push(self, e):
   self._head = new node(e, self.head)
   self._size += 1

def top(self)
   return self.top

def pop(self):
   answer = self._head_element
   self._head = sefl._head.next
   self.size -= 1

이런식으로 하면 head를 넣다 뺐다하면 stack아 된다. 

그래서 이거 시간복잡도를 보자면
List로 구현했으면 O(1)* (Amortized)이라는 수가 나왔겠지만
얜 우린 이제 더블링할 필요가 없어진다 O(1)이다. 만세!

======================================================================
다음은 Queue이다.

def init
self.head = None
self.tail = None
self.size = None

얜 head tail모두 잡아주게 된다.
얜 dequeue하면, head를 하나 밀어주면 된다.
answer = self.head.element
self.head = self.head.next
self.size -= 1

def enqueue(self, e)
self.tail.next = new_one
self.tail = new_one
self.size += 1


이런식으로 하면 된다.
=======================================================================
이 다음은 Circularly LinkedLists이다.

얜 tail에다 지 head를 다시 붙이면 된다.

head가 tail의 next이기에, head가 필요없다. 

def init
self.tail = None
self.size = None

def first():
   head = self.tail.next
   return head.element

def dequeue():
   oldhead = self.tail.next
   if self.size == 1:
      self._tail = None
   else:
      self.tail_next = old_head_next
   self.size-=1
   return oldhead.element


oldhead의 next를 현재 tail의 next로 잡아주고 그 oldhead의 값을 반환해주면 head의 값을 리턴한게 된다.

def enqueue():
   newest = Node(e)
   if self.empty()
      newest.next = newest
   else:
      newest.next = self.tail.next -> 현재의 head를 뒤에 붙임 즉, 넣은게 맨 뒤
      self.tail.next = newest
   self.tail = newest
   self.size += 1

def rotate():
   if self.not empty =>
      self.tail = self.tail.next() -> 현재의 tail을 head로 바꿔 한칸 돌린게 됨

========================================================================================
마지막은 Doubly Linked Lists

-> 얜 앞에거 다 합친거로 보면된다. head tail elemtent3가지를 각 Node들이 모두 갖고 있어서
양쪽으로 연결되어있다.

Doubly Linked List를 HEAD 와 TAIL만으로도 구현할 수 있지만, 앞 뒤에 아무것도 없는 None인 SENTINEL을 두개 붙여놓으면
훨씬 손쉽게 구현할 수 있다.

DLL이다보니, 노드도 prev next element를 모두 가진다

class Node:
slots = _element , _prev , _next 
def init (self, element, prev, next): 
self. element = element 
self. prev = prev 
self. next = next

그리고 우리의 DLL Class는 header trailer 를 가진다.

근데, 여기서 header와 trailer는 sentinel이다.  그렇기에

def init (self):
self. header = self. Node(None, None, None)
self. trailer = self. Node(None, None, None)
self. header. next = self. trailer 
self. trailer. prev = self. header 
self. size = 0

처럼 된다

양측으로 연결되어있기에 중간에 끼워넣는 것과 아무데서나 지우는 것 모두 가능하다.

이때, 전 노드의 next를 새 노드에, 뒷 노드의 prev를 새 노드에 연결하는 것을 잊어서는 안된다.

이거로 만들 수 있는게 Deque이다.

Deque는 Queue와 Stack을 합친 것과 동일한데, 
양쪽으로 넣을 수 있으며 양쪽으로 뺼 수 있다. sentinel만 잘 고려하면 잘 짤 수 있을 거다

insert between함수를 짜서 head와 head.next사이에, tail과 tail.next사이에 넣으면 된다.

def insert between(self, e, predecessor, successor):
   newest = self. Node(e, predecessor, successor)
   predecessor. next = newest
   successor. prev = newest
   self. size += 1
   return newest


==================================================================
그래서 얘네가 전부 다 Link-Based Sequences인데, Array-Based와의 차이점은 뭘까/

위에서 언급했듯이, Array Based는 더블링 때문에 실제 있는 원소보다 훨씬 더 큰 크기를 차지할 수가 있다. 그리고 또한, Amortized시간복잡도를 사용해야 한다
그리고 insertion, deletion을 앞이나 뒤가 아닌 중간쯤에서 하려면 큰 비용이 든다

하지만 LinkedList는 각 객체가 Node로 분리되어있기에 위와 같은 문제점들이 없다. 
하지만 얘의 문제는 인덱스로 접근해낼 수가 없다는 것이다. like stack[5].
