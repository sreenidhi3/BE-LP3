'''
def recursive_fibo(n):
    if n <=1:
        return n
    return recursive_fibo(n-1) + recursive_fibo(n-2)

n=int(input("Enter a number: "))
for i in range(n):
    print(recursive_fibo(i), end=" ")

print()

def iterative_fibo(n):
    a , b = 0, 1
    print(a, end=" ")
    print(b, end=" ")
    for i in range(n-2):
        c = a + b;
        a, b =b, c
        print(c,  end=" ")

iterative_fibo(n)
        
'''

# ----------------------------

'''
class node:
    def __init__(self, symbol, freq, left=None, right=None, huff=''):
        self.symbol = symbol
        self.freq = freq
        self.left = left
        self.right = right
        self.huff = huff
    
# calculating prefix code
def printNodes(node, val=''):
    newVal = val+node.huff
    if node.left:
        printNodes(node.left, newVal)
    if node.right:
        printNodes(node.right, newVal)
    if not node.left and not node.right:
        print(node.symbol + " -> " + newVal)

chars = ['a', 'b', 'c', 'd']
freq = [13, 4, 3, 22]

nodes =[]        

# creates a node for each character
for x in range(len(chars)):
    nodes.append(node(chars[x], freq[x]))
    
# create a Huffman Tree
while len(nodes) > 1:
    # sort all nodes in ascending order
    nodes =  sorted(nodes, key=lambda x: x.freq)
    
    # take first 2 min nodes
    left = nodes[0]
    right = nodes[1]
    
    # assigning code based on direction
    left.huff='0'
    right.huff='1'
    
    newNode = node('N/A', -1, left, right)
    
    nodes.remove(left)
    nodes.remove(right)
    nodes.append(newNode)
    
printNodes(nodes[0])
'''

# ----------------------------

'''

weights = [40, 10, 20, 24]
profits = [280, 100, 120, 120]
maxWeight = 60

ratios = []
for i in range(len(weights)):
    ratios.append([weights[i], profits[i], weights[i]/profits[i], 0])

ratios = sorted(ratios, key= lambda x: x[2])

w = 0
p = 0
while w < maxWeight:
    item = ratios.pop(0)
    if(w+item[0] < maxWeight):
        if(item[3] == 0):
            w = w + item[0]
            p = p + item[1]
            item[3] = 1
            ratios.append(item)
    else:
        p = p + ((maxWeight - w)/item[0] * item[1])
        w = w + (maxWeight - w)
        item[3] = (maxWeight - w)/item[0]
        ratios.append(item)
        
print(ratios)
'''

# ----------------------------

'''

profits = [3, 4, 5, 6]
weights = [2, 3, 4, 5]
W = 5
n = len(profits)

def KnapsackDP(W, weights, profits, n):
    V = [[0 for i in range(W+1)] for i in range(n+1)]
    
    for i in range(1, n+1):
        for w in range(1, W+1):
            if weights[i-1] <=w:
                V[i][w] = max(profits[i-1] + V[i-1][w-weights[i-1]], V[i-1][w])
            else :
                V[i][w] = V[i-1][w]
    # print(V)
    # print(itemsChosen(V, n, W))
    return V[n][W]
    
def itemsChosen(V, n, W):
    items = [0 for i in range(n)]
    
    i, j = n, W
    w = W
    while(w>0):
        if(V[i][j] == V[i-1][j]):
            i=i-1
        else:
            while(V[i][j] == V[i][j-1]):
                j = j-1
            else:
                
            # if(V[i][j] == V[i][j-1]):
            #     print("rows ", V[i][j], V[i][j-1])
            #     j = j-1
            # else:
               items[i-1] = 1
               w = w - i
            #   print(w)
               i = i - 1
               j = j - 1
    return items
    
print(KnapsackDP(W, weights, profits, n))

'''
# ----------------------------

'''
import random

def quicksortR(arr, start, end):
    if(start<end):
        pivot = partitionR(arr, start, end)
        quicksortR(arr, start, pivot-1)
        quicksortR(arr, pivot+1, end)
    return arr

def partitionR(arr, start, end):
    pivotIndex = random.randrange(start, end)
    arr[start], arr[pivotIndex] = arr[pivotIndex], arr[start]
    return partition(arr, start, end)
    
def quicksort(arr, start, end):
    if(start<end):
        pivot = partition(arr, start, end)
        quicksort(arr, start, pivot-1)
        quicksort(arr, pivot+1, end)
    return arr

def partition(arr, start, end):
    pivot = arr[start]
    i = start+1
    j = end
    while(i<j):
        while(arr[i]<pivot and i<end):
            i = i+1
        while(arr[j]>pivot and j>start):
            j = j-1
        if(i<j):
            arr[i], arr[j] = arr[j], arr[i]
    arr[start], arr[j] = arr[j], arr[start]
    return j

print(quicksort([ 1,5,2,4,8], 0, 4))
print(quicksortR([ 1,5,2,4,8], 0, 4))

'''
