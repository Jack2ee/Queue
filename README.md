Queue
=====
#### 큐(Queue)
큐는 먼저 넣은 데이터가 먼저 나오는 FIFO(Firtst-In-First-Out) 구조로 저장하는 자료구조이다.
즉 큐는 LIFO 구조인 스택과 반대되는 개념의 자료구조이다.
스택은 데이터가 입/출력하는 부분이 한 부분밖에 없다고 한다면, 큐는 양쪽 모두 뚤려있다.
한쪽으로는 데이타를 넣기만 하고, 다른쪽에서는 데이타를 빼내기만 한다. 
데이터를 넣는 연산을 PUT 동작, 데이터를 빼내는 동작을 GET 동작이라고 한다.

#### 큐의 구현
큐는 스택과 마찬가지로  ArrayList나 LinkedList를 이용해 구현할 수 있다.
ArrayList를 이용하는 경우 Circular Queue로 구현할 수 있다. 
Circular Queue로 구현하는 이유는 Queue 자료구조의 성격상 한쪽 방향으로 계속 움직이게된다. 
위에서의 그림처럼 왼쪽에서 Enqueue하고 오른쪽에서 Dequeue하게되면, 저장 공간은 왼쪽 방향으로 계속 움직이게된다. 
따라서 원형으로 구현하게 된다면, 방향성에 상관없이 효율적으로 공간을 활용할 수 있게되는 것이다. 
또한 Deque(Double Endded Quque; 덱이라고 발음)이라는 자료구조는 큐와 동일하지만 양쪽에서 데이터를 넣고 뺄 수 있다. 
python의 collection framework에는 deque이라는 클래스를 제공하기 때문에 이 클래스를 이용해서 Queue(혹은 Stack)를 구현할 수 있다. 
```Python
# ArrayList(Circular Queue)로 구현
class ArrayQueue(BaseQueue):
  def __init__(self, max=MAX):
    self.max = max
    self.list( = [None]*self.max
    self.size = self.front = self.rear = 0
    
  def is_empty(self):
    return self.size == 0
  
  def is_full(self):
    return self.next_idx(self.rear) == self.front
    
  def next_idx(self):
    return (idx+1)%self.max
  
  def enqueue(self, data):
    if self.is_full():
      raise Exception('큐가 꽉 참')
      
    self.rear = self.next_idx(self.rear)
    self.list[self.rear] = data
    self.size += 1
   
   def dequeue(self):
    if self.is_empty():
      raise Exception('큐가 빔')
     
    self.front = self.next_idx(self.front)
    return self.list[self.front]
    
    def peak(self):
      return self.list[self.next_idx(self.front)]
    
    def display(self):
      current = self.front
      while current != self.rear:
        current = self.next_idx(current)
        print(self.list[current])
        
 
 # deque 모듈
 from collections import deque
  queue=deque()
  queue.append(1)  # PUT data
  queue.append(2)
  
  while queue:
    queue.popleft()  # GET data
 ```
