# Stack

## description

Stacks and one of the first datastructures to be used, stack exists since the invention of the turing machines. The main concept of Stack is First in Last Out.


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
        stack.Add(value);
        size++;
    }

    public T Pop() {
        if(size == 0) {
            throw Error("Stack Empty");
        }
        T value = stack[stack.Count()];
        stack.Remove(value);
        size--;
        return value;
    }

    public T Peek() {
        return stack[stack.Count()]; 
    }
}
```

## Example

- This purpose of this algorithm is to verify if all brackets are balanced. Wich means after a open bracket '(', '{' and '[', will be a closing bracket ')', '}' and ']' without they overlap.

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

## References

- [Stack Data Structure](https://www.geeksforgeeks.org/stack-data-structure/)