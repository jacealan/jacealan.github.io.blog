---
layout: post
title:  "자료형 Data Structures 2 - 파이썬 튜토리얼 따라가기 9"
date:   2018-02-07 17:30:00 +0900
programming:   true
categories: programming
tags:   programming app book ebook python
background-image: http://quantlabs.net/blog/wp-content/uploads/2015/11/pythonlogo.jpg
---
![image](http://www.msbiblog.com/wp-content/uploads/2016/09/Python_logo.png)
[Python.org](https://www.python.org)의 [The Python Tutorial](https://docs.python.org/3/tutorial/index.html)를 따라가며 설명한다.

## 튜플 Tuple `()`

순서(인덱스)가 있는 데이터 모음으로 튜플이 있다. 튜플은 리스트와 같다. 다만, 차이점은 항목을 변경할 수 없다. 즉, 변수와 상수의 차이와 같다. 튜플의 선언은 항목들을 콤마(,)로 열거하면 된다.

{% highlight python linenos %}
>>> t = 12345, 54321, 'hello!'
>>> t[0]
12345
>>> t
(12345, 54321, 'hello!')
>>> # Tuples may be nested:
... u = t, (1, 2, 3, 4, 5)
>>> u
((12345, 54321, 'hello!'), (1, 2, 3, 4, 5))
>>> # Tuples are immutable:
... t[0] = 88888
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment
>>> # but they can contain mutable objects:
... v = ([1, 2, 3], [3, 2, 1])
>>> v
([1, 2, 3], [3, 2, 1])
{% endhighlight %}

빈 리스트처럼, 빈 튜플도 가능하다. 빈 튜플은 `()`이다. 항목이 하나인 튜플은 뒤에 콤마(,)를 붙여서 선언한다. 콤마가 없으면 변수이다.

{% highlight python linenos %}
>>> empty = ()
>>> singleton = 'hello',    # <-- note trailing comma
>>> len(empty)
0
>>> len(singleton)
1
>>> singleton
('hello',)
{% endhighlight %}

리스트와 마찬가지로 역선언도 가능하다.

{% highlight python linenos %}
>>> x, y, z = t
{% endhighlight %}

## 집합 Sets `{}`

집합은 데이터 모음으로 순서가 없다. 수학에서의 집합과 같다. 그리고, 집합에는 같은 값이 중복되지 않는다. 같은 값은 하나만 남는다.

집합은 수학의 집합처럼 차집합 `-`, 합집합 `|`,  교집합 `&`이 가능하다. 두 집합 사이에 한쪽에만 속하는 원소를 연산하는 `^` 연산자도 있다.

{% highlight python linenos %}
>>> basket = {'apple', 'orange', 'apple', 'pear', 'orange', 'banana'}
>>> print(basket)                      # show that duplicates have been removed
{'orange', 'banana', 'pear', 'apple'}
>>> 'orange' in basket                 # fast membership testing
True
>>> 'crabgrass' in basket
False

>>> # Demonstrate set operations on unique letters from two words
...
>>> a = set('abracadabra')
>>> b = set('alacazam')
>>> a                                  # unique letters in a
{'a', 'r', 'b', 'c', 'd'}
>>> a - b                              # letters in a but not in b
{'r', 'd', 'b'}
>>> a | b                              # letters in a or b or both
{'a', 'c', 'r', 'd', 'b', 'm', 'z', 'l'}
>>> a & b                              # letters in both a and b
{'a', 'c'}
>>> a ^ b                              # letters in a or b but not both
{'r', 'd', 'b', 'm', 'z', 'l'}
{% endhighlight %}

집합도 리스트 컴프레힌션이 가능하다.

{% highlight python linenos %}
>>> a = {x for x in 'abracadabra' if x not in 'abc'}
>>> a
{'r', 'd'}
{% endhighlight %}

## 사전 Dictionaries `{}`

리스트, 문자열, 튜플 같은 순서가 있는 데이터 모음은 순서 인덱싱과 값을 연동한다. 사전은 순서가 없다. 사전은 변경 불가능한 key와 값을 연동한다. 따라서 리스트에서 사용하는 인덱싱 숫자 대신 key를 사용한다. key와 값은 `:`으로 연결한다. 사전의 key 확인은 keys() 메쏘드를 이용한다.

{% highlight python linenos %}
>>> tel = {'jack': 4098, 'sape': 4139}
>>> tel['guido'] = 4127
>>> tel
{'sape': 4139, 'guido': 4127, 'jack': 4098}
>>> tel['jack']
4098
>>> del tel['sape']
>>> tel['irv'] = 4127
>>> tel
{'guido': 4127, 'irv': 4127, 'jack': 4098}
>>> list(tel.keys())
['irv', 'guido', 'jack']
>>> sorted(tel.keys())
['guido', 'irv', 'jack']
>>> 'guido' in tel
True
>>> 'jack' not in tel
False
{% endhighlight %}

사전을 선언하는 다양한 방법은 다음을 참조한다. 사전 자료도 리스트 컴프레힌션이 가능하다.

{% highlight python linenos %}
>>> dict([('sape', 4139), ('guido', 4127), ('jack', 4098)])
{'sape': 4139, 'jack': 4098, 'guido': 4127}
>>> {x: x**2 for x in (2, 4, 6)}
{2: 4, 4: 16, 6: 36}
>>> dict(sape=4139, guido=4127, jack=4098)
{'sape': 4139, 'jack': 4098, 'guido': 4127}
{% endhighlight %}

## 루프 방법 Looping Techniques

### 사전 루프 Dictionaries Looping Techniques

{% highlight python linenos %}
>>> knights = {'gallahad': 'the pure', 'robin': 'the brave'}
>>> for k, v in knights.items():
...     print(k, v)
...
gallahad the pure
robin the brave
{% endhighlight %}

### 순서 자료 루프 Sequence Looping Techniques

enumerate()는 순서자료형의 인덱스를 이용하는 방법 중 하나이다.

{% highlight python linenos %}
>>> for i, v in enumerate(['tic', 'tac', 'toe']):
...     print(i, v)
...
0 tic
1 tac
2 toe
{% endhighlight %}

### 한번에 두 자료 루프 zip()

zip() 을 이용해서 하나의 루프에 여러 개의 리스트를 동시에 적용할 수 있다.

{% highlight python linenos %}
>>> questions = ['name', 'quest', 'favorite color']
>>> answers = ['lancelot', 'the holy grail', 'blue']
>>> for q, a in zip(questions, answers):
...     print('What is your {0}?  It is {1}.'.format(q, a))
...
What is your name?  It is lancelot.
What is your quest?  It is the holy grail.
What is your favorite color?  It is blue.
{% endhighlight %}

### 순서 뒤집기 reversed()

{% highlight python linenos %}
>>> for i in reversed(range(1, 10, 2)):
...     print(i)
...
9
7
5
3
1
{% endhighlight %}

### 순서 정렬 sorted()

 sort() 메쏘드와 같은 기능을 하는 함수로, sorted()는 정렬된 자료를 반환한다.
 
{% highlight python linenos %}
>>> basket = ['apple', 'orange', 'apple', 'pear', 'orange', 'banana']
>>> for f in sorted(set(basket)):
...     print(f)
...
apple
banana
orange
pear
{% endhighlight %}