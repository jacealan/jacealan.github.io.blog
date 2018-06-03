---
layout: post
title:  "제어문 Control Flow Tools - 파이썬 튜토리얼 따라가기 5"
date:   2018-01-30 17:30:00 +0900
programming:   true
categories: programming
tags:   programming app book ebook python
background-image: http://quantlabs.net/blog/wp-content/uploads/2015/11/pythonlogo.jpg
---
![image](http://www.msbiblog.com/wp-content/uploads/2016/09/Python_logo.png)
[Python.org](https://www.python.org)의 [The Python Tutorial](https://docs.python.org/3/tutorial/index.html)를 따라가며 설명한다.

# 제어문

앞 글에서 while로 명령 묶음을 제어하는 방법을 소개했다. 이제 다양한 제어문을 알아본다.

# if

조건을 만족하는지 못하는지에 따라 다음 명령을 선택하는 제어문이다. if 뒤에 조건을 넣고 아래에 들여쓰기로 조건을 만족할 때 실행할 명령을 넣는다. 조건을 만족하지 못할 때 실행할 명령이 있다면 else 밑에 들여쓰기한다. else if 는 elif로 표현할 수 있다. 이때 if.. elif.. elif.. elif.. else로 elif를 연달아 사용할 수 있다.

```
>>> x = int(input("Please enter an integer: ")) # 키보드 입력을 받아 변수 x에 숫자로 할당한다
Please enter an integer: 42 # x는 이제 숫자 42
>>> if x < 0: # x가 0보다 작으면 아래 들여쓰기된 문장들을 모두 실행한다.
...     x = 0
...     print('Negative changed to zero')
... elif x == 0: # x가 0보다 작지 않으면, 그리고 x가 0이면
...     print('Zero')
... elif x == 1: # x가 0보다 작지 않고, x가 0이 아니고, x가 1이면
...     print('Single')
... else: # 위의 조건을 모두 만족하지 않으면
...     print('More')
...
More
```

# for

파이썬의 for는 리스트(또는 순서가 있는 아이템 모음)의 항목들을 처음부터 하나씩 순차적으로 사용해서 반복하도록 한다. 아래의 예에서 words는 3개의 단어로 이루어진 리스트이다. for 제어문은 words의 3 단어를 하나씩 w에 할당해서 들여쓰기한 명령들을 수행한다.

```
>>> # Measure some strings:
... words = ['cat', 'window', 'defenestrate']
>>> for w in words:
...     print(w, len(w))
...
cat 3
window 6
defenestrate 12
```

for 문을 수행하면서 for 문의 리스트가 변하는 경우 구간 선택문으로 실행하면, 중간에 리스트가 바뀌어도 for 문의 리스트에는 영향을 미치지 않는다. 아래 에에서, `for w in words:`로 구간 선택이 아닌 리스트를 그대로 for문을 실행하면 무한 루프에 빠지게 된다.

```
>>> for w in words[:]:  # Loop over a slice copy of the entire list.
...     if len(w) > 6:
...         words.insert(0, w)
...
>>> words
['defenestrate', 'cat', 'window', 'defenestrate']
```

# range()

range()는 수열을 만드는 간단한 함수이다. 아래 예의 range(5)는 0, 1, 2, 3, 4이다. 하나의 수를 넣으면 0부터 주어진 수 바로 전 수까지의 정수 수열을 나타낸다.

```
>>> for i in range(5):
...     print(i)
...
0
1
2
3
4
```

range() 함수는 (시작, 끝, 간격) 형식이다. range(5, 10)는 5 ~ 9 즉, 5부터 10 전까지이다. range(0, 10, 3)은 0, 3, 6, 9이다. 0부터 10전까지 3씩 증가한다. range(-10, -100, -30)는 -10, -40, -70이다. 간격을 음수로 지정해서 감소하는 수열도 가능하다.

다음은 리스트에 len(), range()를 활용한 예로 리스트 각각에 인덱싱을 하는 것이다. 실제로 리스트에 인덱싱이 필요하면 enumerate() 함수를 사용하는 것이 더 좋다.

```
>>> a = ['Mary', 'had', 'a', 'little', 'lamb']
>>> for i in range(len(a)):
...     print(i, a[i])
...
0 Mary
1 had
2 a
3 little
4 lamb
```

주의할 것은 range() 함수는 리스트를 만들지 않는다는 점이다. 이는 메모리 확보에도 도움이 된다. range() 함수로 만들어지는 수열을 리스트로 만들려면 list() 함수를 이용한다.

```
>>> print(range(10))
range(0, 10)
>>> list(range(5))
[0, 1, 2, 3, 4]
```

# break, else

break는 for나 while같은 반복문(loop)를 중간에 멈추고 나오도록 한다.

for나 while에 else가 있으면, break에 의한 강제 정지 없이 반복문이 모두 완료되었을 때 실행되는 명령 묶음을 만들 수 있다.

```
>>> for n in range(2, 10):
...     for x in range(2, n):
...         if n % x == 0: # 소인수를 찾으면
...             print(n, 'equals', x, '*', n//x) # 소인수를 출력하고
...             break # x의 for문을 정지한다.
...     else: # x의 for문이 소인수를 찾지 못해서, break없이 끝나면
...         print(n, 'is a prime number') # 솟수라고 출력한다.
...
2 is a prime number
3 is a prime number
4 equals 2 * 2
5 is a prime number
6 equals 2 * 3
7 is a prime number
8 equals 2 * 4
9 equals 3 * 3
```

# continue

continue는 반복문(for, while)의 실행 중 실행 중이던 회차의 명령들을 멈추고 다음 회차를 시작하도록 한다.

```
>>> for num in range(2, 10):
...     if num % 2 == 0: # num이 2로 나누어 떨어지면
...         print("Found an even number", num) # 짝수라고 출력하고
...         continue # num을 다음 수로 바꾸고 for의 명령들을 다시 시작한다.
...     print("Found a number", num) # 홀수라고 출력한다.
Found an even number 2
Found a number 3
Found an even number 4
Found a number 5
Found an even number 6
Found a number 7
Found an even number 8
Found a number 9
```

# pass

pass는 아무런 기능이 없다. 그냥 지나쳐간다. 다음처럼 형식적으로 필요한 위치에 이용한다.

```
>>> while True:
...     pass  # 강제 종료(Ctrl+C) 전까지 계속 while을 반복한다.
...
>>> class MyEmptyClass:
...     pass
...
>>> def initlog(*args):
...     pass   # 일단 프로그램 구조를 만들어둘 때 유용하다.
...
```