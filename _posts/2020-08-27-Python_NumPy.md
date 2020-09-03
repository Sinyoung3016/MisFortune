---
layout: post
title: "[PYTHON] NumPy"
date: 2020-08-27 00:00:00
categories: [STUDY]
tags: [PYTHON]
last_modified_at: 2020-08-27
---

<p>
From w3schools
<br>With Python</p>

---

__NumPy__
<p> Numerical Python
<br>: python library used for working with array
<br> + linear algebra, fourier transform and matrices
</p>
<p>* 배열은 속도와 자원이 중요한 데이터과학에서 쓰임.
<br>* numPy Array = ndarray, N-dimensional array
<br>* 같은 데이터타입의 데이터만 배열에 넣을 수 있음.
<br>* 일반적인 파이썬 배열 객체보다 더 빠르게 기능함.
</p>

<br>

__Create NumPy Array__

```{.python}
import numpy as np

arr = np.array([1,2,3])
print(arr)
print(type(arr))
```

<figure>
  <center><img src="/Fortune/assets/Python/Numpy/01.png" alt="Midnight" style="width:100%"></center>
</figure>

```{.python}
import numpy as np

print("2D")
arr = np.array([[1,2,3], [4,5,6]])
print(arr)

print("3D")
arr = np.array([[[1,2,3], [4,5,6]], [[1,2,3], [4,5,6]]])
print(arr)

```

<figure>
  <center><img src="/Fortune/assets/Python/Numpy/02.png" alt="Midnight" style="width:100%"></center>
</figure>

```{.python}
#배열의 차원의 수를 알려주는 정수를 반환 : ndim, n dimension
#배열 생성시 인수로 사용되어 차원의 수를 정의 : ndmin ,n minimum dimension
# Matrix operation : numpy.mat

import numpy as np

a = np.array(1)
b = np.array([1,2], ndmin = 3)
c = np.array([[1,2],[3,4]])

print(a.ndim)
print(b.ndim)
print(c.ndim)

```

<figure>
  <center><img src="/Fortune/assets/Python/Numpy/03.png" alt="Midnight" style="width:100%"></center>
</figure>

<br>

__NumPy Array Slicing__

```{.python}
#[start:end] or [start:end:step]
#result include the start index ~ the (end-1) index
#return ndarray

import numpy as np

arr = np.array([1, 2, 3, 4, 5, 6, 7])
print(arr[-3:-1])
print(arr[::2])

arr = np.array([[1, 2, 3, 4, 5], [6, 7, 8, 9, 10]])
print(arr[1, 1:4])

arr = np.array([[1, 2, 3, 4, 5], [6, 7, 8, 9, 10], [1, 2, 3, 4, 5]])
print(arr[0:3, 1:4])

```

<figure>
  <center><img src="/Fortune/assets/Python/Numpy/04.png" alt="Midnight" style="width:100%"></center>
</figure>

<br>

__NumPy Data Types__

|integer|unsigned integer|boolean|float|complex float|object|string|unicode string|void|timedelta|datetime|
|i|u|b|f|c|O|S|U|V|m|M|

```{.python}
#배열 객체의 데이터 유형을 반환 : dtype
#배열 객체의 복사본 만들고 데이터타입을 매개변수로 지정가능 : astype()

import numpy as np

arr = np.array([1, 2, 3, 4])
print(arr.dtype, "\n")

arr = np.array([1.1, 0, 3.3, 4.4], dtype='f')
print(arr.dtype, "\n")

newarr = arr.astype(bool)
print(newarr)
print(newarr.dtype, "\n")
```

<figure>
  <center><img src="/Fortune/assets/Python/Numpy/05.png" alt="Midnight" style="width:100%"></center>
</figure>

<br>

__NumPy Copy and View__

```{.python}
import numpy as np

arr = np.array([1,2,3,4,5])
x = arr.copy() #새로운 배열
y = arr.view() # == arr
arr[0] = 100 # y[0] = 100와 같은 결과

print(arr)
print(x)
print(y, "\n")

#array.base 속성을 통해 해당 배열이 데이터를 가지고 있으면, None 반환
print(arr.base)
print(x.base)
print(y.base)

```

<figure>
  <center><img src="/Fortune/assets/Python/Numpy/06.png" alt="Midnight" style="width:100%"></center>
</figure>

<br>

__NumPy Array Shape__

```{.python}
#배열의 shape를 튜플로 반환, shape

import numpy as np

arr = np.array([[1, 2, 3, 4], [5, 6, 7, 8]])
print(arr)
print('shape of array :', arr.shape)

arr = np.array([1, 2, 3, 4], ndmin=5)
print(arr)
print('shape of array :', arr.shape)

```

<figure>
  <center><img src="/Fortune/assets/Python/Numpy/07.png" alt="Midnight" style="width:100%"></center>
</figure>

<br>

__NumPy Array Reshape__

```{.python}
#배열의 모양을 변경, reshape(shape)
#이때, 요소의 수가 맞아야함.
#reshape(-1)은 배열을 1차원함.

import numpy as np

arr = np.array([1,2,3,4,5,6,7,8,9,10,11,12])
newarr = arr.reshape(2, 2, -1)#-1을 넣으면 알아서 계산해서 배열을 reshape함.
print(newarr, "\n")
print(newarr.base)

```
<figure>
  <center><img src="/Fortune/assets/Python/Numpy/08.png" alt="Midnight" style="width:100%"></center>
</figure>

<br>

__NumPy Array Iterating__

```{.python}
#nditer(), n demension iterator

import numpy as np
#nD에서 위와 같은 방식으로 진행하면, n중 for문을 써야함.
arr = np.array([[1, 2], [3, 4]])
for x  in np.nditer(arr):
  print(x)

print("----")

#iterator를 사용하면서, 요소의 데이터타입을 바꿀 수 있음, 이때 버퍼를 이용 : op_dtypes
for x in np.nditer(arr, flags=['buffered'], op_dtypes=['S']):
  print(x)

print("----")

for x in np.nditer(arr[:, ::2]):
  print(x)

print("----")

#열거형(순서를 하나씩 언급) : ndenumerate()
for idx, x in np.ndenumerate(arr):
  print(idx, x)

```
<figure>
  <center><img src="/Fortune/assets/Python/Numpy/09.png" alt="Midnight" style="width:100%"></center>
</figure>

<br>

__NumPy Joining Array__

```{.python}
#연결하려는 배열과 축(default = 0)을 중심
arr1 = np.array([[1, 2], [3, 4]])
arr2 = np.array([[5, 6], [7, 8]])

# concatenate((arr,arr), axis) : 배열 하나로 연결
print("<concatenate>")
arr = np.concatenate((arr1, arr2), axis=1)
print(arr)

print("----")

# stack((arr,arr), axis) :'배열 요소 두개를 합침' = 요소,인 배열을 만듬.
print("<stack>")
arr = np.stack((arr1, arr2), axis=1)
print(arr)

print("----")

#hstack((arr,arr)) : rows : 가장 작은 요소
print("<hstack>")
arr = np.hstack((arr1, arr2))
print(arr)

print("----")

#vstack((arr,arr)) : columns : 가장 작은 요소
print("<vstack>")
arr = np.vstack((arr1, arr2))
print(arr)

print("----")

#dstack((arr,arr)) : depth : 가장 작은 요소 && 똑같은 깊이의 요소와 연결
print("<dstack>")
arr = np.dstack((arr1, arr2))
print(arr)

```
<figure>
  <center><img src="/Fortune/assets/Python/Numpy/10.png" alt="Midnight" style="width:100%"></center>
</figure>

<br>

__NumPy Splitting Array__

```{.python}
# array_split() : return 배열의 배열
import numpy as np

arr = np.array([[[1, 2], [3, 4], [5, 6]], [[7, 8], [9, 10], [11, 12]]])
newarr = np.array_split(arr, 3, axis=2)
for i in range(len(newarr)):
	print(newarr[i],"\n")

#hsplit의 반대 = hstack
#vsplit의 반대 = vstack
#dsplit의 반대 = dstack
```

<figure>
  <center><img src="/Fortune/assets/Python/Numpy/11.png" alt="Midnight" style="width:100%"></center>
</figure>

<br>

__NumPy Searching Array__

```{.python}
#where() return tuple(index)

arr = np.array([[1, 2, 3], [4, 5, 4]])
x = np.where(arr == 4)
print(x)
print("----")

#searchsorted() : binarysearch를 진행, 따라서 정렬되어 있어야함.
#왼쪽부터 검색해 타겟보다 더 크지 않는 첫번째(왼쪽) 인덱스를 반환, 그래서 9보다 큰 수를 입력해도 4가 나옴.
arr = np.array([6, 7, 8, 9])
x = np.searchsorted(arr, 7)
print(x)
print("----")

#오른쪽부터 검색해 타겟보다 더 작지 않은 첫번째(오른쪽) 인덱스를 반환,
x = np.searchsorted(arr, 7, side ='right')
print(x)
print("----")

x = np.searchsorted(arr, 7)
print(x)
print("----")

x = np.searchsorted(arr, [2, 4, 6])
print(x) #return array

```

<figure>
  <center><img src="/Fortune/assets/Python/Numpy/12.png" alt="Midnight" style="width:100%"></center>
</figure>

<br>

__NumPy Sorting Array__

```{.python}
#sort() return copy of array

arr = np.array([True, False, True])
print(np.sort(arr))

arr = np.array([[3, 2, 4], [5, 0, 1]])
print(np.sort(arr))

```

<figure>
  <center><img src="/Fortune/assets/Python/Numpy/13.png" alt="Midnight" style="width:100%"></center>
</figure>

<br>

__NumPy Filter Array__

```{.python}
#filtering : 기존 배열에서 일부 요소를 가져와서 새 배열을 만드는 것
#NumPy에서는 부울 인덱스 목록을 사용.

arr = np.array([1,2,3,4,5,6,7])

#case01
filter_arr = []
for element in arr:
  if element % 2 == 0:
    filter_arr.append(True)
  else:
    filter_arr.append(False)

newarr = arr[filter_arr]

print(filter_arr)
print(newarr)

print("----")

#case02
filter_arr = ( arr % 2 == 0 )
newarr = arr[filter_arr]

print(filter_arr)
print(newarr)

```

<figure>
  <center><img src="/Fortune/assets/Python/Numpy/14.png" alt="Midnight" style="width:100%"></center>
</figure>

<br>

__Random Numbers in NumPy__

```{.python}
from numpy import random as r

x = r.randint(100) #0~100(int)
x = r.rand() #0~1(float)

x = r.randint(100, size=(5,3)) #shape=[5,3]인 배열
x = r.rand(5,3)

x = r.choice([3,4,5,7]) #배열 안에서 임의로 반환
x = r.choice([3,4,5,7], size=(5,3))

```

<p>Random을 통해 분포 연산 가능.
<br>Seaborn(Matplotlib를 사용)을 통해 시각화 가능.</p>

|Random Permutation|random.shuffle(), random.permutation()|
|Normal Distribution|random.normal()|
|Binomial Distribution|random.binomial()|
|Poisson Distribution|random.poisson()|
|Uniform Distribution|random.uniform()|
|Logistic Distribution|random.logistic()|
|Multinomial Distribution|random.multinomial()|
|Exponential Distribution|random.exponential()|

<br>

__NumPy ufuncs__

<p> : Universal Functions, ndarray객체에서 작동하는 Numpy함수로 벡터화를 통해 속도를 줄임.
<br>* 사칙연산, 반올림내림, 로그, 최소공배수, 최대공약수, 삼각합수, 쌍곡선, 집합 등의 연산이 가능.
</p>

```{.python}
#ufunc 만들기 : frompyfunc(함수이름, 인수(배열)의 수, 출력배열의 수)
def myadd(x, y):
  return x+y

myadd = np.frompyfunc(myadd, 2, 1)
print(myadd([1,2], [3,5]))

#함수가 ufunc인지 확인
print(type(myadd))
```

<figure>
  <center><img src="/Fortune/assets/Python/Numpy/15.png" alt="Midnight" style="width:100%"></center>
</figure>


<br>
<br>


