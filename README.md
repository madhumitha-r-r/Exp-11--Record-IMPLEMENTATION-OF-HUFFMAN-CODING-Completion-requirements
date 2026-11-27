# Implementation of Huffman Coding Algorithm

## Aim
To implement the Huffman Coding algorithm using Python to generate variable-length binary codes based on the frequency of characters.

## Software Requirements
- Python
- Jupyter Notebook
- OpenCV
- NumPy

## Theory
Huffman Coding is a lossless data compression technique used to reduce the size of data.

It assigns shorter binary codes to frequently occurring characters and longer binary codes to less frequently occurring characters.

## Algorithm
1. Initialize the input string.
2. Calculate the frequency of each character.
3. Create tree nodes for each character and its frequency.
4. Sort the nodes based on frequency.
5. Select the two nodes with the smallest frequencies.
6. Combine them into a new node.
7. Repeat until a single Huffman tree is formed.
8. Generate binary codes by traversing the tree.
9. Display the characters and their corresponding Huffman codes.

## Program 
### Developed by
#### Name : MADHUMITHA R R
#### Reg no : 212224240083

```python
import cv2
import numpy

input_string = "MADHUMITHA R R"

# Calculate frequency of each character
frequency = {}
for char in input_string:
    if char in frequency:
        frequency[char] += 1
    else:
        frequency[char] = 1

# Create tree nodes
nodes = [[char, freq] for char, freq in frequency.items()]

# Build Huffman tree
while len(nodes) > 1:
    nodes = sorted(nodes, key=lambda x: x[1])

    left = nodes.pop(0)
    right = nodes.pop(0)

    new_node = [[left, right], left[1] + right[1]]
    nodes.append(new_node)

huffman_tree = nodes[0]

# Generate Huffman codes
huffman_codes = {}

def generate_codes(tree, code=""):
    if isinstance(tree[0], str):
        huffman_codes[tree[0]] = code
    else:
        generate_codes(tree[0][0], code + "0")
        generate_codes(tree[0][1], code + "1")

generate_codes(huffman_tree)

# Display Huffman codes
print("Character | Huffman Code")
print("-------------------------")

for char, code in huffman_codes.items():
    print(f"    {char}    |    {code}")
```

## Output

<img width="215" height="232" alt="image" src="https://github.com/user-attachments/assets/ced68e56-185b-4cbb-8e06-0534489f531d" />


## Result
Thus, the Huffman Coding algorithm was successfully implemented using Python. The frequency of each character was calculated, a Huffman tree was constructed, and corresponding binary codes were generated.
