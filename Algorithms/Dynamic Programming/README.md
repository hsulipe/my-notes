# Dynamic Programming

## Objective

Quick study about Dynamic Programming. Resolution of some known problems.


## Concept

The main idea behind Dynamic Programming is to divide one problem into several sub problems. Then add a caching layer to the resolved problems, this way when the problem reapear the solution is already known.

## Tabulation vs Memoization

### Tabulation

Representes an way to store the results based on the bottom-Up approach. This means dividing the Big problem into smaller problems first.


### Memoization

Representes the other way around. solving the smaller problems first which results on the global solution.


## Hackerrank Problems

- [The Coin Change Problem](https://www.hackerrank.com/challenges/coin-change/problem)

## Example


- The Coin Change Problem
    - Given an infinite number of coins of _c_ types. Return All ways to make change for _n_ . This problem utilizes Dynamic Programming and memoization to store combinations to smaller numbers like _1_ then _n-1_ to _n_.


```javascript
function getWays(n, c) {
    let ways = new Array(n + 1)
    for(let i=0;i<n+1;i++)
    {
        ways[i]=0;
    }
    ways[0] = 1;
    
    for (let i = 0; i < c.length; i++) {
        for (let j = 0; j < ways.length; j++) {
            if (c[i] <= j) {
                ways[j] += ways[(j - c[i])];
            }
        }
    }
    return ways[n]
}
```


## References

- [Dynamic Programming](https://www.geeksforgeeks.org/dynamic-programming/).
- Cracking the Code Interview, by Gayle Laakmann Mcdowell.


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