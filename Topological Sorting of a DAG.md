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
# Ex. No: 17D - Topological Sorting of a DAG

# AIM:
# To write a Python program to print topological sorting of a Directed Acyclic Graph (DAG).

from collections import defaultdict

class Graph:
    def __init__(self, vertices):
        self.graph = defaultdict(list)  # adjacency list
        self.V = vertices               # number of vertices

    def addEdge(self, u, v):
        self.graph[u].append(v)

    def topologicalSortUtil(self, v, visited, stack):
        visited.add(v)
        for neighbour in self.graph[v]:
            if neighbour not in visited:
                self.topologicalSortUtil(neighbour, visited, stack)
        stack.append(v)

    def topologicalSort(self):
        visited = set()
        stack = []

        for vertex in range(self.V):
            if vertex not in visited:
                self.topologicalSortUtil(vertex, visited, stack)

        # Return reversed stack as topological order
        return stack[::-1]

# Example Usage
g = Graph(6)
g.addEdge(5, 2)
g.addEdge(5, 0)
g.addEdge(4, 0)
g.addEdge(4, 1)
g.addEdge(2, 3)
g.addEdge(3, 1)

print("Topological Sort of the given DAG:")
print(g.topologicalSort())

```

## OUTPUT

![image](https://github.com/user-attachments/assets/736627c7-3bb7-45dc-be6d-67da9294bc07)


## RESULT
The program successfully performs topological sorting on a given Directed Acyclic Graph (DAG) and prints the vertices in an order such that for every directed edge from vertex u to vertex v, u comes before v in the ordering.
