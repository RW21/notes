# Python-notes
<!-- markdown-toc start - Don't edit this section. Run M-x markdown-toc-refresh-toc -->
**Table of Contents**

- [Python-notes](#python-notes)
    - [Naming](#naming)
        - [General](#general)
    - [Basic data types](#basic-data-types)
        - [Dictionary](#dictionary)
        - [Sets](#sets)
    - [Iterators](#iterators)
    - [Generators](#generators)
    - [`collections`](#collections)
        - [`namedtuple`](#namedtuple)
        - [`deque`](#deque)
        - [`Counter`](#counter)
        - [`defaultdict`](#defaultdict)
    - [`itertools`](#itertools)
        - [Infinite iterators](#infinite-iterators)
        - [Combinatoric iterators](#combinatoric-iterators)
        - [Others](#others)
    - [Map / filter / reduce](#map--filter--reduce)
        - [`filter`](#filter)
        - [`reduce`](#reduce)
    - [Sorting](#sorting)
        - [Inserting and preserving order](#inserting-and-preserving-order)
    - [Boolean](#boolean)
    - [Object oriented](#object-oriented)
        - [One-line constructors](#one-line-constructors)
    - [F-strings](#f-strings)
    - [File handling](#file-handling)

<!-- markdown-toc end -->
## Naming

### General

Choose appropriate words.

Instead of get, perhaps use:

- Fetch
- Download
- Receive

Properly name temporary variables. No more tmp etc.

## Basic data types

### Dictionary

- `update`
  - Adds elements to the dictionary if the key is not in the dictionary.

### Sets

- Union
- Update
  - Adds all elements of array B to set A. `A.update(B)`
- Intersection
- Difference

etc.

## Iterators

```python
class PowTwo:
    """Class to implement an iterator
    of powers of two"""

    def __init__(self, max = 0):
        self.max = max

    def __iter__(self):
        self.n = 0
        return self

    def __next__(self):
        if self.n <= self.max:
            result = 2 ** self.n
            self.n += 1
            return result
        else:
            raise StopIteration
```

## Generators

```python
def rev_str(my_str):
    length = len(my_str)
    for i in range(length - 1,-1,-1):
        yield my_str[i]
```

## `collections`

Alternative to pythons built-in containers.

### `namedtuple`

Use dataclasses instead.

### `deque`

`deque` can be used as a queue. For a stack use normal lists.

### `Counter`

`dict` subclass. Can be used as a multiset (set with duplicates allowed).

```python
Counter(['a','a','b','b','c'])

# Counter({'a': 2, 'b': 2, 'c': 1})
```

### `defaultdict`

`dict` subclass. Sets default type etc. for default dictionary argument. Prevents having to check for inclusion every time.

## `itertools`

Tools for iterables. 

### Infinite iterators

Repeat iterators.

- `count`
- `cycle`
- `repeat`

### Combinatoric iterators

- `product`
  - Computes the cartesian product of input iterables.
- `permutations`
  - All possible orderings, not repeated elements.
- `combinations`
  - In sorted orders.

### Others

- `accumulate`
- `chain`
- `compress`

## Map / filter / reduce

Functional approaches. Use comprehensions instead.

### `filter`

```python
number_list = range(-5, 5)
less_than_zero = list(filter(lambda x: x < 0, number_list))
```

### `reduce`

Only thing not reproducible using comprehensions. 

```python
product = 1
list = [1, 2, 3, 4]
for num in list:
    product = product * num
```

```python
product = reduce((lambda x, y: x * y), [1, 2, 3, 4])
```

## Sorting

### Inserting and preserving order

- `bisect`

## Boolean

- `any`
  - Return true when at least one of the elements is true.
- `all`
  - Return true when all the elements are true.

## Object oriented

### One-line constructors

```python
class A(object):
    def __init__(self, a, b, c, d, e, f):
        self.__dict__.update({k: v for k, v in locals().items() if k != 'self'})
```

### Dunder

- Difference between `__init__` and `__call__`.
  - init when initialise, call when called.


## F-strings

```python
a = 1
name = Joel

print(f'There is only {a} {name}.')
```

## File handling

```python
file = open("filename", mode)
```

Mainly use the following modes:

- `r`
  - read only
- `w`
  - write only
- Add `+`
  - update
   
Just loop through file to get line by line.
