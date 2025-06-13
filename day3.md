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

# Update Tuple coordinates
coordinates = (3.5, 8.2) 
coordinates[0] = 5.0  # This will raise an error because tuples are immutable 
coordinates = (coordinates[0] + 1.5, coordinates[1] - 2.2)  # Update coordinates
print(coordinates)  # Output: (5.0, 6.0)
