# Ex. No: 17A - Generate a Graph for a Given Fixed Degree Sequence

## AIM:
To write a Python program to generate a graph for a given **fixed degree sequence**.

## ALGORITHM:

**Step 1**: Start the program.

**Step 2**: Check if the sum of the degree sequence is even.  
> (A necessary condition for the sequence to be graphical.)

- If not even, print an error message and exit the program.

**Step 3**: Use the **Havel-Hakimi algorithm** to determine whether a simple graph can be constructed from the sequence, and to generate the graph.

**Step 4**: If the graph is successfully created, **visualize it** using a graph drawing function (e.g., `networkx.draw()`).

**Step 5**: End the program.

## PYTHON PROGRAM

```
# Function to check if the sum of the degree sequence is even
def is_valid_degree_sequence(degree_sequence):
    if sum(degree_sequence) % 2 != 0:
        return False
    return True

# Function to apply the Havel-Hakimi algorithm to generate the graph
def generate_graph(degree_sequence):
    # Sort the degree sequence in non-increasing order
    degree_sequence.sort(reverse=True)
    
    # List to store edges of the graph
    edges = []
    
    # While there are vertices left to process
    while degree_sequence and degree_sequence[0] > 0:
        # Remove the first vertex with the highest degree
        max_degree = degree_sequence.pop(0)
        
        # If there are not enough vertices to connect, it's an invalid degree sequence
        if max_degree > len(degree_sequence):
            return "Degree sequence is not graphical"
        
        # Connect this vertex with the next `max_degree` vertices
        for i in range(max_degree):
            degree_sequence[i] -= 1
            # Add an edge between the first vertex and the `i`-th vertex
            edges.append((0, i + 1))
        
        # Sort the sequence again after modifying it
        degree_sequence.sort(reverse=True)
    
    return edges

# Main program
def main():
    degree_sequence = [3, 3, 2, 2, 2]
    
    # Step 1: Check if the degree sequence is valid
    if not is_valid_degree_sequence(degree_sequence):
        print("Error: The sum of the degree sequence is odd, invalid input!")
        return
    
    # Step 2: Generate the graph from the degree sequence
    edges = generate_graph(degree_sequence)
    
    if isinstance(edges, str):  # If it's an error message
        print(edges)
    else:
        print("Graph edges:")
        for edge in edges:
            print(edge)

# Run the program
main()

```

## OUTPUT

![image](https://github.com/user-attachments/assets/0dbde78e-ebfa-494e-abc0-5a1b90907c52)


## RESULT
The Python program successfully generates a graph for the given fixed degree sequence using the Havel-Hakimi algorithm and visualizes the result.
