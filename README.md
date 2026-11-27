# EX 11: Implementation of the Huffman Coding Algorithm

## DEVELOPED BY:
## NAME: DAKSHA SUBBAIAN
## REGISTER NUMBER: 212223230036

## **Aim**

To implement Huffman coding to compress the data using Python.

## **Software Required**

1\. Anaconda – Python 3.7

## **Algorithm**

### **Step 1:**

Initialize the input string and calculate the frequency of occurrence of each character using a dictionary.

### **Step 2:**

Create individual tree nodes for each character along with its corresponding frequency.

### **Step 3:**

Sort the nodes based on their frequencies. Combine the two nodes with the lowest frequencies to form a new node. Repeat this process until a single Huffman tree is formed.

### **Step 4:**

Traverse the Huffman tree recursively by assigning 0 to the left branch and 1 to the right branch to generate Huffman codes for each character.

### **Step 5:**

Display each character and its corresponding Huffman code.

## **Program**

```
# Get the input string
input_string = "DAKSHA SUBBAIAN"

# Calculate frequency of occurrence
frequency = {}
for char in input_string:
    if char in frequency:
        frequency[char] += 1
    else:
        frequency[char] = 1

# Create tree nodes
nodes = [[char, freq] for char, freq in frequency.items()]

# Main function to implement Huffman coding
while len(nodes) > 1:
    nodes = sorted(nodes, key=lambda x: x[1])

    left = nodes.pop(0)
    right = nodes.pop(0)

    new_node = [[left, right], left[1] + right[1]]
    nodes.append(new_node)

# The final node is the Huffman tree
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

# Print the characters and their Huffman codes
print("Character | Huffman Code")
print("-------------------------")
for char, code in huffman_codes.items():
    print(f"    {char}    |    {code}")
```

## **Output**

<img width="257" height="273" alt="image" src="https://github.com/user-attachments/assets/d9a5f867-8040-4b5a-8fb6-bd47ddc602d6" />

## **Result**

Thus, the Huffman coding algorithm was successfully implemented to compress the data using Python programming.
