# Single-DoublyLinkedLists-

    对比单链表和双链表。这里self.head都是指针。
    1）大家都是先建一个 node，定义指针子。然后在进行design
    2）每个新建的功能都要从init开始哈
    3）都考虑一下self.head是空的时候。
    4）双链条一定要两个node相连。next+prev。 单链条，有next就可以了

      class Node(object):
          def __init__(self, val=None):
              self.val = val
              self.next = None
              self.prev = None

      class BilateralLinklist(object):
          def __init__(self):
              self.head = None
              self.size = 0

          def display(self):
              cur = self.head
              if self.head == None:
                  return
              while cur:
                  print(cur.val)
                  cur = cur.next
              # 只是呈现所以不用加入val。
              # 先打印第一个，再轮下面那个

          def addTail(self,val):
              newNode = Node(val)
              cur =self.head
              if self.head == None:
                  self.head = newNode
              while cur.next:
                  cur = cur.next
              cur.next = newNode
              newNode.prev = cur

              self.size +=1

          def addHead(self,val):
              newNode = Node(val)
              if self.head == None:
                  self.head = newNode
              else:
                  self.head.prev = newNode
                  newNode.next = self.head
                  self.head = newNode
                  # 前面加一个新值 -》 新值后面是起始值 -〉起始值自动前移

              self.size +=1

          def reverse(self):
              temp = None
              cur = self.head
              while cur is not None:
                  temp = cur.prev
                  cur.prev = cur.next
                  cur.next = temp
                  cur = cur.prev
                  # 占位前面的空位：temp
                  # 前位=原来的下一个 - 》 原来的下一个占位前位，挪过来 -〉 cur变到前一个.和原来相反
                  # 顺序不能换，先定义前面的东西/位-值。确定两者合并。逻辑，等于上一个。

              if temp is not None:
                  self.head = temp.prev
                  # 必须放在尾巴上。指针在前一个。
                  
      #  https://www.geeksforgeeks.org/reverse-a-doubly-linked-list/  
      
          def getSize(self):
              print (self.size)

myList = BilateralLinklist()
myList.addHead(2) 
myList.addHead(1)
myList.addTail(3)
myList.display()  
myList.reverse() 
myList.display() 
myList.getSize()
