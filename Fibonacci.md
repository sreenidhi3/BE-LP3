
# Iterative Fibonacci Algorithm
### The time complexity of the above code is T(N), i.e., linear. 
#####We have to find the sum of two terms, and it is repeated n times depending on the value of n.
###The space complexity of the above code is O(N).
```
def iterative_fibonacci(n):
    a, b = 0, 1 
    print(a)
    print(b)
    for i in range(n-2):
        c = a+b
        print(c)
        a = b 
        b = c
    return
```

# Recursive Fibonacci Algorithm
### The time complexity of the above code is T(2^N), i.e., exponential.
### The Space complexity of the above code is O(1) for a recursive series.

```
def recursive_fibonacci(n):
    if(n <= 1):
        return n
    else:
        return(recursive_fibonacci(n-1) + recursive_fibonacci(n-2))
```
```
n = int(input("Enter number of terms:"))

print("Fibonacci sequence using Recursive Method:")
for i in range(n):
    print(recursive_fibonacci(i))
    

print("\nFibonacci sequence using Iterative Method: ")
iterative_fibonacci(n)
```
