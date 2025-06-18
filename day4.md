## Day 4: AI-Ready Functions

### Key Learnings
- functions, lambda, HOf, Clousers, 

### Code Snippet
```python
#Functions
def greet(name):
    return f"Hello, {name}!"
print(greet("Alice"))
# Prints: Hello, Alice! 

def greet(name='World'):
    return f"Hello, {name}!"

print(greet())  # Prints: Hello, World! 
print(greet("Alice"))  # Prints: Hello, Alice! 

def greet(first_name, last_name):
    return f"Hello, {first_name} {last_name}!"

print(greet(first_name='Alice', last_name='Johnson'))
# Prints: Hello, Alice Johnson! 

#*args & **kwargs
def add_numbers(*args):
    return sum(args)

print(add_numbers(1, 2, 3, 4))  # Prints: 10


def print_key_values(**kwargs):
    for key, value in kwargs.items():
        print(f'{key} = {value}')

print_key_values(name='Alice', age=30)
# Prints:
# name = Alice
# age = 30

#HOF
def apply(function, value):
    return function(value)

def square(x):
    return x * x

print(apply(square, 5))  # Prints: 25

#lambda
square = lambda x: x * x
print(square(5))  # Prints: 25

#clousers
def outer(x):
    def inner(y):
        return x + y
    return inner

add5 = outer(5)
print(add5(10))  # Prints: 15
