# Ex. No: 17C - DFS Traversal from a Given Source Vertex

## AIM:
To write a Python program to **print DFS traversal** from a given source vertex.

## ALGORITHM:

**Step 1**: Start the program.

**Step 2**: Create a graph using **adjacency list representation**.

**Step 3**: Add edges between vertices using the `addEdge()` method.

**Step 4**: Implement the `DFSUtil()` function to **recursively visit** and print each unvisited vertex:
- Mark the current vertex as **visited**.
- Recursively call `DFSUtil` for each **unvisited adjacent vertex**.

**Step 5**: In the `DFS()` function:
- Initialize an empty set for visited vertices.
- Call `DFSUtil()` starting from the given vertex.

**Step 6**: Input the **starting vertex** and perform DFS traversal.

**Step 7**: Print the vertices in **DFS order**.

**Step 8**: End the program.

## PYTHON PROGRAM

```
class Graph:
    def __init__(self, vertices):
        self.V = vertices
        self.graph = {i: [] for i in range(self.V)}  # adjacency list

    def addEdge(self, u, v):
        # Assuming undirected graph; remove second append for directed graph
        self.graph[u].append(v)
        self.graph[v].append(u)

    def DFSUtil(self, v, visited, dfs_order):
        visited.add(v)
        dfs_order.append(v)

        for neighbor in self.graph[v]:
            if neighbor not in visited:
                self.DFSUtil(neighbor, visited, dfs_order)

    def DFS(self, start_vertex):
        visited = set()
        dfs_order = []
        self.DFSUtil(start_vertex, visited, dfs_order)
        return dfs_order


# Driver code
if __name__ == "__main__":
    g = Graph(6)
    g.addEdge(0, 1)
    g.addEdge(0, 2)
    g.addEdge(1, 3)
    g.addEdge(1, 4)
    g.addEdge(2, 4)
    g.addEdge(3, 5)
    g.addEdge(4, 5)

    start_vertex = 0
    print(f"DFS traversal starting from vertex {start_vertex}:")
    dfs_result = g.DFS(start_vertex)
    print(" -> ".join(map(str, dfs_result)))

```

## OUTPUT

![image](https://github.com/user-attachments/assets/3caca169-43ae-4205-b7eb-83f01cfba189)


## RESULT
The program successfully performs Depth-First Search (DFS) traversal on the graph starting from the specified source vertex and prints the vertices in the order they are visited. It uses recursion to explore as far as possible along each branch before backtracking.
