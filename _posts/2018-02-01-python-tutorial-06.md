---
layout: post
title:  "함수 Function - 파이썬 튜토리얼 따라가기 6"
date:   2018-02-01 17:30:00 +0900
programming:   true
categories: programming
tags:   programming app book ebook python
background-image: http://quantlabs.net/blog/wp-content/uploads/2015/11/pythonlogo.jpg
---
![image](http://www.msbiblog.com/wp-content/uploads/2016/09/Python_logo.png)
[Python.org](https://www.python.org)의 [The Python Tutorial](https://docs.python.org/3/tutorial/index.html)를 따라가며 설명한다.

# 함수

앞에 만들었던 피보나치 수열 프로그램을 한 덩어리로 함수를 만들 수 있다. 함수의 선언은 def로 한다. 함수 이름을 정하고 파라미터를 괄호안에 넣는 형태이다. 함수의 바디는 함수 선언 다음줄부터 들여쓰기로 작성한다.

함수 바디의 시작에 선택적으로 함수의 설명(Documemtation Strings)을 추가할 수 있다. 관련 설명은 뒤에서 한다.

```
>>> def fib(n):    # 함수 선언
...     """Print a Fibonacci series up to n.""" # 함수 설명
...     a, b = 0, 1
...     while a < n:
...         print(a, end=' ')
...         a, b = b, a+b
...     print()
...
>>> # 함수 사용
... fib(2000)
0 1 1 2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

파이썬에서는 함수에 등호(=) 연산이 가능하다. 이를 통해 함수의 이름을 변경하는 것도 가능하다.

```
>>> fib
<function fib at 10042ed0>
>>> f = fib
>>> f(100)
0 1 1 2 3 5 8 13 21 34 55 89
```

보통 함수라고 하면 실행 후 일정 값을 반환(return)한다. 하지만 위의 fib()는 반환 값이 없다. 이런 경우 반환 값이 None이라고 한다.

```
>>> fib(0)
>>> print(fib(0))
None
```

다음처럼 함수가 반환 값을 갖도록 할 수 있다. 함수의 반환 값은 다양한 형식이 가능하다.

```
>>> def fib2(n):
...     """Return a list containing the Fibonacci series up to n."""
...     result = []
...     a, b = 0, 1
...     while a < n:
...         result.append(a)
...         a, b = b, a+b
...     return result
...
>>> f100 = fib2(100)
>>> f100
[0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
```

위에서 append()는 메쏘드 method라고 한다. 메쏘드는 하나의 오브젝트(object)에 속한 함수로, 오브젝트의 형식에 따라 메쏘드는 다를 수도 같을 수도 있다. append(a)는 리스트의 마지막에 항목을 추가하는 메쏘드다.

# 함수 변수 전달 방법

함수를 부를 때 필요한 변수를 전달한다. 이때 전달받는 변수에 대해서 기본 값을 설정해두면, 함수를 이용할 때 기본값이 있는 변수는 전달하지 않아도 된다.

```
def ask_ok(prompt, retries=4, reminder='Please try again!'):
    while True:
        ok = input(prompt)
        if ok in ('y', 'ye', 'yes'): # in은 뒤에 나열된 것에 앞의 것이 속하는지 여부를 판단한다
            return True
        if ok in ('n', 'no', 'nop', 'nope'):
            return False
        retries = retries - 1
        if retries < 0:
            raise ValueError('invalid user response')
        print(reminder)
```

위에 처럼 ask_ok()라는 함수를 정의했다면, 함수를 이용하는 방법은 3가지다.

## ask_ok('Do you really want to quit?')

이것은 ask_ok()의 prompt 변수만 전달하는 방법이다. ask_ok() 함수를 이용할 때 prompt는 만드시 포함해야 한다.

## ask_ok('OK to overwrite the file?', 2)

ask_ok() 함수 이용 시, 기본값이 설정된 변수는 선택적으로 전달 할 수 있다.

## ask_ok('OK to overwrite the file?', 2, 'Come on, only yes or no!')

물론, ask_ok() 함수 이용 시, 기본값이 설정된 변수 모두 다르게 전달할 수 있다.

# 퀴즈, 출력값은?

```
i = 5

def f(arg=i):
    print(arg)

i = 6
f()
```

위에서 f()는 5이다. 함수의 선언(def)때 i 값이 5이기 때문이다.

함수를 선언할 때 기본 설정 값이 변경가능한 것(mutable object)이면 기본 설정값은 최소 선언시에만 적용된다. 따라서 같은 함수를 반복적으로 부르면 기본 설정값은 최초에만 적용된다. 함수를 부를 때마다 해당 함수 내의 변수값은 그대로 유지된다.

```
def f(a, L=[]):
    L.append(a)
    return L

print(f(1))
print(f(2))
print(f(3))
```

위 프로그램의 출력은 다음과 같다.

```
[1]
[1, 2]
[1, 2, 3]
```

함수의 선언에서 `L=[]`이 아니라 아래처럼 `L=None`으로 고정 상수로 기본설정하면, 모두 같은 결과([1])을 출력한다.

```
def f(a, L=None):
    if L is None:
        L = []
    L.append(a)
    return L
```

# 키워드 인자

함수에서 선언된 인자은 함수 요청시 키워드=값 형태로 전달할 수 있다. 기본값 설정이 없는 인자는 반드시 전달되어야 한다.

```
def parrot(voltage, state='a stiff', action='voom', type='Norwegian Blue'):
    print("-- This parrot wouldn't", action, end=' ')
    print("if you put", voltage, "volts through it.")
    print("-- Lovely plumage, the", type)
    print("-- It's", state, "!")
parrot(1000)                                          # 1 positional argument
parrot(voltage=1000)                                  # 1 keyword argument
parrot(voltage=1000000, action='VOOOOOM')             # 2 keyword arguments
parrot(action='VOOOOOM', voltage=1000000)             # 2 keyword arguments
parrot('a million', 'bereft of life', 'jump')         # 3 positional arguments
parrot('a thousand', state='pushing up the daisies')  # 1 positional, 1 keyword
```

위에서 voltage의 값으로 1000, 'a million', 'a thousand' 등처럼 수도, 문자열도 이용 가능하다. 이것은 파이썬의 변수가 특정 타입으로 고정되지 않기 때문이다.

아래는 잘못된 함수 요청이다.

```
parrot()                     # 필수 인자 voltage가 빠짐
parrot(voltage=5.0, 'dead')  # 위치로 판별되는 인자는 키워드 인자 앞에 위치해야 한다
parrot(110, voltage=220)     # 위치 판별 인자가 voltage인데 키워드 인자로 voltage를 또 포함한다
parrot(actor='John Cleese')  # actor는 키워드 인자가 아니다
```

키워드 인자는 순서 상관없다. 단, 위치 판별 인자는 키워드 인자 앞쪽에 있어야 한다. 그리고 기본값이 설정된 키워드 인자는 함수 요청시 필수 인자가 아니다.

## **keywords

함수를 선언할 때 필요 인자를 모두 정확하게 설정해야하는 것은 아니다. 먼저 다음 예를 보자.

```
def cheeseshop(kind, *arguments, **keywords):
    print("-- Do you have any", kind, "?")
    print("-- I'm sorry, we're all out of", kind)
    for arg in arguments:
        print(arg)
    print("-" * 40)
    for kw in keywords:
        print(kw, ":", keywords[kw])

cheeseshop("Limburger", "It's very runny, sir.",
           "It's really very, VERY runny, sir.",
           shopkeeper="Michael Palin",
           client="John Cleese",
           sketch="Cheese Shop Sketch")
```

함수를 선언할 때, `*`, `**`는 특별한 표시다. `**keywords`는 예에서 보이는 shopkeeper="Michael Palin", client="John Cleese", sketch="Cheese Shop Sketch"들을 표시한다. 파이썬의 딕셔너리 형식으로 인자를 전달한다. 미리 설정한 인자와 `**keyword` 사이에는 `*arguments`가 들어올 수 있는데, 이것은 튜퓰 형식으로 함수를 이용할 때 앞에 설정한 인자와 뒤쪽의 딕셔너리 인자 사이의 인자들을 튜플로 받는다. (딕셔너리, 튜플 등은 다음 포스트에서 설명한다) 위의 결과는 다음과 같다.

```
-- Do you have any Limburger ?
-- I'm sorry, we're all out of Limburger
It's very runny, sir.
It's really very, VERY runny, sir.
----------------------------------------
shopkeeper : Michael Palin
client : John Cleese
sketch : Cheese Shop Sketch
```

보통, 튜플, 딕셔너리 인자를 뒤쪽에 두지만, 기본값을 갖는 인자는 그 뒤에 놓여도 문제없다. 단, 함수의 인자 전달을 프로그래머 자신이 정확히 이해할 수 있게 하는 것이 좋다.

```
>>> def concat(*args, sep="/"):
...     return sep.join(args)
...
>>> concat("earth", "mars", "venus")
'earth/mars/venus'
>>> concat("earth", "mars", "venus", sep=".")
'earth.mars.venus'
```

함수에 전달할 인자를 리스트나 딕셔너리로 그룹화해두었다면 `*`, `**`를 이용해서 간단히 이용할 수 있다. 리스트의 경우는 `*list`로 리스트의 값들을 순서대로 함수의 인자로 전달할 수 있다. 딕셔너리는 `**dictionary`로 이용할 수 있다.

```
>>> list(range(3, 6))            # normal call with separate arguments
[3, 4, 5]
>>> args = [3, 6]
>>> list(range(*args))            # call with arguments unpacked from a list
[3, 4, 5]
```

```
>>> def parrot(voltage, state='a stiff', action='voom'):
...     print("-- This parrot wouldn't", action, end=' ')
...     print("if you put", voltage, "volts through it.", end=' ')
...     print("E's", state, "!")
...
>>> d = {"voltage": "four million", "state": "bleedin' demised", "action": "VOOM"}
>>> parrot(**d)
-- This parrot wouldn't VOOM if you put four million volts through it. E's bleedin' demised !
```

# 람다 함수 lambda function

익명함수라고 불리는 람다 함수는 함수의 간략형(?)이다. 다음 예에서 `f=lambda x: x + 42`가 된다. 그리고 f(0)를 하면 x=0이 되어서 0+42, 즉 42가 된다. 람다 함수도 나중에 다시 설명할 기회가 있을 것이다.

```
>>> def make_incrementor(n):
...     return lambda x: x + n
...
>>> f = make_incrementor(42)
>>> f(0)
42
>>> f(1)
43
```

# 함수안내문 Documentation Strings

함수를 선언할 때 def 바로 아래에 `"""    """`로 함수에 대한 설명을 넣으면 좋다고 앞에서 설명했다. 이 설명을 확인할 수 있다. 아래의 예처럼 my_function 함수의 Documentation Strings를 `__doc__`로 불러올 수 있다.

```
>>> def my_function():
...     """Do nothing, but document it.
...
...     No, really, it doesn't do anything.
...     """
...     pass
...
>>> print(my_function.__doc__)
Do nothing, but document it.

    No, really, it doesn't do anything.
```

# 함수 주석 Function Annotations

함수를 선언 할 때 함수 인자와 결과값의 데이터 형식을 명시할 수 있다. 하지만, 이것은 필수도 아니고, 꼭 지켜야하는 것은 아니다. 즉, 프로그램 수행과는 무관하다. 하지만 프로그램을 읽으며 해석하는데 도움이 된다. 함수 주석 방법은 아래 예를 참조하자.

```
>>> def f(ham: str, eggs: str = 'eggs') -> str:
...     print("Annotations:", f.__annotations__)
...     print("Arguments:", ham, eggs)
...     return ham + ' and ' + eggs
...
>>> f('spam')
Annotations: {'ham': <class 'str'>, 'return': <class 'str'>, 'eggs': <class 'str'>}
Arguments: spam eggs
'spam and eggs'
```