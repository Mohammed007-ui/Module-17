# Ex. No: 17B - BFS Traversal from a Given Source Vertex

## AIM:
To write a Python program to **print BFS traversal** from a given source vertex.

## ALGORITHM:

**Step 1**: Start the program.

**Step 2**: Create a graph using **adjacency list representation**.

**Step 3**: Add edges between vertices using the `addEdge()` method.

**Step 4**: Implement the `BFS()` function:
- Initialize all vertices as **not visited**.
- Use a **queue** to track vertices for traversal.
- Mark the **starting vertex** as visited and enqueue it.
- Dequeue a vertex, process it, and enqueue all its **adjacent unvisited vertices** while marking them as visited.

**Step 5**: Input the **starting vertex** and perform BFS traversal from it.

**Step 6**: Print the vertices in **BFS order**.

**Step 7**: End the program.

## PYTHON PROGRAM

```
from collections import deque

class Graph:
    def __init__(self, vertices):
        self.V = vertices  # Number of vertices
        self.graph = {i: [] for i in range(self.V)}  # Adjacency list

    def addEdge(self, u, v):
        # Assuming undirected graph; for directed, remove the second append
        self.graph[u].append(v)
        self.graph[v].append(u)

    def BFS(self, start_vertex):
        visited = [False] * self.V
        queue = deque()

        visited[start_vertex] = True
        queue.append(start_vertex)

        bfs_order = []

        while queue:
            vertex = queue.popleft()
            bfs_order.append(vertex)

            for neighbor in self.graph[vertex]:
                if not visited[neighbor]:
                    visited[neighbor] = True
                    queue.append(neighbor)

        return bfs_order


# Driver code
if __name__ == "__main__":
    # Create a graph with 6 vertices (0 to 5)
    g = Graph(6)
    g.addEdge(0, 1)
    g.addEdge(0, 2)
    g.addEdge(1, 3)
    g.addEdge(1, 4)
    g.addEdge(2, 4)
    g.addEdge(3, 5)
    g.addEdge(4, 5)

    start_vertex = 0
    print(f"BFS traversal starting from vertex {start_vertex}:")
    bfs_result = g.BFS(start_vertex)
    print(" -> ".join(map(str, bfs_result)))

```

## OUTPUT

![image](https://github.com/user-attachments/assets/4f9211d0-3589-440a-8d3b-77e3020b376d)

## RESULT
The program successfully performs a BFS traversal on the graph starting from the specified source vertex and prints the nodes in the order they are visited. The graph is implemented as an adjacency list, and BFS uses a queue to explore nodes level-by-level.
