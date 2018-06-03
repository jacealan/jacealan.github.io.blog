---
layout: post
title:  "코딩 스타일 PEP8 - 파이썬 튜토리얼 따라가기 7"
date:   2018-02-02 17:30:00 +0900
programming:   true
categories: programming
tags:   programming app book ebook python
background-image: https://3.bp.blogspot.com/-nqoS4KnuSkc/WPjc59y66lI/AAAAAAAAAdU/JXq8qgKNjBYWwAXJWO8Bv_5R4Pp6bFDxgCLcB/s1600/pep8.jpg
---
![image](https://3.bp.blogspot.com/-nqoS4KnuSkc/WPjc59y66lI/AAAAAAAAAdU/JXq8qgKNjBYWwAXJWO8Bv_5R4Pp6bFDxgCLcB/s1600/pep8.jpg)
[Python.org](https://www.python.org)의 [The Python Tutorial](https://docs.python.org/3/tutorial/index.html)를 따라가며 설명한다.

# PEP8 (Python Enhancement Proposals 8)

PEP8은 프로그래밍한 코드를 읽기 쉽게, 보는 이가 편하게 만들기 위한 파이썬 코딩 스타일이다. 프로그래밍 언어들은 각각의 특징에 따라 다양한 코딩 스타일을 권장한다. 파이썬에서 가장 기본이 되는 코딩 스타일 PEP8은 다음과 같다.

## 들여쓰기는 공백 4칸

탭이 아니다. 좁은 들여쓰기는 타이핑이 편하고, 넓은 들여쓰기는 읽기 편하다. 중간 크기로 4칸이다.

## 한줄은 79를 넘지 않는다

80자 미만으로 줄의 길이를 제한하는 것은 작은 화면에서의 프로그래밍을 가능하게 한다. 또한 넓은 화면에서 여러 코드를 옆에 놓기도 편하다.

## 함수와 클래스의 위, 아래 빈 줄 넣기

함수와 클래스는 위,아래에 빈 줄을 두어서 구분한다.

## 코멘트는 한줄로

가능하면 코멘트는 한줄로 한다.

## DocStrings 사용

설명문 Documentaion Strings를 이용한다.

## a = f(1, 2) + g(3, 4)

연산자의 앞, 뒤는 공백을 둔다. 콤마(,)는 뒤쪽에 공백을 둔다. 괄호 안 내용은 붙여 쓴다.

## CamelCase, lower_case_with_underscores

클래스 이름은 카멜 케이스 형식으로 만든다. 공백없고, 단어 첫글자는 대문자로. 함수 이름은 소문자를 언더바(_)로 연결해서 이용한다. 클래스의 첫 메쏘드의 인자는 `self`를 이용한다.

## UTF-8

파이썬의 기본 인코딩은 UTF-8이다. 다른 인코딩은 사용하지 않는다. 바꿔야 한다면 ASCII가 차선책이다.

## ASCII 문자

프로그래밍에 ASCII 문자만 이용한다. 그래야 언제, 어디서나, 누구와도 소통이 가능하다. 코멘트, 주석, 설명문 등도 ASCII로 즉, 영어로 작성하면 좋겠지만, 이 부분에서는 한글을 쓰는게 더 읽기 쉽고 편하다.(한국에서는)

 # Reference

 <https://www.python.org/dev/peps/pep-0008/> Style Guide for Python Code