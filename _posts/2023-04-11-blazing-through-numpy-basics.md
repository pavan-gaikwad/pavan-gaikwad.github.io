---
layout: post
title:  "Blazing through numpy basics"
date:   2023-04-11 21:48:43 +0530
categories: ml, ai, notes
---
- ML requires all data to be in numeric form. Data that is not numeric is converted to numeric form.
    
- The best library we have right now for numeric calculations in Python is numpy.
    

## Create an array[¶](#Create-an-array)

In [ ]:

```
import numpy as np
```

arr = np.array([1, 2, 3, 4, 5], dtype=np.float32) print(arr)

```
[1. 2. 3. 4. 5.]
```

- dtype ensures that all the elements of the array are of the same, given type.
    
- In case your data contains a mixed type, then numpy would "upcast" the datatypes, but will keep them in the same type.
    
- Let's say you have all integers but one string element, the to ensure all elements are of the same type, numpy would "upcast" the Integers into String.
    
- A numpy array is same as a Python list but with more features. We can easily convert a python list into a numpy array.
    

## Copy an array[¶](#Copy-an-array)

In [ ]:

```
x = np.array([1, 2, 3])
y = x
z = np.copy(x)
# here x and y both refer to the same array, but z is a copy.
# if we change x, y will change, but z will not.
x[0] = 10
print("x = ", x)
print("y = ", y)
print("z =", z)
```

```
x =  [10  2  3]
y =  [10  2  3]
z = [1 2 3]
```

- In Python, if we copy a list, it creates a reference to the original list.
    
- If we modify the referenced list, the original list is modified.
    
- Numpy works in a similar way, but if you have to create a copy, it has a copy() function that can copy a list so we have multiple copies to work with
    
- In the above example, y and x refer to the same numpy array but z has its own copy.
    

## Typecast Array[¶](#Typecast-Array)

- Typecasting is done using the astype() function.
    

In [ ]:

```
# code to demo type casting in numpy arrays
a = np.array([1, 2, 3])
print(a.dtype)
b = a.astype(np.float32)
print(b.dtype)
print(b)
```

#upcasting demo. a = np.array([1, 2, 3], dtype=np.int8) b = np.array([1, 2, 3], dtype=np.int16) c = a + b print(c.dtype)

#upcasting to a string a = np.array([1, 2, 3, "hello"]) print("datatype of a is" ,a.dtype) print("a is upcasted to a String : ", a)

```
int64
float32
[1. 2. 3.]
int16
datatype of a is <U21
a is upcasted to a String :  ['1' '2' '3' 'hello']
```

## NaN type in numpy[¶](#NaN-type-in-numpy)

- In ML problems, you will not always have full data. In case of incomplete data, you will need a way to fill empty values into the array. NaN is the value that you can place in an array wherever you have missing data.
    
- NaN stands for Not A Number. It is a placeholder to indicate the absence of value.
    

In [ ]:

```
#NaN demo in numpy
a = np.array([1, 2, 3, np.nan])
print(a.dtype)
print(a)
```

```
float64
[ 1.  2.  3. nan]
```

## Infinite arrays[¶](#Infinite-arrays)

- In NumPy, we have np.inf and -np.inf. np.inf is for positive infinity, and -np.inf is for negative infinity.
    
- I am not sure, where these will be used, but we will see.
    

In [ ]:

```
# infinite array demo
a = np.array([1, 2, 3, np.inf])
print(a.dtype)
print(a)
print(np.isinf(a))
```

```
float64
[ 1.  2.  3. inf]
[False False False  True]
```

## Creating a array with range of numbers[¶](#Creating-a-array-with-range-of-numbers)

In [ ]:

```
# arange demo
a = np.arange(10)
print(a)
b = np.arange(start=0, stop=10, step=2)
print(b)
```

# note that the stop value is not included in the array c = np.arange(start=0, stop=10, step=0.5) print(c)

# let's say you know the number of elements you want in the array, you can use linspace function to create an array. # the linspace function will create an array with the specified number of elements and the elements will be equally spaced. a = np.linspace(start=0, stop=10, num=5) print(a)

```
[0 1 2 3 4 5 6 7 8 9]
[0 2 4 6 8]
[0.  0.5 1.  1.5 2.  2.5 3.  3.5 4.  4.5 5.  5.5 6.  6.5 7.  7.5 8.  8.5
 9.  9.5]
[ 0.   2.5  5.   7.5 10. ]
```

## Shaping an array[¶](#Shaping-an-array)

- numpy.reshape is a function that takes an array and converts it into rows and columns based on the inputs parameters of required rows and columns.
    
- Of course, number of elements and expected rows and columns have to match.
    
- If you have 16 elements, you can do a 2X8 or a 4X4 but not 8X2.
    

In [ ]:

```
# reshape demo
a = np.arange(10)
print(a)
b = a.reshape(2, 5)
print(b)
c = a.reshape(5, 2)
print(c)
```

```
[0 1 2 3 4 5 6 7 8 9]
[[0 1 2 3 4]
 [5 6 7 8 9]]
[[0 1]
 [2 3]
 [4 5]
 [6 7]
 [8 9]]
```

- if you don't know the number of rows or columns, you can use -1 in the reshape function.
    

In [ ]:

```
# reshape demo with -1
a = np.arange(10)
print(a)
b = a.reshape(2, -1)
print(b)
c = a.reshape(-1, 2)
print(c)
```

```
[0 1 2 3 4 5 6 7 8 9]
[[0 1 2 3 4]
 [5 6 7 8 9]]
[[0 1]
 [2 3]
 [4 5]
 [6 7]
 [8 9]]
```

- numpy.flatten takes any array and flattens it into 1 dimension.
    

In [ ]:

```
# flatten demo
a = np.arange(10)
print(a)
b = a.reshape(2, 5)
print(b)
c = b.flatten()
print(c)
```

```
[0 1 2 3 4 5 6 7 8 9]
[[0 1 2 3 4]
 [5 6 7 8 9]]
[0 1 2 3 4 5 6 7 8 9]
```

- numpy.transpose function tranposes an array, basically converting rows to columns and vice-versa.
    

In [ ]:

```
# transpose demo
a = np.arange(10)
print(a)
b = a.reshape(2, 5)
print(b)
c = b.T
print(c)
```

```
[0 1 2 3 4 5 6 7 8 9]
[[0 1 2 3 4]
 [5 6 7 8 9]]
[[0 5]
 [1 6]
 [2 7]
 [3 8]
 [4 9]]
```

- transpose also takes in axes parameter which is a tuple that switches the dimensions.
    
- The number elements in the tuple should of course match the number of dimensions, otherwise the function would not know where to put the missing dimensions.
    

In [ ]:

```
# transpose demo with axes argument
a = np.arange(10)
print(a)
b = a.reshape(2, 5)
print(b)
c = np.transpose(b, axes=(1, 0))
print(c)
```

```
[0 1 2 3 4 5 6 7 8 9]
[[0 1 2 3 4]
 [5 6 7 8 9]]
[[0 5]
 [1 6]
 [2 7]
 [3 8]
 [4 9]]
```

In [ ]:

```
# transpose numpy multidimensional array
a = np.arange(24)
print(a)
# create 2 of 3x4 arrays
b = a.reshape(2, 3, 4)
print("\nafter reshape\n",b)
# transpose the 2 arrays
# the axes argument is used to specify the order of the axes
# here we are specifying that the first axis should be the second axis, the second axis should be the first axis and the third axis should be the third axis
c = np.transpose(b, axes=(1, 0, 2))
print("\nafter transposing \n",c)
```

```
[ 0  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23]
```

after reshape [[[ 0 1 2 3] [ 4 5 6 7] [ 8 9 10 11]]

[[12 13 14 15] [16 17 18 19] [20 21 22 23]]]

after transposing [[[ 0 1 2 3] [12 13 14 15]]

[[ 4 5 6 7] [16 17 18 19]]

[[ 8 9 10 11] [20 21 22 23]]]

- numpy has a convenient zeros, ones and ones_like and zeros_like function which create an array with zeros, ones of a defined shape or create the arrays with shapes like a reference array, respectively.
    

In [ ]:

```
# ones_like demo
a = np.arange(10)
print(a)
# here we are creating an array of ones with the same shape as a
b = np.ones_like(a)
print(b)
```

```
[0 1 2 3 4 5 6 7 8 9]
[1 1 1 1 1 1 1 1 1 1]
```

## Linear algebra with numpy[¶](#Linear-algebra-with-numpy)

In [ ]:

```
# numpy linear algebra demo
# numpy has a linear algebra module that can be used to perform linear algebra operations on numpy arrays.
# let's create two arrays
a = np.array([[1, 2], [3, 4]])
print(a)
b = np.array([[5, 6], [7, 8]])
print(b)
```

# simple addition c = a + b print("Simple addition") print(c)

# multiplication c = a * b print("Simple multiplication") print(c)

# matrix multiplication c = a.dot(b) print("Matrix multiplication") print(c)

# matrix inverse c = np.linalg.inv(a) print("Matrix inverse") print(c)

# matrix determinant c = np.linalg.det(a) print("Matrix determinant") print(c)

# matrix trace c = np.trace(a) print("Matrix trace") print(c)

```
[[1 2]
 [3 4]]
[[5 6]
 [7 8]]
Simple addition
[[ 6  8]
 [10 12]]
Simple multiplication
[[ 5 12]
 [21 32]]
Matrix multiplication
[[19 22]
 [43 50]]
Matrix inverse
[[-2.   1. ]
 [ 1.5 -0.5]]
Matrix determinant
-2.0000000000000004
Matrix trace
5
```

## non-linear math with numpy[¶](#non-linear-math-with-numpy)

In [ ]:

```
# non linear math functions demo
a = np.arange(1,10)
print(a)
```

# sin function print("sin function") b = np.sin(a) print(b)

# cos function c = np.cos(a) print("cos function") print(c)

# tan function d = np.tan(a) print("tan function") print(d)

# log function e = np.log(a) print("log function") print(e)

# exponential function f = np.exp(a) print("exponential function") print(f)

```
[1 2 3 4 5 6 7 8 9]
sin function
[ 0.84147098  0.90929743  0.14112001 -0.7568025  -0.95892427 -0.2794155
  0.6569866   0.98935825  0.41211849]
cos function
[ 0.54030231 -0.41614684 -0.9899925  -0.65364362  0.28366219  0.96017029
  0.75390225 -0.14550003 -0.91113026]
tan function
[ 1.55740772 -2.18503986 -0.14254654  1.15782128 -3.38051501 -0.29100619
  0.87144798 -6.79971146 -0.45231566]
log function
[0.         0.69314718 1.09861229 1.38629436 1.60943791 1.79175947
 1.94591015 2.07944154 2.19722458]
exponential function
[2.71828183e+00 7.38905610e+00 2.00855369e+01 5.45981500e+01
 1.48413159e+02 4.03428793e+02 1.09663316e+03 2.98095799e+03
 8.10308393e+03]
```

## Creating matrices with random numbers[¶](#Creating-matrices-with-random-numbers)

- numpy allows us to create arrays with random numbers.
    
- We can control the distribution from which the random numbers are picked.
    

In [ ]:

```
# numpy random demo
# numpy has a random module that can be used to generate random numbers.
# let's generate 10 random numbers between 0 and 1
a = np.random.rand(10)
print(a)
```

```
[0.90234858 0.09928035 0.96980907 0.65314004 0.17090959 0.35815217
 0.75068614 0.60783067 0.32504723 0.03842543]
```

In [ ]:

```
# random numbers with seed
# if you want to generate the same random numbers every time, you can use the seed function.
# the seed function will set the seed for the random number generator.
# if you run the code below multiple times, you will get the same random numbers.
np.random.seed(0)
a = np.random.rand(10)
print(a)
```

np.random.seed(0) b = np.random.rand(10) print(b)

```
[0.5488135  0.71518937 0.60276338 0.54488318 0.4236548  0.64589411
 0.43758721 0.891773   0.96366276 0.38344152]
[0.5488135  0.71518937 0.60276338 0.54488318 0.4236548  0.64589411
 0.43758721 0.891773   0.96366276 0.38344152]
```

In [ ]:

```
# random numbers from a uniform distribution
# the uniform function will generate random numbers from a uniform distribution.
# the uniform function takes 3 arguments, the first argument is the lower bound, the second argument is the upper bound and the third argument is the number of random numbers to generate.
a = np.random.uniform(low=0, high=1, size=10)
print(a)
```

# random numbers from normal distribution # the normal function will generate random numbers from a normal distribution. # the normal function takes 3 arguments, the first argument is the mean, the second argument is the standard deviation and the third argument is the number of random numbers to generate. a = np.random.normal(loc=0, scale=1, size=10) print(a)

# random numbers from a choice # the choice function will generate random numbers from a choice. # the choice function takes 3 arguments, the first argument is the array from which the random numbers should be generated, the second argument is the number of random numbers to generate and the third argument is whether the random numbers should be generated with replacement or not. a = np.random.choice(a=[1, 2, 3, 4, 5], size=10, replace=True) print(a)

```
[0.79172504 0.52889492 0.56804456 0.92559664 0.07103606 0.0871293
 0.0202184  0.83261985 0.77815675 0.87001215]
[ 1.49407907 -0.20515826  0.3130677  -0.85409574 -2.55298982  0.6536186
  0.8644362  -0.74216502  2.26975462 -1.45436567]
[1 5 1 5 2 5 2 3 3 1]
```

## Access elements from an array[¶](#Access-elements-from-an-array)

- Accessing array elements works similar to how we access elements in lists
    

In [ ]:

```
# access elements in a numpy array
# let's create a numpy array
a = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9])
print(a)
```

# access the first element print(a[0])

```
[1 2 3 4 5 6 7 8 9]
1
```

- Just like in Python lists, the numpy arrays can be sliced to create new ones.
    

In [ ]:

```
# array slicing
# let's create a numpy array
a = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9])
print(a)
```

# access the first 3 elements print(a[0:3])

# access the last 3 elements print(a[-3:])

# access the first 3 elements with a step of 2 print(a[0:3:2])

```
[1 2 3 4 5 6 7 8 9]
[1 2 3]
[7 8 9]
[1 3]
```

In [ ]:

```
# slicing multidimensional arrays
# let's create a numpy array
a = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
print(a)
```

# access the first row print(a[0])

# access the first column print(a[:, 0])

# access the first 2 rows and first 2 columns print(a[0:2, 0:2])

```
[[1 2 3]
 [4 5 6]
 [7 8 9]]
[1 2 3]
[1 4 7]
[[1 2]
 [4 5]]
```

## Filtering elements from numpy array based on where conditions[¶](#Filtering-elements-from-numpy-array-based-on-where-conditions)

In [ ]:

```
# filter elements in a numpy array
# let's create a numpy array
a = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9])
print(a)
```

# filter elements that are greater than 5 print(a[a > 5])

# filter elements that are less than or equal to 5 print(a[a <= 5])

```
[1 2 3 4 5 6 7 8 9]
[6 7 8 9]
[1 2 3 4 5]
```

## Numpy functions for statistics[¶](#Numpy-functions-for-statistics)

- mean, variance, median are some functions available in numpy to perform statistical analysis
    

In [ ]:

```
# statistics demo
# let's create a numpy array
a = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9])
print(a)
```

# mean print("mean", a.mean())

# median print("median", np.median(a))

# standard deviation print("standard deviation", a.std())

# variance print("variance", a.var())

```
[1 2 3 4 5 6 7 8 9]
mean 5.0
median 5.0
standard deviation 2.581988897471611
variance 6.666666666666667
```

## Aggregation, Concatenation, etc.[¶](#Aggregation,-Concatenation,-etc.)

In [ ]:

```
# aggregate functions demo
# let's create a numpy array
a = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
print(a)
```

# sum print("sum", a.sum())

# sum along the rows print("sum along the rows", a.sum(axis=1))

# sum along the columns print("sum along the columns", a.sum(axis=0))

# min print("min", a.min())

# min along the rows print("min along the rows", a.min(axis=1))

# min along the columns print("min along the columns", a.min(axis=0))

# max print("max", a.max())

# max along the rows print("max along the rows", a.max(axis=1))

# max along the columns print("max along the columns", a.max(axis=0))

# argmin print("argmin", a.argmin())

# argmin along the rows print("argmin along the rows", a.argmin(axis=1))

# argmin along the columns print("argmin along the columns", a.argmin(axis=0))

# argmax print("argmax", a.argmax())

# argmax along the rows print("argmax along the rows", a.argmax(axis=1))

# argmax along the columns print("argmax along the columns", a.argmax(axis=0))

# cumulative sum demo print("cumsum", a.cumsum())

# cumsum along the rows print("cumsum along the rows", a.cumsum(axis=1))

# cumsum along the columns print("cumsum along the columns", a.cumsum(axis=0))

```
[[1 2 3]
 [4 5 6]
 [7 8 9]]
sum 45
sum along the rows [ 6 15 24]
sum along the columns [12 15 18]
min 1
min along the rows [1 4 7]
min along the columns [1 2 3]
max 9
max along the rows [3 6 9]
max along the columns [7 8 9]
argmin 0
argmin along the rows [0 0 0]
argmin along the columns [0 0 0]
argmax 8
argmax along the rows [2 2 2]
argmax along the columns [2 2 2]
cumsum [ 1  3  6 10 15 21 28 36 45]
cumsum along the rows [[ 1  3  6]
 [ 4  9 15]
 [ 7 15 24]]
cumsum along the columns [[ 1  2  3]
 [ 5  7  9]
 [12 15 18]]
```

## Sort functions in numpy[¶](#Sort-functions-in-numpy)

In [ ]:

```
# sorting demo
# let's create a numpy array
a = np.array([1, 4, 2, 5, 3])
print(a)
```

# sort the array print(np.sort(a))

# sort the array in descending order print(np.sort(a)[::-1])

```
[1 4 2 5 3]
[1 2 3 4 5]
[5 4 3 2 1]
```