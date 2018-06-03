---
layout: post
title:  "리스트 List - 파이썬 튜토리얼 따라가기 3"
date:   2018-01-27 17:30:00 +0900
programming:   true
categories: programming
tags:   programming app book ebook python
background-image: http://quantlabs.net/blog/wp-content/uploads/2015/11/pythonlogo.jpg
---
![image](http://www.msbiblog.com/wp-content/uploads/2016/09/Python_logo.png)
[Python.org](https://www.python.org)의 [The Python Tutorial](https://docs.python.org/3/tutorial/index.html)를 따라가며 설명한다.

# 리스트 List

리스트는 다양한 형태의 데이터를 순서대로 쌓아둔 것이다. 각 항목은 콤마 `,`로 구분하고 `[]`안에 둔다.
​
```
>>> squares = [1, 4, 9, 16, 25]
>>> squares
[1, 4, 9, 16, 25]
```
​
# 리스트 부분 선택

문자열과 마찬가지로, 파이썬에서 순서를 갖는 데이터는 순서대로 번호가 부여되고, 일부분을 뽑을 수 있다.
​
```
>>> squares[0]  # 번호에 맞는 항목
1
>>> squares[-1]
25
>>> squares[-3:]  # 부분 선택이 가능하다
[9, 16, 25]
```
​
## `[:]`

`[:]`는 처음부터 끝까지로 리스트 전체를 나타낸다. 

```
>>> squares[:]
[1, 4, 9, 16, 25]
```
​
# 리스트 수정, 합치기, 바꾸기

리스트는 다른 리스트와 합칠 수 있다.
​
```
>>> squares + [36, 49, 64, 81, 100]
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```
​
문자열은 특정 위치를 수정할 수 없지만, 리스트는 가능하다.
​
```
>>> cubes = [1, 8, 27, 65, 125]  # 리스트에 잘못된 부분이 보인다.
>>> 4 ** 3  # 4의 3제곱은 64
64
>>> cubes[3] = 64  # 리스트 cubes의 3번 위치의 값을 수정한다
>>> cubes
[1, 8, 27, 64, 125]
```
​
## append()

리스트는 append()로 마지막에 새로운 아이템을 추가할 수 있다. (append같은 것을 메쏘드(method)라고 한다)
​
```
>>> cubes.append(216)  # 6의 3제곱 값을 추가
>>> cubes.append(7 ** 3)  # 7의 3제곱 값을 추가
>>> cubes
[1, 8, 27, 64, 125, 216, 343]
```
​
리스트는 일부분을 수정, 삭제할 수 있다.
​
```
>>> letters = ['a', 'b', 'c', 'd', 'e', 'f', 'g']
>>> letters
['a', 'b', 'c', 'd', 'e', 'f', 'g']
>>> # 수정
>>> letters[2:5] = ['C', 'D', 'E']
>>> letters
['a', 'b', 'C', 'D', 'E', 'f', 'g']
>>> # 삭제
>>> letters[2:5] = []
>>> letters
['a', 'b', 'f', 'g']
>>> # 빈 리스트로
>>> letters[:] = []
>>> letters
[]
```
​
# len()

리스트에 파이썬 내장함수 len()을 사용할 수 있다.
​
```
>>> letters = ['a', 'b', 'c', 'd']
>>> len(letters)
4
```
​
# 리스트 속의 리스트

리스트는 리스트를 포함할 수 있다.
​
```
>>> a = ['a', 'b', 'c']
>>> n = [1, 2, 3]
>>> x = [a, n]
>>> x
[['a', 'b', 'c'], [1, 2, 3]]
>>> x[0]
['a', 'b', 'c']
>>> x[0][1]
'b'
```