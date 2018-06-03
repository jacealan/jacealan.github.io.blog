---
layout: post
title:  "맥에서 MyEBook 실행방법"
date:   2018-01-21 17:30:00 +0900
programming:   true
categories: programming
tags:   programming app book ebook
background-image: /assets/2018-01-21.png
---
![image](/assets/2018-01-21.png)

맥용 MyEBook을 구매하신 분들 중 실행이 안되시는 분들을 위한 안내입니다. 현재 맥용 MyEBook은 터미널에서 실행해야 합니다. 마우스로 아이콘 클릭으로 실행시 csv 파일 저장이 안되는 경우가 있기때문입니다.

# 터미널 열기
**터미널**은 `응용 프로그램 > 유틸리티 > 터미널`에 있습니다. 실행하면 설정에 따라 조금 다를 수 있지만, 깜빡이는 터미널 화면이 보입니다.

# MyEBook 폴더에서 실행시키기
일단 다운받은 MyEBook 압축 파일을 푼 폴더(디렉토리)로 이동합니다. 맥의 기본 환경에서 다운로드하고 그대로 압축을 풀었다면(보통 자동으로 풀립니다), `cd 디렉토리` 입력으로 바로 이동합니다. 그리고 `ls`로 포함된 파일, 디렉토리를 확인합니다.

```shell
~ $ cd Downloads/MyEBook
~/Downloads/MyEBook $ ls
MyEBook      Python       chromedriver lib          myebook.gif
~/Downloads/MyEBook $ ./MyEBook
```

# 실행 모드 전환
위 방법으로 실행이 안된다면 파일 모드 변경을 합니다. `chmod u+x *`으로 파일 실행이 가능하도록 실행파일을 바꿉니다. 그리고 다시 `./MyEBook`으로 실행합니다.

```shell
~/Downloads/MyEBook $ chmod u+x *
```

![image](/assets/2018-01-07.png)