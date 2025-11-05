# Huffman-Coding
# Developed By: Daniel C
# Reg No: 212223240023
## Aim
To implement Huffman coding to compress the data using Python.

## Software Required
1. Anaconda - Python 3.7

## Algorithm:
### Step1:
Get the input string.

### Step2:
Create tree nodes.

### Step3:
Main function to implement huffman coding.

### Step4:
calculate frequency of occurence.

### Step5:
print the characters and its huffmancode.
 
## Program:

``` Python
# Developed By: Daniel C
# reg no: 212223240023

# Input String
string = "DANIEL"

# Define NodeTree class
class NodeTree(object):
    def __init__(self, left=None, right=None):
        self.left = left
        self.right = right

    def children(self):
        return (self.left, self.right)

    def nodes(self):
        return (self.left, self.right)

    def __str__(self):
        return '%s %s' % (self.left, self.right)

# Function to generate Huffman codes
def huffman_code_tree(node, left=True, binString=''):
    if type(node) is str:
        return {node: binString}
    (l, r) = node.children()
    d = dict()
    d.update(huffman_code_tree(l, True, binString + '0'))
    d.update(huffman_code_tree(r, False, binString + '1'))
    return d

# Step 1: Calculate frequency of each character
freq = {}
for c in string:
    freq[c] = freq.get(c, 0) + 1

# Step 2: Sort frequencies in descending order
freq = sorted(freq.items(), key=lambda x: x[1], reverse=True)

# Step 3: Build Huffman Tree
nodes = freq
while len(nodes) > 1:
    (key1, c1) = nodes[-1]
    (key2, c2) = nodes[-2]
    nodes = nodes[:-2]
    node = NodeTree(key1, key2)
    nodes.append((node, c1 + c2))
    nodes = sorted(nodes, key=lambda x: x[1], reverse=True)

# Step 4: Generate and print Huffman codes
huffmanCode = huffman_code_tree(nodes[0][0])

print('Char | Huffman Code')
print('------------------')
for (char, frequency) in freq:
    print(f'{char:4} | {huffmanCode[char]}')

```
## Output:

### Print the characters and its huffmancode
<img width="266" height="191" alt="image" src="https://github.com/user-attachments/assets/3c85dcab-8836-4cb7-aaa0-a63b54a44b09" />




## Result
Thus the huffman coding was implemented to compress the data using python programming.
