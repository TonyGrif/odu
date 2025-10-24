---
aliases:
  - np
classes:
  - DASC600
tags:
  - computing
  - python-library
  - scientific-computing
  - multidimensional-arrays
  - arrays
---
[Numpy](https://numpy.org/) is one of the fundamental [[Python]] packages for high-performance/scientific computing and data analysis. It is designed to work efficiently with large arrays of data by leveraging contiguous allocation of memory for the actual data within the array. Numpy also provides **vectorization**, the ability to batch operations on data without the need for loops.

Many packages (like [[Pandas]]) are built on top of this library or work in conjunction with it.
# Numpy Arrays
These are dense, continuous, uniformly sized blocks of identically typed data values that are fast and flexible for large datasets. Every array contains a shape and a datatype (`dtype`). In Numpy, arrays are an instance of a `ndarray` type object.
## Creating an Array
```python
import numpy as np

one_array = np.array([1,2,3])    # One dimensional array
two_array = np.array([[1,2,3][4,5,6]])    # Two dimensional array

numpy_from_list = np.arrange(pylist) # From Python List
```
Documentation: https://numpy.org/doc/stable/user/quickstart.html#quickstart-array-creation
## Reshaping
This method will create a new array with a new shape while preserving the data. The new shape **must** have the same number of elements as the initial array.
```python
import numpy as np

two_array = np.array([[1,2,3][4,5,6]])    # Two dimensional array
rearray = np.reshape(two_array, (3,2))  # Create a 3x2 array from the 2x3
```
Documentation: https://numpy.org/doc/stable/user/quickstart.html#quickstart-shape-manipulation
## Indexing and Slicing
Indexing and slicing provide a convenient and readable way to access a subset of data from an array.

**NOTE**: Numpy slices are the original data, meaning any changes you make to the slices will be reflected to the original array. To explicitly create a copy call the `.copy()` function. Certain advanced slices are exempt from this rule as the slices could target elements not contiguous in memory.
```python
import numpy as np

oned_array = np.array([1,2,3,4,5,6,7,8,9])
first = oned_array[0]
last = oned_array[-1]
subset = ond_array[2:5]
subset_copy = ond_array[2:5].copy()

twod_array = np.array([[1,2,3][4,5,6]])
first_row = twod_array[0,:]
first_col = twod_array[:,0]
```
Documentation: https://numpy.org/doc/stable/user/quickstart.html#quickstart-indexing-slicing-and-iterating
### Comparison Based Slicing
```python
array = np.array([[1,2,3][4,5,6]])

small = array[array < 2]
large = array[array > 4]
ends = array[(array < 2) & (array > 4)]
```
Documentation: https://numpy.org/doc/stable/user/quickstart.html#quickstart-indexing-slicing-and-iterating
## Operations
Any arithmetic operations between equal sized arrays applies the operation element-wise.
```python
import numpy as np

array = np.array([[1,2,3][4,5,6]])

mularray = array * array
subarray = array - array
```
Arithmetic operations between an array and a scalar will propagate the argument to each element in the array; this is known as **broadcasting**.
```python
import numpy as np

array = np.array([[1,2,3][4,5,6]])

scalarray = array * 2
```
Comparisons between equal sized arrays will return a boolean array of the same size.
```python
import numpy as np

array = np.array([[1,2,3][4,5,6]])
array_two = np.array([[6,5,4][3,2,1]])

comparray = array > array_two
```
Documentation: https://numpy.org/doc/stable/user/quickstart.html#quickstart-basic-operations
## Functions
Numpy comes builtin with a number of functions to operate on arrays.
```python
import numpy as np

array = np.array([[1,2,3][4,5,6]])

np.min(array)
np.max(array)

array.min()
array.max()
```
### Axis
Most functions in Numpy will perform the operation on a certain axis, being either rows or on columns. This can be changed in most functions using the `axis=` parameter.
```python
import numpy as np

array = np.array([[1,2,3][4,5,6]])

np.sum(array)
np.sum(array, axis=1)
```