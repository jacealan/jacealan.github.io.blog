---
layout: post
title:  "맥 새로 설치"
date:   2018-01-03 17:30:00 +0900
programming:   true
categories: programming
tags:   life mac
background-image: https://images.pexels.com/photos/39284/macbook-apple-imac-computer-39284.jpeg?w=1260&h=750&auto=compress&cs=tinysrgb
---
![iMac, MBP, iPad on Desk](https://images.pexels.com/photos/39284/macbook-apple-imac-computer-39284.jpeg?w=1260&h=750&auto=compress&cs=tinysrgb)
맥 새로 설치하려다 난리 중인지 거의 한달중이다. 2009 iMac, 2011 MBP... 참 오래된 사과들이다. 바꾸고 싶지만 잘돌아가는 덕에 1~2년에 한번 클린 설치를 한다. 그런데, 이번에 하이시에라(High Sierra)에서 파일시스템이 바뀌면서 완전 꼬였다.

설치 USB가 잘못됫는지, 기존 파일시스템으로 포맷이 안되서 APFS로 포맷 했는데, 갑자기 마우스가 먹통. 배터리 바꿔줘도 안된다. 결국, 다이소에서 TG 무선 마우스를 사고 말았다. 그리고도 계속 알수없는 ERROR!!! Sierra로 설치하려니 APFS를 인식못한다.ㅠㅠ 결국 Sierra 설치 USB 만들고 다시 설치. 그래도 매직마우스는 먹통.ㅠㅠ High Sierra로 다시 올렸다. 어차피 벌어진 일... MBP도 클린설치!

프로그래밍 때문에 iTerm2, Atom Editor를 사용해왔는데, 이상하게 iMac에서 이 둘을 설치하고 화면이 꺼지는 일이 계속 발생한게 클린설치 이유였다. 그런데, 클린설치 후에도 같은 증상.ㅠㅠ 결국, 바꾸기로 했다. macOS 자체 터미널을 iTerm2 설정 그대로 만들고, 에디터는 Visual Studio Code를 이용하기로. 이제 안꺼진다. iTerm2, Atom 중 무언가가 구형 iMac과 부딪히거나, 시스템부하 문제인 듯 한데... 이유는 모르겠고, 암튼 해결완료!

파이썬(Python3)를 패키징된 아나콘다(Anaconda)로 사용해왔다. 그런데 몇 가지 라이브러리, 모듈 등이 제대로 설치가 안되고 튕기기를 반복했다. 이것이 클린설치 두번째 이유. 그래서 이번에는 [Python.org](http://python.org)에서 다운받아 설치했다. 그런데, 이것도 비슷한 문제, 그리고 다른 문제가 생겼다. 해결방법 찾고 테스트하느라 또 몇일... 방법은 찾았는데, 기존 설치된 python3와 충돌 경고.

에잇! 다시 청소하자! 클린설치!

지금 iMac은 다시 한번 클린설치 중이다. MBP는 내일 출근해서 틈틈이 할 예정!