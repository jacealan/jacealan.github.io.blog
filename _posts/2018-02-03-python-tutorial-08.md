---
layout: post
title:  "자료형 Data Structures - 파이썬 튜토리얼 따라가기 8"
date:   2018-02-03 17:30:00 +0900
programming:   true
categories: programming
tags:   programming app book ebook python
background-image: http://quantlabs.net/blog/wp-content/uploads/2015/11/pythonlogo.jpg
---
![image](http://www.msbiblog.com/wp-content/uploads/2016/09/Python_logo.png)
[Python.org](https://www.python.org)의 [The Python Tutorial](https://docs.python.org/3/tutorial/index.html)를 따라가며 설명한다.

# 리스트 메쏘드

리스트는 프로그래램을 할 때 가장 많이 다루는 자료형이다. 파이썬은 리스트를 위한 다양한 메쏘드를 가지고 있다.

## list.append(x)

리스트의 맨 뒤에 새로운 값을 추가한다. `a[len(a):] = [x]`과 같은 기능을 한다.

## list.extend(iterable)

리스트와 리스트를 합친다. iterable 리스트의 내용을 기존 리스트에 붙여서 리스트를 확장한다. 리스트 전체를 하나의 값으로 추가하는 것과 구분해야 한다. `a[len(a):] = iterable`과 같은 기능을 한다.

## list.insert(i, x)

i 인덱스에 x를 추가하고 뒷부분을 하나씩 밀어낸다. `a.insert(0, x)`는 리스트의 맨앞에 새 값을 추가한다. `a.insert(len(a), x)`는 리스트의 뒤에 새 값을 추가한다.

## list.remove(x)

리스트에 있는 x값 중 맨 앞의 것을 제거한다. 만약 리스트에 x값이 없으면 에러가 발생한다.

## list.pop([i])

`list.pop()`은 리스트의 마지막값을 제거한다. `print(list.pop())`은 리스트의 마지막 값을 리스트에서 제거하고, 제거하는 값을 출력한다. 파이썬 설명 문서들에서 `[]`는 옵션 인자를 나타낸다. 해당 인자는 필요에 따라 추가하면 된다. 원하는 i 인덱스의 값을 제거하고 싶다면 `()`에 그 인덱스를 넣는다.

## list.clear()

리스트의 모든 값을 지운다. `del a[:]`와 같은 기능을 한다.

## list.index(x[, start[, end]])

리스트에서 x 값의 인덱스를 나타낸다. 파이썬의 인덱스는 기본적으로 0부터 시작한다. 해당 값이 없으면 에러가 발생한다.

x 값을 찾기 위한 구간을 지정할 수 있다. 구간을 지정해도, 나타내는 인덱스값은 전체 리스트를 기준으로 한다.

## list.count(x)

리스트에 x값이 몇 개 있는지 리턴한다.

## list.sort(key=None, reverse=False)

리스트를 정렬한다. 정렬 방식에 대해서는 `sorted()`를 설명할 때 추가 설명한다.

## list.reverse()

리스트의 순서를 뒤집는다.

## list.copy()

리스트 전체를 나타낸다. `a[:]`와 같은 기능을 한다.

아래 예를 통해 메쏘드의 기능을 다시 한번 확인한다.

```
>>> fruits = ['orange', 'apple', 'pear', 'banana', 'kiwi', 'apple', 'banana']
>>> fruits.count('apple') # apple은 몇개?
2
>>> fruits.count('tangerine') # tangerline은 몇개?
0
>>> fruits.index('banana') # banana의 index는?
3
>>> fruits.index('banana', 4)  # 4 인덱스뒤에 있는 banana의 index는?
6
>>> fruits.reverse() # 순서 뒤집기
>>> fruits
['banana', 'apple', 'kiwi', 'banana', 'pear', 'apple', 'orange']
>>> fruits.append('grape') # 맨 뒤에 grape를 추가한다.
>>> fruits
['banana', 'apple', 'kiwi', 'banana', 'pear', 'apple', 'orange', 'grape']
>>> fruits.sort() # 리스트를 알파벳순으로 정렬한다.
>>> fruits
['apple', 'apple', 'banana', 'banana', 'grape', 'kiwi', 'orange', 'pear']
>>> fruits.pop() # 리스트의 마지막 값은?
'pear'
```

# 스택 Stacks

append, pop은 리스트를 스택처럼 다룬다. 스택은 새 값을 마지막에 추가하고, 마지막 값부터 제거한다.

```
>>> stack = [3, 4, 5]
>>> stack.append(6)
>>> stack.append(7)
>>> stack
[3, 4, 5, 6, 7]
>>> stack.pop()
7
>>> stack
[3, 4, 5, 6]
>>> stack.pop()
6
>>> stack.pop()
5
>>> stack
[3, 4]
```

# 큐 Queues

큐는 맨 앞에 새 값을 추가하고, 맨 앞 값부터 제거한다. 스택과 반대이다. 파이썬의 리스트는 큐로써 이용할 수 있다. 다만, 스택으로 이용할 때에 비해 많이 느리다. 리스트 전체를 밀고, 당겨야하기 때문이다. [collections.deque](https://docs.python.org/3/library/collections.html#collections.deque)는 이런 단점 없이 스택으로, 큐로 이용할 수 있다.

```
>>> from collections import deque
>>> queue = deque(["Eric", "John", "Michael"])
>>> queue.append("Terry")           # Terry arrives
>>> queue.append("Graham")          # Graham arrives
>>> queue.popleft()                 # The first to arrive now leaves
'Eric'
>>> queue.popleft()                 # The second to arrive now leaves
'John'
>>> queue                           # Remaining queue in order of arrival
deque(['Michael', 'Terry', 'Graham'])
```

# 리스트 컴프레힌션 List Comprehensions

기존 리스트의 값들을 연산해 새로운 리스트를 만드는 경우가 많다.

```
>>> squares = []
>>> for x in range(10):
...     squares.append(x**2)
...
>>> squares
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

람다 함수(lambda)와 매핑(map)를 이용해 이러한 리스트 연산을 간단히 할 수 있다.

```
squares = list(map(lambda x: x**2, range(10)))
```

파이썬은 List Comrehensions로 이를 더 쉽고 편하게 할 수 있다.

```
squares = [x**2 for x in range(10)]
```

for, if의 다중 이용도 가능하다.

```
>>> [(x, y) for x in [1,2,3] for y in [3,1,4] if x != y]
[(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]
```

이를 기존의 코딩 형식으로 만들면 다음과 같다.

```
>>> combs = []
>>> for x in [1,2,3]:
...     for y in [3,1,4]:
...         if x != y:
...             combs.append((x, y))
...
>>> combs
[(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]
```

다음 예에서 리스트 컴프레힌션의 활용법을 알아본다.

```
>>> vec = [-4, -2, 0, 2, 4]
>>> # create a new list with the values doubled
>>> [x*2 for x in vec]
[-8, -4, 0, 4, 8]
>>> # filter the list to exclude negative numbers
>>> [x for x in vec if x >= 0]
[0, 2, 4]
>>> # apply a function to all the elements
>>> [abs(x) for x in vec]
[4, 2, 0, 2, 4]
>>> # call a method on each element
>>> freshfruit = ['  banana', '  loganberry ', 'passion fruit  ']
>>> [weapon.strip() for weapon in freshfruit]
['banana', 'loganberry', 'passion fruit']
>>> # create a list of 2-tuples like (number, square)
>>> [(x, x**2) for x in range(6)]
[(0, 0), (1, 1), (2, 4), (3, 9), (4, 16), (5, 25)]
>>> # the tuple must be parenthesized, otherwise an error is raised
>>> [x, x**2 for x in range(6)]
  File "<stdin>", line 1, in <module>
    [x, x**2 for x in range(6)]
               ^
SyntaxError: invalid syntax
>>> # flatten a list using a listcomp with two 'for'
>>> vec = [[1,2,3], [4,5,6], [7,8,9]]
>>> [num for elem in vec for num in elem]
[1, 2, 3, 4, 5, 6, 7, 8, 9]
```

리스트 컴프레힌션에서는 함수의 이용도 가능하다.

```
>>> from math import pi
>>> [str(round(pi, i)) for i in range(1, 6)]
['3.1', '3.14', '3.142', '3.1416', '3.14159']
```

## 행열 바꾸기, 복잡한 리스트 컴프레힌션

다음처럼 3x4 행렬을 4x3 행렬로 바꾸는 것도 가능하다.

```
>>> matrix = [
...     [1, 2, 3, 4],
...     [5, 6, 7, 8],
...     [9, 10, 11, 12],
... ]
>>> [[row[i] for row in matrix] for i in range(4)]
[[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]
```

이것을 한단계 풀어서 보면 다음과 같다.

```
>>> transposed = []
>>> for i in range(4):
...     transposed.append([row[i] for row in matrix])
...
>>> transposed
[[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]
```

리스트 컴프레힌션을 사용하지 않으면 다음처럼 할 수 있다.

```
>>> transposed = []
>>> for i in range(4):
...     # the following 3 lines implement the nested listcomp
...     transposed_row = []
...     for row in matrix:
...         transposed_row.append(row[i])
...     transposed.append(transposed_row)
...
>>> transposed
[[1, 5, 9], [2, 6, 10], [3, 7, 11], [4, 8, 12]]
```

하지만, 행열을 바꿔야 한다면, 다음처럼 zio() 함수를 이용하는 것이 좋다.

```
>>> list(zip(*matrix))
[(1, 5, 9), (2, 6, 10), (3, 7, 11), (4, 8, 12)]
```

# del

리스트를 한 인덱스를 제거하는데는 pop() 메쏘드를 이용한다.  del 명령은 리스트의 한 인덱스, 구간, 전체를 제거할 수 있다. 또한 리스트 변수 자체를 지울 수도 있다.

```
>>> a = [-1, 1, 66.25, 333, 333, 1234.5]
>>> del a[0]
>>> a
[1, 66.25, 333, 333, 1234.5]
>>> del a[2:4]
>>> a
[1, 66.25, 1234.5]
>>> del a[:]
>>> a
[]
>>> del a
>>> a
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'a' is not defined
```