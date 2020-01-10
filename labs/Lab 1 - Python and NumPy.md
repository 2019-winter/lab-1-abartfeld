---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.1'
      jupytext_version: 1.2.4
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

# Name(s)
Andrew Bartfeld


**Instructions:** This is an individual assignment, but you may discuss your code with your neighbors.


# Python and NumPy

While other IDEs exist for Python development and for data science related activities, one of the most popular environments is Jupyter Notebooks.

This lab is not intended to teach you everything you will use in this course. Instead, it is designed to give you exposure to some critical components from NumPy that we will rely upon routinely.

## Exercise 0
Please read and reference the following as your progress through this course. 

* [What is the Jupyter Notebook?](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/What%20is%20the%20Jupyter%20Notebook.ipynb#)
* [Notebook Tutorial](https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook)
* [Notebook Basics](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/Notebook%20Basics.ipynb)

**In the space provided below, what are three things that still remain unclear or need further explanation?**


1.

2.

3.


## Exercises 1-7
For the following exercises please read the Python appendix in the Marsland textbook and answer problems A.1-A.7 in the space provided below.

```python
import numpy as np
import pandas as pd
```

## Exercise 1

```python
a = np.full((6, 4), 2)
a
```

## Exercise 2

```python
b = np.ones((6, 4))
np.fill_diagonal(b, 3)
b
```

## Exercise 3

`a*b` is element multiplication, which requires the two matrices to be identical in dimension, which a and b fulfill.

`dot(a, b)` is matrix multiplication, which requires the number of columns of one to be equal to the number of rows of the other, which a and b do not fulfill.

```python
c = a * b
print(c)

```

## Exercise 4

Transposing an array basically rotates it about the leading diagonal, swapping the number of rows with the number of columns.

The two results are different dimensions because dotting a mxn array with a nxp array produces a nxn array. The first result is 6x4 dotted with 4x6, producing a 4x4 matrix. The second is 4x6 dotted with 6x4, producing a 6x6 matrix.

```python
print(np.dot(a.transpose(), b))
print(np.dot(a, b.transpose()))

```

## Exercise 5

```python
def foo():
    print('bar')

foo()

```

## Exercise 6

```python
def rand_array(n):
    for i in range(n):
        a = np.random.randint(0, 10, (int(np.random.random()*10) + 1, int(np.random.random()*10) + 1))
        print(a)
        print('Mean: {}'.format(np.mean(a)))
        print('Sum: {}'.format(np.sum(a)))
                       
rand_array(2) # Change argument to change number of arrays created
    

```

## Exercise 7

```python
def count_ones(arr):
    i = 0
    for row in arr:
        for num in row:
            if num == 1:
                i = i + 1
    return i

print(b)
count = count_ones(b)
print(count)

c = np.where(b == 1)
print(len(c[0]))

```

## Excercises 8-???
While the Marsland book avoids using another popular package called Pandas, we will use it at times throughout this course. Please read and study [10 minutes to Pandas](https://pandas.pydata.org/pandas-docs/stable/getting_started/10min.html) before proceeding to any of the exercises below.


## Exercise 8
Repeat exercise A.1 from Marsland, but create a Pandas DataFrame instead of a NumPy array.

```python
import pandas as pd

a = np.full((6, 4), 2)
a = pd.DataFrame(a)
print(a)
```

## Exercise 9
Repeat exercise A.2 using a DataFrame instead.

```python
b = np.ones((6, 4), dtype=int)
np.fill_diagonal(b, 3)
b = pd.DataFrame(b)
print(b)
```

## Exercise 10
Repeat exercise A.3 using DataFrames instead.

`a.dot(b)` doesn't work for the reasons outlined in Exercise 3 above.

```python
res1 = a * b
print(res1)
a.dot(b)
```

## Exercise 11
Repeat exercise A.7 using a dataframe.

```python
# YOUR SOLUTION HERE
```

## Exercises 12-14
Now let's look at a real dataset, and talk about ``.loc``. For this exercise, we will use the popular Titanic dataset from Kaggle. Here is some sample code to read it into a dataframe.

```python
titanic_df = pd.read_csv(
    "https://raw.githubusercontent.com/dlsun/data-science-book/master/data/titanic.csv"
)
titanic_df
```

Notice how we have nice headers and mixed datatypes? That is one of the reasons we might use Pandas. Please refresh your memory by looking at the 10 minutes to Pandas again, but then answer the following.


## Exercise 12
How do you select the ``name`` column without using .iloc?

```python
titanic_df['name']
```

## Exercise 13
After setting the index to ``sex``, how do you select all passengers that are ``female``? And how many female passengers are there?

```python
titanic_df.set_index('sex',inplace=True)

titanic_df.loc['female']
len(titanic_df.loc['female'])
```

## Exercise 14
How do you reset the index?

```python
titanic_df.reset_index()
```
