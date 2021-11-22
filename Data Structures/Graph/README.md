# Graphs - WIP

![Graph](../../Assets/images/graph-diagram-1.png)

## Description

Graph is mathematical structure used to model pairwise relations between objects. A graph is made of vertices connected by edges.

## Complexity

| Operation | Complexity     |
|-----------|----------------|
| Insertion |     O(log(n))  |
| Deletion  |     O(log(n))  |
| Access    |     O(log(n))  |

### Types of graphs

- Directed graph

    Where edges link vertices asymmetrically.

- Undirected graph

    Where edges link vertices symmetrically.

- Simple graph
- Complete graph
- Tree

### In-memory representation

Graphs can be represented computationally by the usage of an adjacency list or a incidence matrix.

- Graphs 1 Adjacency list

    | Node | Adjacent to | vertices |
    |------|-------------|----------|
    |   A  | adjacent to |    B     |
    |   B  | adjacent to |  C,D     |
    |   C  | adjacent to |  A,D     |
    |   D  | adjacent to |   --     |

- Graph 1 incidence matrix

    |   | A | B | C | D |
    |---|---|---|---|---|
    | A | 0 | 1 | 0 | 0 |
    | B | 0 | 0 | 1 | 1 |
    | C | 1 | 0 | 0 | 1 |
    | D | 0 | 0 | 0 | 0 |

## Implementation

## DFS - Depth-first-search

Since Trees are also graphs, the DFS of trees and graphs are very similar, the only diferrence is that graph may contain cycles wich may lead to an infinite loop. To avoid this use a boolean array to mark the nodes that were already visited.

- Python

    ```python
    def DFS_graph (vertice, visited):
        visited.add(vertice)

        for neighbour in vertice[neighbours]:
            if neighbour not in visited:
                DFS_graph(neighbour, visited)
    ```

## BFS - Breadth-first-search

Also very similar to the BFS algorithm for trees. The only difference is the addition of the boolean array 'visited', used to avoid infinite loops and passing in the same vertice more than once.

- Python

    ```python
    def BFS_graph(vertice):
        visited = [False] * graph.size

        queue = []

        queue.append(vertice)
        visited[vertice] = True

        while len(queue) > 0:
            s = queue.pop(0)

            for i in graph[vertice].neigbours:
                if visited[i] == False:
                    queue.append(i)
                    visited[i] = True
    ```

## Dijkstra algorithm

Dijkstra's algorithm is very similar to the Breadth-first-algorithm. The main diferrence is that it is used mainly for weighted graphs and it's purpose is to find the lowest-cost path from one node to another.
![Dijkstra](/Assets/images/Dijkstra_Animation.gif)

## References

[Teoria dos Grafos](https://pt.wikipedia.org/wiki/Teoria_dos_grafos)  
[Graph data structure and algorithms](https://www.geeksforgeeks.org/graph-data-structure-and-algorithms/)  
[Deph-first-search](https://www.geeksforgeeks.org/depth-first-search-or-dfs-for-a-graph/)  
[Breadth-first-search](https://www.geeksforgeeks.org/breadth-first-search-or-bfs-for-a-graph/)  
[Incidence Matrix](http://https://en.wikipedia.org/wiki/Incidence_matrix)  
[Algoritmo de Dijkstra](https://pt.wikipedia.org/wiki/Algoritmo_de_Dijkstra)
