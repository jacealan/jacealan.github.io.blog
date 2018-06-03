---
layout: post
title:  "문자열 Strings - 파이썬 튜토리얼 따라가기 2"
date:   2018-01-26 17:30:00 +0900
programming:   true
categories: programming
tags:   programming app book ebook python
background-image: http://quantlabs.net/blog/wp-content/uploads/2015/11/pythonlogo.jpg
---
![image](http://www.msbiblog.com/wp-content/uploads/2016/09/Python_logo.png)
[Python.org](https://www.python.org)의 [The Python Tutorial](https://docs.python.org/3/tutorial/index.html)를 따라가며 설명한다.

# 문자, 문자열

파이썬에서 문자나 문자열은 큰따옴표(`"`) 또는 작은따옴표(`'`) 사이에 둔다. 큰따옴표, 작음따옴표 사이에 포함 관계는 없다. 동일한 문자열 기호다. 많은 컴퓨팅 관련 문법처럼 `\`는 약속된 기능을 무시하고 글자 그대로 인식시킨다. 파이썬 인터액티브 모드(Python Interactive Mode)로 문자열을 사용해보자.

# 큰따옴표 ", 작은따옴표 '

```
>>> 'spam eggs'  # 작음따옴표 사이에
'spam eggs'
>>> 'doesn\'t'  # \로 '의 문자열 기능 없는 하나의 문자로 인식시킨다
"doesn't"
>>> "doesn't"  # 큰따옴표 사이에
"doesn't"
>>> '"Yes," he said.' # 작은따옴표, 큰따옴표를 겹쳐 사용하면 내부의 따옴표는 단순 문자다
'"Yes," he said.'
>>> "\"Yes,\" he said."
'"Yes," he said.'
>>> '"Isn\'t," she said.' # 아래와 비교
'"Isn\'t," she said.'
>>> '"Isn\"t," she said.' # print()를 사용한 아래 예제와 같이 비교 이해
'"Isn"t," she said.'
```

# print()
print()는 파이썬의 출력 함수다. 출력에 필요한 기능, 형식을 모두 적용해서 출력한다. 위에서 사용한 인터액티브 모드의 입력은 입력한 것을 그대로 다시 한번 정리해서 보여주는 것이다. 그리서 문자열이라는 표시로 작은따옴표나 큰따옴표로 묶어서 나타낸다. print()를 사용하면 원하는 출력 형태 그대로 나타낸다.

```
>>> '"Isn\'t," she said.'
'"Isn\'t," she said.'
>>> print('"Isn\'t," she said.')
"Isn't," she said.
>>> s = 'First line.\nSecond line.'  # \n 은 줄바꿈 표시
>>> s  # print()를 사용하지 않으면, \n 을 그대로 보여준다
'First line.\nSecond line.'
>>> print(s)  # print()를 사용하면 각 기호의 기능이 모두 적용된 결과물을 출력한다.
First line.
Second line.
>>> print('"Isn\'t," she said.') # 위의 예제와 비교
"Isn't," she said.
>>> print('"Isn\"t," she said.') # 위의 예제와 비교
"Isn"t," she said.
```

# `\`보다 강력한 `r`
문자열 속의 `\`는 `\` 다음 글자의 특수 기능과 의미를 제거한다. 문자열 따옴표 앞에 `r`을 붙이면 따옴표 안의 모든 글자를 단순 글자(raw string)로 이해한다.

```
>>> print('C:\some\name')  # \n 을 줄바꿈으로 이해
C:\some
ame
>>> print(r'C:\some\name')  # 따옴표 앞의 r 때문에 모두 글자로
C:\some\name
>>> print(r'"Isn\'t," she said.') # 위의 예제들과 비교
"Isn\'t," she said.
>>> print(r'"Isn\"t," she said.') # 위의 예제들과 비교
"Isn\"t," she said.
```

# 삼겹따옴표(`'''`, `"""`)로 여러줄도 OK
문자열을 여러줄로 나타내려면 삼겹따옴표를 이용한다. 파이썬에서 맨 끝의 `\`는 줄을 바꿔서 이어간다는 표시이다. `'''`, `"""`를 이용하면 `\`없이 여러줄 문자열이 가능하다.

```
>>> print("""\
... Usage: thingy [OPTIONS]
...      -h                        Display this usage message
...      -H hostname               Hostname to connect to
... """)
Usage: thingy [OPTIONS]
     -h                        Display this usage message
     -H hostname               Hostname to connect to
```

위의 예에서 `print("""\`의 `\`는 줄바꿈 입력을 위한 표시이다. 줄을 바꿔서 입력을 이어가야 할 때 파이썬은 앞에 `>>>`이 아닌 `...`으로 앞에서 이어지고 있다고 표시한다.

# 문자열 * 숫자

파이썬에서 문자열에 숫자를 곱하면 숫자만큼 해당 문자열을 숫자만큼 반복해서 붙인다.

```
>>> # 3 times 'un', followed by 'ium'
>>> 3 * 'un' + 'ium'
'unununium'
```

# 문자열 자동 합체
두개 이상의 문자열을 옆에 두면 자동으로 붙는다.

```
>>> 'Py' 'thon'
'Python'
```

이 기능을 이용하면, 파이썬에서 긴 문자열을 입력할 때 나누어서 입력할 수 있다.

```
>>> text = ('Put several strings within parentheses '
...         'to have them joined together.')
>>> text
'Put several strings within parentheses to have them joined together.'
```

단, 자동 합체 기능은 순수 문자열 끼리만 가능하다. 변수를 이용하거나, 위의 문자열 * 숫자 등에서 자동 합체 기능을 이용하면 에러가 발생한다.

```
>>> prefix = 'Py'
>>> prefix 'thon'  # can't concatenate a variable and a string literal
  ...
SyntaxError: invalid syntax
>>> ('un' * 3) 'ium'
  ...
SyntaxError: invalid syntax
```

# + 로 문자열 붙이기
문자열을 붙이는 연산자는 `+`이다. 앞의 것은 편의를 위한 특수 기능이다.

```
>>> prefix + 'thon'
'Python'
```

# 문자열 속 문자 위치

문자열은 맨 앞부터 각 문자에 0, 1, 2, 3, ... 으로 번호를 붙여둔다. 원하는 위치의 문자는 `[]`를 이용한다.

```
>>> word = 'Python'
>>> word[0]  # 0번째 문자
'P'
>>> word[5]  # 6번째 문자
'n'
>>> word[-1]  # 마지막 문자
'n'
>>> word[-2]  # 뒤에서 두번째 문자
'o'
>>> word[-6] # 뒤에서 6번째 문자
'P'
```

`[시작위치:끝위치]'로 문자열의 일부 구간을 확인할 수 있다.

```
>>> word[0:2]  # 0번째부터 2번째 전까지
'Py'
>>> word[2:5]  # 2번째부터 5번째 전까지
'tho'
```

시작위치가 없으면 처음부터, 끝위치가 없으면 마지막까지를 나타낸다.

```
>>> word[:2] + word[2:]
'Python'
>>> word[:4] + word[4:]
'Python'
>>> word[:2]   # character from the beginning to position 2 (excluded)
'Py'
>>> word[4:]   # characters from position 4 (included) to the end
'on'
>>> word[-2:]  # characters from the second-last (included) to the end
'on'
```

시작위치와 끝위치의 번호가 혼동되면 다음 그림을 참조한다. 

```
 +---+---+---+---+---+---+
 | P | y | t | h | o | n |
 +---+---+---+---+---+---+
 0   1   2   3   4   5   6
-6  -5  -4  -3  -2  -1
```

파이썬 문자열의 위치가 잘못되면 에러가 발생한다.

```
>>> word[42]  # the word only has 6 characters
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: string index out of range
```

하지만, 문자열의 구간에서는 문자열 밖의 위치를 나타내도 적절히 해석한다.

```
>>> word[4:42]
'on'
>>> word[42:]
''
```

# 문자열은 부분 수정이 불가능

문자열은 전체가 하나의 값이어서, 일부분을 수정할 수 없다. 

```
>>> word[0] = 'J'
  ...
TypeError: 'str' object does not support item assignment
>>> word[2:] = 'py'
  ...
TypeError: 'str' object does not support item assignment
```

문자열의 일부를 바꾸려면 새로 문자열을 만들어야 한다.

```
>>> 'J' + word[1:]
'Jython'
>>> word[:2] + 'py'
'Pypy'
```

문자열 변수에 새로운 문자열을 넣는 것은 가능하다.

```
>>> word = 'test'
>>> word
'test'
```

# 문자열 길이 len()

len()는 문자열의 길이, 글자수를 나타낸다.

```
>>> s = 'supercalifragilisticexpialidocious'
>>> len(s)
34
```