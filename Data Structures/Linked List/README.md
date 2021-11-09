# Linked List

## Description

![Diagram-1](Assets/linked-list-diagram-1.md)

## Complexity

| Operation | Complexity |
|-----------|------------|
| Insertion |     O(1)*  |
| Deletion  |     O(1)*  |
| Access    |     O(n)   |


## Implementation
- C#  

```c#

```


- Python 1st

```python
class LinkedList:
    def __init__(self):
        self.list = []
        self.size = 0
    
    def add(data):
        list.append(data)
        size += 1
    
    def remove(data):
        ind = find(data)
        if ind == -1:
            return False
        list.pop(ind)
        size -= 1
        return True
    
    def find(data, index = 0):
        if index >= size:
            return -1
        if list[index] == data:
            return index
        find(data, index + 1)
```

- Python 2st - WORK_IN_PROGRESS

```python
class LinkedList:
    def __init__(self)
        self.head = None
        self.tail = None
        self.size = 0
    
    def add(data):
        node = Node(data)
        if size == 0:
            head = node
            tail = node
        else:
            tail.next = node
            tail = node

    def remove(data):
        node = find(data)
        if node == None:
            return False
        node = node.next


    def find(data, node = head):
        if node == Node:
            return None
        if node.value == data:
            return node
        if node.next == None:
            return None
        find(data, node.next)

class Node:
    def __init__(self, value):
        self.value = value
        self.next = None
```
## References

- [Linked List Data Structure](https://www.geeksforgeeks.org/data-structures/linked-list/)