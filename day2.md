# Day 2: Python Lists & Loops

## Key Differences from JS
- `arr.append(x)` instead of `arr.push(x)`.
- List comprehensions (`[x*2 for x in arr]`) replace `map/filter`.
- Slicing is simpler (`arr[1:3]` vs `arr.slice(1, 3)`).

## Code Snippets
```python
arr = [1, 2, 3, 4, 5]
arr.append(6)   #[1, 2, 3, 4, 5, 6]
arr.remove(2)  #[1, 3, 4, 5, 6]
print(arr[0:3], "Slicing") # Output: [1, 3, 4]
print(arr[:3])   # Output: [1, 3, 4]
print(arr[1:])   # Output: [3, 4, 5, 6]
print(arr[-1])   # Output: 6
print(arr) # Output: [1, 3, 4, 5, 6]


# List comprehensions
squared = [x ** 2 for x in arr]
multiple = [x * 2 for x in arr]
evens = [x for x in arr if x % 2 == 0]
print(evens)    # Output: [4, 6]
print(squared)  # Output: [1, 9, 16, 25, 36]
print(multiple)  # Output: [2, 6, 8, 10, 12]

fruits = ["apple", "banana", "cherry"]
fruits.append("orange") # fruits = ["apple", "banana", "cherry", "orange"]

# Loop through a list
for fruit in fruits:
    print(fruit)

  #Output: 
    apple
    banana
    cherry
    orange

# Loop with index (like JS for-i loop)
for i, fruit in enumerate(fruits):
    print(f"{i + 1} - {fruit}")

  #Output: 
    1 - apple
    2 - banana
    3 - cherry
    4 - orange


for x in range(6):
  print(x) # Output: 0, 1, 2, 3, 4, 5

