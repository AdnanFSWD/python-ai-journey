## Day 4: Numpy Cheet Codes

### Key Learnings
- Numpy: NumPy is used to work with arrays. The array object in NumPy is called ndarray.

### Code Snippet
```python

import numpy as np

# --- 1. Array Creation ---

# From a list or tuple
arr1 = np.array([1, 2, 3, 4])
arr2 = np.array([[1, 2], [3, 4]])
print(f"arr2: {arr2}")

# Zeros, Ones, Empty
zeros_arr = np.zeros((3, 4))      # 3x4 array of zeros
print(f"zeros_arr: {zeros_arr}")
ones_arr = np.ones((2, 2))        # 2x2 array of ones
print(f"ones_arr: {ones_arr}")
empty_arr = np.empty((2, 3))      # 2x3 array, uninitialized (fast)
print(f"empty_arr: {empty_arr}")

# Range and Linspace
arange_arr = np.arange(0, 10, 2)  # [0, 2, 4, 6, 8] (start, stop (exclusive), step)
print(f"arange_arr: {arange_arr}")
linspace_arr = np.linspace(0, 1, 5) # 5 evenly spaced points between 0 and 1 (inclusive)
print(f"linspace_arr: {linspace_arr}")

# Random Arrays
rand_arr = np.random.rand(3, 3)   # 3x3 array of random floats between 0 and 1
randn_arr = np.random.randn(2, 2) # 2x2 array of random floats from standard normal distribution
randint_arr = np.random.randint(0, 10, (2, 3)) # 2x3 array of random integers between 0 (inclusive) and 10 (exclusive)

# Identity matrix
identity_mat = np.eye(3)          # 3x3 identity matrix

# --- 2. Array Attributes ---

arr = np.array([[1, 2, 3], [4, 5, 6]])

print(f"Shape: {arr.shape}")       # (rows, columns) e.g., (2, 3)
print(f"Dimensions: {arr.ndim}")   # Number of dimensions e.g., 2
print(f"Size: {arr.size}")         # Total number of elements e.g., 6
print(f"Data Type: {arr.dtype}")   # e.g., int64, float64

# --- 3. Indexing and Slicing ---

arr = np.array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
matrix = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])

# Single element indexing
print(arr[0])      # 0
print(matrix[0, 1]) # 2

# Slicing (start:stop:step)
print(arr[2:5])    # [2 3 4]
print(arr[:5])     # [0 1 2 3 4] (from beginning)
print(arr[5:])     # [5 6 7 8 9] (to end)
print(arr[::2])    # [0 2 4 6 8] (every second element)
print(arr[::-1])   # [9 8 7 6 5 4 3 2 1 0] (reversed)

# 2D Array Slicing
print(matrix[0:2, 1:3])  # [[2 3], [5 6]] (rows 0-1, columns 1-2)
print(matrix[:, 0])     # [1 4 7] (all rows, first column)
print(matrix[1, :])     # [4 5 6] (second row, all columns)

# Boolean Indexing
arr = np.array([10, 20, 30, 40, 50])
greater_than_20 = arr[arr > 20] # [30 40 50]

# Fancy Indexing
indices = [0, 2, 4]
selected_elements = arr[indices] # [10 30 50]

# --- 4. Array Manipulation ---

arr1 = np.array([1, 2, 3])
arr2 = np.array([4, 5, 6])

# Reshaping
reshaped_arr = arr1.reshape((3, 1)) # Converts to a column vector

# Stacking
stacked_h = np.hstack((arr1, arr2)) # [1 2 3 4 5 6] (horizontal stack)
stacked_v = np.vstack((arr1, arr2)) # [[1 2 3], [4 5 6]] (vertical stack)

# Splitting
split_arr_h = np.hsplit(stacked_h, 2) # [array([1, 2, 3]), array([4, 5, 6])]
split_arr_v = np.vsplit(stacked_v, 2) # [array([[1, 2, 3]]), array([[4, 5, 6]])]

# Transposing
matrix = np.array([[1, 2], [3, 4]])
transposed_matrix = matrix.T # [[1 3], [2 4]]

# Adding/Removing dimensions
expanded_dims = np.expand_dims(arr1, axis=0) # [[1 2 3]] (adds a new axis at the beginning)
squeezed_arr = np.squeeze(reshaped_arr)    # [1 2 3] (removes single-dimensional entries)

# Flattening
flattened_arr = matrix.flatten() # [1 2 3 4] (returns a copy)
raveled_arr = matrix.ravel()     # [1 2 3 4] (returns a view if possible, otherwise a copy)

# --- 5. Mathematical Operations ---

arr1 = np.array([1, 2, 3])
arr2 = np.array([4, 5, 6])

# Element-wise operations
add_arr = arr1 + arr2      # [5 7 9]
sub_arr = arr2 - arr1      # [3 3 3]
mul_arr = arr1 * arr2      # [4 10 18]
div_arr = arr2 / arr1      # [4.  2.5 2. ]
power_arr = arr1 ** 2      # [1 4 9]

# Universal Functions (ufuncs)
sqrt_arr = np.sqrt(arr1)
sin_arr = np.sin(arr1)
log_arr = np.log(arr1)

# Aggregation functions
arr = np.array([1, 2, 3, 4, 5])
print(f"Sum: {np.sum(arr)}")       # 15
print(f"Mean: {np.mean(arr)}")     # 3.0
print(f"Max: {np.max(arr)}")       # 5
print(f"Min: {np.min(arr)}")       # 1
print(f"Std Dev: {np.std(arr)}")   # Standard deviation
print(f"Variance: {np.var(arr)}")  # Variance

# Aggregation along axes
matrix = np.array([[1, 2, 3], [4, 5, 6]])
sum_rows = np.sum(matrix, axis=0)  # [5 7 9] (sum of columns)
sum_cols = np.sum(matrix, axis=1)  # [ 6 15] (sum of rows)

# Dot product (matrix multiplication)
mat1 = np.array([[1, 2], [3, 4]])
mat2 = np.array([[5, 6], [7, 8]])
dot_product = np.dot(mat1, mat2)
# Or using the @ operator (Python 3.5+)
dot_product_at = mat1 @ mat2

# --- 6. Broadcasting ---

# When performing operations on arrays of different shapes, NumPy attempts to broadcast.
arr_scalar = np.array([1, 2, 3]) + 10 # [11 12 13] (scalar is broadcast)

arr_row = np.array([[1, 2, 3]])
arr_col = np.array([[10], [20]])
# This will result in an error without proper broadcasting rules
# If shapes are compatible, broadcasting will extend the smaller array's dimensions
# Example:
a = np.array([[0,0,0],[10,10,10],[20,20,20],[30,30,30]])
b = np.array([1,2,3])
c = a + b # b is broadcast across each row of a

# --- 7. Copying Arrays ---

arr = np.array([1, 2, 3])
view_arr = arr.view() # Creates a view (changes to view_arr affect arr)
copy_arr = arr.copy() # Creates a deep copy (changes to copy_arr do NOT affect arr)

# --- 8. Saving and Loading Arrays ---

# np.save('my_array.npy', arr)
# loaded_arr = np.load('my_array.npy')

# np.savetxt('my_array.txt', arr, delimiter=',')
# loaded_txt_arr = np.loadtxt('my_array.txt', delimiter=',')

# --- 9. Useful Functions and Constants ---

print(f"Pi: {np.pi}")
print(f"Euler's number: {np.e}")
print(f"Not a Number: {np.nan}")
print(f"Infinity: {np.inf}")

# Check for NaN or Inf
# print(np.isnan(np.array([1, np.nan])))
# print(np.isinf(np.array([1, np.inf])))

# Where
x = np.arange(9).reshape((3,3))
print(f"Where: {np.where(x > 5, 100, x)}") # if x > 5, replace with 100, else keep x

# Unique
unique_elements = np.unique([1, 1, 2, 3, 2, 4]) # [1 2 3 4]

# Sorting
sorted_arr = np.sort([3, 1, 2]) # [1 2 3]

# Argmax/Argmin (indices of max/min)
print(f"Argmax: {np.argmax(arr)}")
print(f"Argmin: {np.argmin(arr)}")

# Clamp/Clip
clipped_arr = np.clip(np.array([1, 10, 20]), 5, 15) # [ 5 10 15] (values outside [5, 15] are clipped)

# All/Any
print(f"All elements > 0: {np.all(arr > 0)}")
print(f"Any element > 5: {np.any(arr > 5)}")
