# Stack

## description

Stacks and one of the first datastructures to be used, stack exists since the invention of the turing machines. The main concept of Stack is First in Last Out.
It also can be used to create a queue.

## Complexity

| Operation            | Complexity |
|----------------------|------------|
| Insertion on top     |     O(1)   |
| Remove top element   |     O(1)   |
| Access top element   |     O(1)   |

## Implementation

- C#  

```c#
class Stack<T> {
    Array<T> stack;
    int capacity;
    int size;
    public Stack(int n) {
        this.stack = new Array<T>(n)
        this.capacity = n;
        this.size = 0;
    }

    public void Append(T value) {
        if(size >= n) {
            throw Error("Stack Overflow");
        }
        stack[stack.Length - 1] = value;
        size++;
    }

    public T Pop() {
        if(size == 0) {
            throw Error("Stack Empty");
        }
        T value = stack[stack.Length - 1];
        stack[stack.Length - 1] = 0;
        size--;
        return value;
    }

    public T Peek() {
        return stack[stack.Length - 1];
    }
}
```

- Python  

```python
class Stack:
    def __init__ (self, capacity):
        self.capacity = capacity
        self.stack_array = [0]*capacity
        self.size = 0
    
    def append(data):
        if size >= capacity:
            return 0
        
        stack_array[size] = data
        size += 1
        return data
    
    def pop():
        if size == 0:
            return 0

        size -= 1
        
        aux = stack_array[size]
        stack_array[size] = 0
         
        return aux
    
    def peek():
        return stack_array[size - 1]
```

## Example

- This purpose of this algorithm is to verify if all brackets are balanced. Wich means after a open bracket `(`, `{` and `[`, will be a closing bracket `)`, `}` and `]` without they overlap.

```c#
public static string isBalanced(string s)
{
    Stack<char> stack = new Stack<char>();
    char[] input = s.ToCharArray();
    
    if(s.Length%2 == 1) return false;
    
    for(int i = 0; i < input.Length; i++) {
        char curr = input[i];
        if(curr == '[' || curr == '{' || curr == '(') {
            stack.Push(input[i]);
        }
        else {
            if (stack.Count == 0) return false;
            if ((input[i] == '}' && stack.Peek() != '{') || 
                (input[i] == ']' && stack.Peek() != '[') || 
                (input[i] == ')' && stack.Peek() != '('))
                return false;
            stack.Pop();
        }
    }
    return (stack.Count == 0)? true: false;
}
```

- Stacks can also be used to implement Queues and other data structures. 


## Problems

[Balanced brackets](https://www.hackerrank.com/challenges/balanced-brackets/problem)  
[Queue using two stacks](https://www.hackerrank.com/challenges/queue-using-two-stacks/problem)


## References

- [Stack Data Structure](https://www.geeksforgeeks.org/stack-data-structure/)
