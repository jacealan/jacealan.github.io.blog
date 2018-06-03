---
layout: post
title:  "첫 프로그래밍 - 파이썬 튜토리얼 따라가기 4"
date:   2018-01-28 17:30:00 +0900
programming:   true
categories: programming
tags:   programming app book ebook python
background-image: http://quantlabs.net/blog/wp-content/uploads/2015/11/pythonlogo.jpg
---
![image](http://www.msbiblog.com/wp-content/uploads/2016/09/Python_logo.png)
[Python.org](https://www.python.org)의 [The Python Tutorial](https://docs.python.org/3/tutorial/index.html)를 따라가며 설명한다.

# 파이썬 프로그램 형식

파이썬에서도 복잡한 문제 해결을 위해 2줄 이상의 소스 코드를 작성할 수 있다. 다음은 10보다 작은 피보나치 수열을 보여주는 프로그램이다.
​2018
```
>>> # Fibonacci series:
... # the sum of two elements defines the next
... a, b = 0, 1
>>> while b < 10:
...     print(b)
...     a, b = b, a+b
...
1
1
2
3
5
8
```
​
# x, y = 1, 2

`a, b = 0, 1`은 a에 0을, b에 1을 입력하는 명령을 한번에 처리하는 것이다. 아래의 `a, b = b, a+b`도 a에 b의 값을, b에 a의 값과 b의 값의 합을 입력하는 것이다.

# 들여쓰기 (while, loop, body)
​
while은 뒤의 조건이 참일 때, 아래 명령들을 반복(loop)하도록 한다. 위의 예에서, b가 0인 상태에서 while의 조건이 참이므로 아래의 print(b) 등을 수행한다. while이 반복할 내용들은 loop의 body라고 한다. body는 모두 들여쓰기를 해야 한다. 이때 들여쓰기 한 칸, 두 칸, 등 자유롭게 할 수 있지만 모두 동일한 양만큼 들여쓰기 해야한다. 파이썬에서는 4칸 들여쓰기를 권장한다. 파이선 인터액티브 모드에서 body는 빈 줄로 끝난다.
​
## Visual Studio Code

일반 텍스트 편집기는 이런 줄맞춤, 들여쓰기 등이 불편하다. 그래서 다양한 프로그래밍을 위한 에디터(editor)가 이용된다. 제이스는 현재 Visual Studio Code를 이용한다. 관련 내용은 다음을 참조한다.

[프로그래밍 환경, 제이스의 맥북](https://jacealan.github.io/2018-01-20-setup-for-programming.html)

# print()
​
파이썬의 print는 출력 명령이 끝나면 줄을 바꿔서 맨앞으로 가게 되있다. 이를 바꾸려면 print의 마지막 부분을 고쳐야한다. end라는 키워드로 마지막을 줄바꿈을 결정할 수 있다. 다음 예는 print의 마지막을 `,`로 바꾸고 줄바꿈하지 않도록 한다.
​
```
>>> a, b = 0, 1
>>> while b < 1000:
...     print(b, end=',')
...     a, b = b, a+b
...
1,1,2,3,5,8,13,21,34,55,89,144,233,377,610,987,
```
​
​