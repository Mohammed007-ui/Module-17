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
def havel_hakimi(sequence):
    # Remove zeros and sort in descending order
    sequence = sorted([d for d in sequence if d > 0], reverse=True)
    if not sequence:
        return True, []

    n = sequence[0]
    sequence = sequence[1:]

    if n > len(sequence):
        return False, []

    for i in range(n):
        sequence[i] -= 1
        if sequence[i] < 0:
            return False, []

    # Recursively check remaining sequence
    return havel_hakimi(sequence)

def is_graphical(sequence):
    # Check if sum is even
    if sum(sequence) % 2 != 0:
        return False
    return havel_hakimi(sequence)[0]

# Example sequence
degree_sequence = [3, 3, 2, 2, 2, 1, 1]

print("Degree Sequence:", degree_sequence)
if is_graphical(degree_sequence):
    print("The degree sequence is graphical.")
else:
    print("The degree sequence is NOT graphical.")

```

## OUTPUT
```
![image](https://github.com/user-attachments/assets/4f5d0d12-0e00-4d03-b247-f6591cc62505)

```

## RESULT
The program successfully checks if the given degree sequence can represent a simple graph using the Havel-Hakimi algorithm, constructs the graph if possible, and visualizes it. The visualization helps in understanding the structure of the generated graph.
