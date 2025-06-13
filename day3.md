# Day 3: Dictionaries & Tuples

## Key Insights
- Dictionaries = JS objects, but use `obj["key"]` instead of `obj.key`.
- `.get()` avoids `KeyError` (like `?.` in JS).
- Tuples are immutable (like frozen JS arrays).

## Code Snippets
```python
# Dictionary merging
defaults = {"theme": "dark", "font": "Arial"}
user_settings = {"font": "Roboto"}
final_settings = {**defaults, **user_settings}  # {"theme": "dark", "font": "Roboto"}

object = {
    "name": "example",
    "description": "This is an example object.",
    "version": 1,
    "data": {
        "key1": "value1",
    },
    "is_active": True,
    "tags": ["example", "sample"],
}

object["data"]["key2"] = "value2"
object["is_active"] = False
object["tags"].append("new_tag")
object.get("language", "Python") # Default value if 'language' key does not exist
object.update({"version": 2, "language": "JavaScript", "is_visible": True}) # Update object with new keys and values
print(object.keys()) # Output: dict_keys(['name', 'description', 'version', 'data', 'is_active', 'tags', 'language', 'is_visible'])
print(object.values()) # Output: ['example', 'This is an example object.', 2, {'key1': 'value1', 'key2': 'value2'}, False, ['example', 'sample', 'new_tag'], 'JavaScript', True]
print(object.items()) # Output: dict_items([('name', 'example'), ('description', 'This is an example object.'), ('version', 2), ('data', {'key1': 'value1', 'key2': 'value2'}), ('is_active', False), ('tags', ['example', 'sample', 'new_tag']), ('language', 'JavaScript'), ('is_visible', True)])
print(object)

# Create a dictionary
my_dict = {"apple": 1, "banana": 2, "cherry": 3}
print(my_dict["apple"])  # Output: 1
# Update a value
my_dict["apple"] = 100
# Insert a new key-value pair
my_dict["date"] = 4
# Delete a key-value pair
del my_dict["banana"]
print(my_dict)  # Output: {'apple': 100, 'cherry': 3, 'date': 4}

# Loop through keys
for key in my_dict:
    print(f"Key: {key}")

# Loop through values
for value in my_dict.values():
    print(f"Value: {value}")

# Loop through key-value pairs
for key, value in my_dict.items():
    print(f"{key} -> {value}")

# Get with fallback
print(my_dict.get("apple", 0))  # 100
print(my_dict.get("banana", 0))  # 0 (since it's gone)

# Check for key
if "apple" in my_dict:
    print("apple exists")

# Clear all
my_dict.clear()
print(my_dict)  # {}

# Nested dictionaries:
companies = {
    "Google": {"CEO": "Sundar Pichai", "Established": 1998},
    "Amazon": {"CEO": "Andy Jassy", "Established": 1994},
}

print(companies["Google"]["CEO"])  # Sundar Pichai

#Comprehensive dictionaries (dict comprehensions)
squares = {i: i * i for i in range(5)}
print(squares)  # {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}

#Merging dictionaries (Python 3.9+):
dict1 = {"apple": 1}
dict2 = {"banana": 2}

merged = dict1 | dict2
print(merged)  # {"apple": 1, "banana": 2}

# Update Tuple coordinates
coordinates = (3.5, 8.2)

for item in coordinates:
    print(item)

# Count number of a particular item
print(coordinates.count(3.5))  # 1

# Find index of first match
print(coordinates.index(8.2))  # 1

x, y = coordinates
print(x)  # 5
print(y)  # 10

coordinates[0] = 5.0  # This will raise an error because tuples are immutable 
coordinates = (coordinates[0] + 1.5, coordinates[1] - 2.2)  # Update coordinates
print(coordinates)  # Output: (5.0, 6.0)

matrix:[
 [1, 2, 3],
 [4, 5, 6],
 [7, 8, 9]
]
# matrix[1] means “give me the second row” (since indexing starts at 0)
matrix[0] == (1, 2, 3)
matrix[1] == (4, 5, 6)
matrix[2] == (7, 8, 9)
print(matrix[1][1])  # Prints 5

