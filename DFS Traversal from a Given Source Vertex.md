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
        self.V = vertices  # Number of vertices
        self.graph = {i: [] for i in range(vertices)}  # Dictionary to store the adjacency list

    def add_edge(self, src, dest):
        # Add an edge to the graph (undirected)
        self.graph[src].append(dest)
        self.graph[dest].append(src)

    def DFSUtil(self, v, visited):
        # Mark the current node as visited and print it
        visited.add(v)
        print(v, end=" ")

        # Recur for all the vertices adjacent to this vertex
        for neighbor in self.graph[v]:
            if neighbor not in visited:
                self.DFSUtil(neighbor, visited)

    def DFS(self, start_vertex):
        # Initialize the visited set
        visited = set()
        # Call the recursive DFSUtil function
        print("DFS Traversal starting from vertex", start_vertex)
        self.DFSUtil(start_vertex, visited)

# Example usage
if __name__ == "__main__":
    # Create a graph given the number of vertices
    g = Graph(5)
    g.add_edge(0, 1)
    g.add_edge(0, 4)
    g.add_edge(1, 2)
    g.add_edge(1, 3)
    g.add_edge(2, 3)

    # Start DFS traversal from vertex 0
    g.DFS(0)

```

## OUTPUT

![image](https://github.com/user-attachments/assets/24daf5bc-7678-45ff-b92e-d9b1f8a10c21)


## RESULT
Thus, the Python program successfully performs a DFS traversal starting from a given source vertex and prints the vertices in the order they are visited.
