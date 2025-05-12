# Ex. No: 17D - Topological Sorting of a DAG

## AIM:
To write a Python program to **print topological sorting** of a **Directed Acyclic Graph (DAG)**.

## ALGORITHM:

**Step 1**: Create a graph and add edges to represent relationships between nodes.

**Step 2**: Use a `visited` set to keep track of visited nodes and a **stack** (or list) to record the **order of nodes** after processing.

**Step 3**: Perform **DFS** for each unvisited node:
- Explore all its neighbors.
- Recursively apply DFS to each unvisited adjacent node.
- After all neighbors are visited, **push the current node onto the stack**.

**Step 4**: After DFS is complete for all nodes, the stack will contain nodes in **reverse order of their completion time**.

**Step 5**: Print the stack in **reverse** to get the **topological order**.

---

## PYTHON PROGRAM

```
# Class to represent the graph
class Graph:
    def __init__(self, vertices):
        self.V = vertices  # number of vertices
        self.graph = {i: [] for i in range(vertices)}  # adjacency list

    # Add an edge to the graph
    def add_edge(self, u, v):
        self.graph[u].append(v)

    # Helper function for DFS
    def dfs_util(self, v, visited, stack):
        visited[v] = True
        # Recursively visit all the adjacent vertices
        for neighbor in self.graph[v]:
            if not visited[neighbor]:
                self.dfs_util(neighbor, visited, stack)
        # After visiting all neighbors, push the current vertex to stack
        stack.append(v)

    # Function to perform topological sort
    def topological_sort(self):
        visited = [False] * self.V  # Track visited vertices
        stack = []  # Stack to store the topological order
        
        # Call the recursive helper function for all unvisited vertices
        for i in range(self.V):
            if not visited[i]:
                self.dfs_util(i, visited, stack)
        
        # Reverse the stack to get the correct topological order
        return stack[::-1]


# Driver code
def main():
    # Create a graph with 6 vertices
    g = Graph(6)

    # Add edges to the graph
    g.add_edge(5, 2)
    g.add_edge(5, 0)
    g.add_edge(4, 0)
    g.add_edge(4, 1)
    g.add_edge(2, 3)
    g.add_edge(3, 1)

    # Perform topological sort and print the result
    top_order = g.topological_sort()
    print("Topological Sorting of the given DAG:")
    print(top_order)

# Run the program
main()

```

## OUTPUT

![image](https://github.com/user-attachments/assets/16e5bb36-014e-45f6-a911-c3bc5e56ff3a)


## RESULT
The Python program successfully generates a graph for the given fixed degree sequence using the Havel-Hakimi algorithm and visualizes the result.








