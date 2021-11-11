# Trees

## Binary Tree

Birary tree is a special type of tree that instead of having multiple children, it has only two. One to the left and one to the right. Thats the reason why its called a Binary tree.

## Complexity

| Operation  | Complexity     |
|------------|----------------|
| Insertion  |     O(log*n)   |
| Deletion   |     O(log*n)   |
| Access     |     O(log*n)   |

### Height and Depth

```python
def height(root):
    if root.left is None and root.right is None:
        return 0
    if root.left is None:
        return height(root.right) + 1
    if root.right is None:
        return height(root.left) + 1
    
    return max(height(root.left), height(root.right)) + 1
```

### Level Order

To pass to all nodes of a tree using the level order, is necessary to use an auxiliar data structure, the queue. And this operation cannot be done recursively.

```python
def levelOrder(root):
    node = root
    
    queue = []
    queue.append(root)
    while len(queue):
        node = queue.pop(0)
        if node.left:
            queue.append(node.left)
        if node.right:
            queue.append(node.right)
        print(node.info, end=" ")
```

## References

- [Binary trees](https://www.geeksforgeeks.org/binary-tree-data-structure/)
