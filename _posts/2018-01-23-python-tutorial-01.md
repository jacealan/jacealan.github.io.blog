---
layout: post
title:  "소스 코드 인코딩 Encoding, 수와 연산 Numbers - 파이썬 튜토리얼 따라가기 1"
date:   2018-01-23 17:30:00 +0900
programming:   true
categories: programming
tags:   programming app book ebook python
background-image: http://quantlabs.net/blog/wp-content/uploads/2015/11/pythonlogo.jpg
---
![image](http://www.msbiblog.com/wp-content/uploads/2016/09/Python_logo.png)
[Python.org](https://www.python.org)의 [The Python Tutorial](https://docs.python.org/3/tutorial/index.html)를 따라가며 설명한다.

# 소스 코드 인코딩 안내

소스 코드의 인코딩 안내가 없으면 개발 환경에 따라 소스 코드를 제대로 해석하지 못하는 경우가 있다. Mac, Unix, Linux 등은 이제 utf-8이 기본 인코딩이어서 필수 요소는 아니다. 하지만 앞의 환경에서 작성한 소스 코드를 Windows에서 읽으면 에러가 발생하기 쉽다. 파이썬은 소스 코드의 맨 앞에 소스 코드 자체의 인코딩을 안내해두는 것이 좋다.

```
# -*- coding: encoding -*-
```

encoding 부분에 인코딩 환경을 적는다. 예를 들면 다음과 같다.

```
# -*- coding: utf-8 -*-
```

# 코멘트는 \#으로 시작

소스 코드를 작성하면서 코멘트를 잘 기록해야 가독성과 이해도 그리고 차후 수정이 쉽다. 코멘트는 프로그램의 실행과는 전혀 상관없다. `#`뒤에는 무엇이든 써도 된다. 단, 문자(열)을 표시하는 (작은)따옴표 `\``, `"` 쌍 사이의 `#`는 코멘트로서 무의미한 글자 `#`이다.

```
# 첫번째 코멘트
spam = 1  # 두번째 코멘트
          # 세번째 코멘트
text = "따옴표 사이의 #는 코멘트 표시가 아닌 글자 #이다."
```

# 연산(계산)

수 연산, 식 연산은 파이썬 인터액티브 모드(Interactive Mode)로 설명한다. 수식 연산은 수학의 연산 법칙, 연산 순서를 그대로 따른다. 띄어쓰기는 연산과 무관하다. 인터액티브 모드는 터미널에서 `python' 또는 'python3'로 들어간다.

![image](/assets/2018-01-23-python-tutorial-01.png)

```
>>> 2 + 2
4
>>> 50 - 5 * 6
20
```

나누기 연산 결과는 소수로 표현된다. `//`는 나누기 연산 결과에 가우스값`[]`을 나타낸다. 즉, 결과값보다 크지 않은 정수이다. `%`는 나머지값이다.

```
>>> (50 - 5 * 6) / 4
5.0
>>> 8 / 5  # 나누기 연산 결과는 소수
1.6
>>> 17 / 3
5.666666666666667
>>>
>>> 17 // 3  # //는 나눈 값보다 크지 않은 정수
5
>>> 17 % 3  # 나머지
2
```

`**`는 제곲이다.
```
>>> 5 ** 2  # 5의 제곱
25
>>> 2 ** 7  # 2의 7제곱
128
```

`=`는 우측의 결과값으로 좌측 변수를 선언한다. 선언된 변수는 수학 수식의 x, y 등처럼 이용할 수 있다. 선언되지 않은 변수는 이용할 수 없다.

```
>>> width = 20
>>> height = 5 * 9
>>> width * height
900
>>> n  # 선언되지 않은 변수
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'n' is not defined
```

파이썬 인터액티브 모드에서 `_`(언더바)는 바로 전 결과값이다.

```
>>> tax = 12.5 / 100
>>> price = 100.50
>>> price * tax
12.5625
>>> price + _ # _는 12.5625
113.0625
>>> round(_, 2) # _는 113.0625
113.06
```