# Huffman Encoding using Greedy Strategy

#### Time Complexity -> O(nlogn)
#### Space Complexity -> O(n)

```
class node():
    def __init__(self, left=None, right=None, huff='', symbol='', f=-1):
        self.left = left
        self.right = right
        self.huff = huff
        self.symbol = symbol
        self.freq = f

def printNodes(node, val=''):
	newVal = val + node.huff
	if(node.left):
		printNodes(node.left, newVal)
	if(node.right):
		printNodes(node.right, newVal)
	if(not node.left and not node.right):
		print(f"{node.symbol} -> {newVal}")
		
# characters for huffman tree
chars = ['a', 'b', 'c', 'd', 'e', 'f', 'g']

# frequency of characters
freq = [ 4, 7, 12, 14, 17, 43, 54]

# list containing unused nodes
nodes = []

# converting characters and frequencies into huffman tree nodes
for x in range(len(chars)):
	nodes.append(node(f = freq[x], symbol = chars[x]))

while len(nodes) > 1:
	# sort all the nodes in ascending order based on their frequency
	nodes = sorted(nodes, key=lambda x: x.freq)

	# pick 2 smallest nodes
	left = nodes[0]
	right = nodes[1]

	# assign directional value to these nodes
	left.huff = '0'
	right.huff = '1'
# combine the 2 smallest nodes to create new node as their parent
	newNode = node(left, right,'', left.symbol+right.symbol, left.freq+right.freq,)

	# remove the 2 nodes and add their parent as new node among others
	nodes.remove(left)
	nodes.remove(right)
	nodes.append(newNode)

printNodes(nodes[0])
```
