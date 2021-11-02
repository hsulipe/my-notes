# Queue

## Description


Queues are very commonly used data structures. They are very useful to maintain the order of objects.
The main rule about queues is First in First out. Wich means that the first object to be inserted into the queue is the first object to be removed.

## Implementations


- C#

```c#
class Queue<T> {
    List<T> queue = new List<T>();

    public Queue() {

    }

    public void Enqueue(T el) {
        queue.Add(el);
    }

    public T Dequeue() {
        T el = queue[0];
        queue.Remove(el);
        return el;   
    }

    public T Peek() {
        return queue[0];
    }
}
```

## Utilization


- BFS: Bread-first-search
    - Used to verify the distance from one node to all other nodes in a graph.

```c#
public static int[] BreadFirstSearch(Graph g, int s_index) {
    int[] distances = new int[g.Nodes.Count];
    for(int i = 0; i < g.Nodes.Count; i++){
        distances[i] = -1;
    }
    
    distances[s_index] = 0;
    
    Queue<Node> q = new Queue<Node>();
    Node cur_node = g.Nodes[s_index];
    
    HashSet<Node> seen = new HashSet<Node>();
    
    q.Enqueue(cur_node);
    seen.Add(cur_node);
    while(q.Count > 0) {
        cur_node = q.Dequeue();
        foreach (Node n in cur_node.Children) {
            if(!seen.Contains(n)){
                q.Enqueue(n);
                seen.Add(n); 
                distances[n.Key] = distances[cur_node.Key] + 6;
            }
        }
    }
    
    return distances;
}
```

## References
- [Queue Data Structure](https://www.geeksforgeeks.org/queue-data-structure/)