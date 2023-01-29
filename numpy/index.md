# Numpy Refresher


[Numpy](http://www.numpy.org) is a package used for scientific computing in python. Numpy's core is implemented in C/C++ providing fast implementations of matrices operations. Numpy also utilizes the processors SIMD and other instructions to make implementation faster

## What is Numpy

Numpy is a package used for scientific computing in python. Numpy's core is implemented in C/C++ providing fast implementations of matrices operations. Numpy also utilizes the processors SIMD and other instructions to make implementation faster. Main offering of Numpy is powerful N-dimensional array object and useful linear algebra, Fourier transform, and random number capabilities.
Numpy main object is homogeneous multidimensional arrays. Indexed by the positive tuple of integers. 
Its dimensions are called **axes**. No of axes is called **rank**. <br>
Axes length is the no of elements in that dimension. Normally, **axes 0** is **rows** and **axes 1** is **column**

## Imporrant NumPy Arrays Attributes
1. **ndim** No of dimensions
2. **shape** Size of each dimension
3. **size** Total array size in bytes
4. **itemsize** Size of an element in bytes
5. **nbytes** Total array size in bytes

I will cover them in detail but first lets understand few ways to create numpy arrays.


```python
>>> import numpy as np
```

## How to create an simple numpy array


```python
>>> arr = np.array([1,2,3,4,5])
>>> arr
```

<div class="output">


    array([1, 2, 3, 4, 5])
</div>


All items in numpy array should have same data type. If not then numpy will upcast the needed ones


```python
>>> arr = np.array([1.1, 2,3,4,5])
>>> arr
```

<div class="output">


    array([ 1.1,  2. ,  3. ,  4. ,  5. ])
</div>


Otherwise one can explicitly assign the datatype using **"dtype"**


```python
>>> arr = np.array([1.1, 2,3,4,5], dtype=int)
```

## Creating a multidimensional array


```python
>>> np.array([range(i, i + 3) for i in [2, 4, 6]])
```


<div class="output">

    array([[2, 3, 4],
           [4, 5, 6],
           [6, 7, 8]])

</div>


```python
>>> a = np.array([range(1,100)])
>>> print(a.shape)
>>> print(a.ndim)
>>> a
```
<div class="output">
    (1, 99)
    <br>
    2
    <br>




    array([[ 1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15, 16, 17,
            18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34,
            35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51,
            52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68,
            69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85,
            86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 97, 98, 99]])

</div>

## Arrays from Scratch


```python
# np.zeros(shape, dtype=float, order='C')
>>> np.zeros((2,3))
#shape is a tuple and passed with brackets
```


<div class="output">

    array([[ 0.,  0.,  0.],
           [ 0.,  0.,  0.]])

</div>


```python
# np.ones(shape, dtype=None, order='C')
>>> np.ones((2,3), dtype=int)
```


<div class="output">

    array([[1, 1, 1],
           [1, 1, 1]])
</div>


How about a matrix of all the same value


```python
# np.full(shape, fill_value, dtype=None, order='C')
>>> np.full((3,2), 3.1)
```


<div class="output">

    array([[ 3.1,  3.1],
           [ 3.1,  3.1],
           [ 3.1,  3.1]])
</div>

### How about a little more flexibility in creating the numpy array
#### 1. Creating the linear sequence of array with flexibility of providing step size


```python
# np.arange([start,] stop[, step,], dtype=None)
>>> a = np.arange(1, 10, 1)
>>> print(a)

>>> a = np.arange(1, 10, .5, dtype=float)
>>> print(a)
```
<div class="output">
    [1 2 3 4 5 6 7 8 9]
    [ 1.   1.5  2.   2.5  3.   3.5  4.   4.5  5.   5.5  6.   6.5  7.   7.5  8.
      8.5  9.   9.5]
</div>


```python
>>> a = np.arange(1, 10, .5, dtype=float)
>>> for i in a:
...    print(int(i), end=' ')
```
<div class="output">
    1 1 2 2 3 3 4 4 5 5 6 6 7 7 8 8 9 9 
</div>

```python
>>> a = np.arange(1, 10, .5, dtype=int)
>>> print(a)
>>> a = np.arange(1, 10, .5).astype(int) # Floating point step size
>>> print(a)
```

<div class="output">
    [ 1.   1.5  2.   2.5  3.   3.5  4.   4.5  5.   5.5  6.   6.5  7.   7.5  8.
      8.5  9.   9.5]
    [1 1 2 2 3 3 4 4 5 5 6 6 7 7 8 8 9 9]
</div>

#### 2.  Creating the linear sequence of array with fliexibility of providing the number values required 


```python
# np.linspace(start, stop, num=50, endpoint=True, retstep=False, dtype=None)
>>> sample = np.linspace(1, 10)
>>> print("Samples ---->", sample, end=' \n')
>>> sample,step = np.linspace(1, 10, num=20, retstep=True)
>>> print("Step ---->", step)
```

```
    Samples
    [  1.           1.18367347   1.36734694   1.55102041   1.73469388
       1.91836735   2.10204082   2.28571429   2.46938776   2.65306122
       2.83673469   3.02040816   3.20408163   3.3877551    3.57142857
       3.75510204   3.93877551   4.12244898   4.30612245   4.48979592
       4.67346939   4.85714286   5.04081633   5.2244898    5.40816327
       5.59183673   5.7755102    5.95918367   6.14285714   6.32653061
       6.51020408   6.69387755   6.87755102   7.06122449   7.24489796
       7.42857143   7.6122449    7.79591837   7.97959184   8.16326531
       8.34693878   8.53061224   8.71428571   8.89795918   9.08163265
       9.26530612   9.44897959   9.63265306   9.81632653  10.        ] 
    
    Step
    0.473684210526
```

### Array with distributed random values
####  Array of uniformly distributed random values between 0 and 1


```python
# np.random.random_sample(size=None)
>>> np.random.random((3, 2))
```


<div class="output">

    array([[ 0.86739782,  0.56355004],
           [ 0.70993532,  0.06739621],
           [ 0.53815033,  0.59688062]])

</div>


```python
# np.random.normal(loc=0.0, scale=1.0, size=None)
>>> np.random.normal(0, 1, (3,3))
```

<div class="output">


    array([[ 0.97078719,  0.32316481,  0.64860467],
           [-0.41963849,  0.1416606 , -2.00128317],
           [-1.20452905, -0.86871742,  1.10516725]])
</div>



```python
#randint(low, high=None, size=None, dtype='l')
>>> np.random.randint(10, 100,size=3)
```


<div class="output">

    array([14, 48, 77])
</div>


#### Identity Matrix


```python
# np.eye(N, M=None, k=0, dtype=<class 'float'>)
>>> np.eye(4)
```


<div class="output">
    array([[ 1.,  0.,  0.,  0.],
           [ 0.,  1.,  0.,  0.],
           [ 0.,  0.,  1.,  0.],
           [ 0.,  0.,  0.,  1.]])

</div>

## NumPy Standard Data Types

- **bool_** Boolean (True or False) stored as a byte <br>
- **int_** Default integer type (same as C long; normally either int64 or int32) <br>
- **intc** Identical to C int (normally int32 or int64) <br>
- **intp** Integer used for indexing (same as C ssize_t; normally either int32 or int64) <br>
- **int8** Byte (–128 to 127) <br>
- **int16** Integer (–32768 to 32767) <br>
- **int32** Integer (–2147483648 to 2147483647) <br>
- **int64** Integer (–9223372036854775808 to 9223372036854775807) <br>
- **uint8** Unsigned integer (0 to 255) <br>
- **uint16** Unsigned integer (0 to 65535) <br>
- **uint32** Unsigned integer (0 to 4294967295) <br>
- **uint64** Unsigned integer (0 to 18446744073709551615) <br>
- **float_**  Shorthand for float64 <br>
- **float16** Half-precision float: sign bit, 5 bits exponent, 10 bits mantissa <br>
- **float32** Single-precision float: sign bit, 8 bits exponent, 23 bits mantissa <br>
- **float64** Double-precision float: sign bit, 11 bits exponent, 52 bits mantissa <br>


## NumPy Random Generator - Seed the RandomState
numpy random generator can be seeded with a *seed* value to make sure that same random arrays are generated each time the code runs.

Seeding the random generator allows the generator to generate the same random values everytime. It names values in the array predictible
**np.random.seed(0)**
> np.random.seed(0); np.random.randint(10, size=6) <br>
> np.random.seed(0); np.random.randint(10, size=6)

Above code will generate same array everytime


```python
>>> np.random.seed(1)
>>> x1 =np.random.randint(10, size=6)
>>> x2 = np.random.randint(10, size=(3, 4))
>>> x3 = np.random.randint(10, size=(3,4,5))

print(x1)
print(x2)
print(x3)
```

<div class="output">
    [5 8 9 5 0 0]
    [[1 7 6 9]
     [2 4 5 2]
     [4 2 4 7]]
    [[[7 9 1 7 0]
      [6 9 9 7 6]
      [9 1 0 1 8]
      [8 3 9 8 7]]
    
     [[3 6 5 1 9]
      [3 4 8 1 4]
      [0 3 9 2 0]
      [4 9 2 7 7]]
    
     [[9 8 6 9 3]
      [7 7 4 5 9]
      [3 6 8 0 2]
      [7 7 9 7 3]]]

</div>

```python
>>> np.random.seed(0); np.random.randint(10, size=6)
>>> np.random.seed(0); np.random.randint(10, size=6)
```


<div class="output">

    array([5, 0, 3, 3, 7, 9])


</div>

