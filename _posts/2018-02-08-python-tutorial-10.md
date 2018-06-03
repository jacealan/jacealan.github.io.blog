---
layout: post
title:  "비교, 조건 - 파이썬 튜토리얼 따라가기 10"
date:   2018-02-08 17:30:00 +0900
programming:   true
categories: programming
tags:   programming app book ebook python
background-image: http://quantlabs.net/blog/wp-content/uploads/2015/11/pythonlogo.jpg
---
![image](http://www.msbiblog.com/wp-content/uploads/2016/09/Python_logo.png)
[Python.org](https://www.python.org)의 [The Python Tutorial](https://docs.python.org/3/tutorial/index.html)를 따라가며 설명한다.

## 비교, 조건

while, if 등의 조건문에는 단순 비교 뿐만 아니라 복잡한 복합 비교도 가능하다.

### in, not in, is, is not

리스트나 튜플 등의 나열 자료에 데이터가 들어있는지 안들어있는지를 비교할 때는 `in`, `not in`을 사용한다. `is`는 `=`와 같다. `is not`은 `!=`와 같다. 이 연사자는 +, * 등과 같은 산술 연산자보다 나중에 연산한다.

### 복합 비교 a < b < c

파이썬은 복합 비교 형식이 가능하다.

### 비교 조건을 연결할 때 and, or, not

비교 조건들을 and, or, not으로 연계할 수 있다. 이들 연산자 사이에도 순서가 있다. not이 최우선, or가 최후선이다.

`A and not B or C`는 `(A and (not B)) or C`와 같다.

and, or 와 같은 연산자 는 기본적으로 좌에서 우로 연산이 흐른다.

{% highlight python linenos %}
>>> string1, string2, string3 = '', 'Trondheim', 'Hammer Dance'
>>> non_null = string1 or string2 or string3
>>> non_null
'Trondheim'
{% endhighlight %}

## 복합 비교

파이썬은 복잡한 비교가 가능하다. 다음을 참조한다.

{% highlight python linenos %}
(1, 2, 3)              < (1, 2, 4)
[1, 2, 3]              < [1, 2, 4]
'ABC' < 'C' < 'Pascal' < 'Python'
(1, 2, 3, 4)           < (1, 2, 4)
(1, 2)                 < (1, 2, -1)
(1, 2, 3)             == (1.0, 2.0, 3.0)
(1, 2, ('aa', 'ab'))   < (1, 2, ('abc', 'a'), 4)
{% endhighlight %}