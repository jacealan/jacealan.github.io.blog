---
layout: post
title:  "맥 터미널(Terminal) 설정"
date:   2018-01-05 17:30:00 +0900
programming:   true
categories: programming
tags:   mac programming
background-image: https://gist.githubusercontent.com/agnoster/3712874/raw/screenshot.png
---
# 폰트 추가 : Powerline Fonts
맥을 설치하고 제일 먼저 하는 것은 폰트 추가다. 대부분의 폰트가 프로그래밍용으로는 불편하다. 이유는 가변폭과 혼동되는 글자때문이다. 대표적인 것이 영어 L 소문자와 숫자 1이다. 이를 구분할 수 있어야 편하다. 그리고, 터미널 설정을 할 때 프롬프트를 편하게 사용하기 위해 powerline 패치된 폰트가 필요하다. 터미널에서 아래 같은 화면이 가능하다.

![normal](https://camo.githubusercontent.com/3c3a1717e42f17651f688ecc19f87e7433275098/68747470733a2f2f7261772e6769746875622e636f6d2f706f7765726c696e652f706f7765726c696e652f646576656c6f702f646f63732f736f757263652f5f7374617469632f696d672f706c2d6d6f64652d6e6f726d616c2e706e67)
![insert](https://camo.githubusercontent.com/627cc0d6ca618d9480dfbeeaf1f35ca0cc30781b/68747470733a2f2f7261772e6769746875622e636f6d2f706f7765726c696e652f706f7765726c696e652f646576656c6f702f646f63732f736f757263652f5f7374617469632f696d672f706c2d6d6f64652d696e736572742e706e67)
![visual](https://camo.githubusercontent.com/4a4454311274d16299aef08227496c5d1a7a9fd5/68747470733a2f2f7261772e6769746875622e636f6d2f706f7765726c696e652f706f7765726c696e652f646576656c6f702f646f63732f736f757263652f5f7374617469632f696d672f706c2d6d6f64652d76697375616c2e706e67)
![replace](https://camo.githubusercontent.com/28430e34155892705de259c0e5fb0eec63825856/68747470733a2f2f7261772e6769746875622e636f6d2f706f7765726c696e652f706f7765726c696e652f646576656c6f702f646f63732f736f757263652f5f7374617469632f696d672f706c2d6d6f64652d7265706c6163652e706e67)

파워라인 폰트를 모아놓은 [GitHub - powerline/fonts: Patched fonts for Powerline users.](https://github.com/powerline/fonts)에서 다운받고 설치하면 된다. 필요한 폴트만 설치해도 된다..

모두 설치하는 것은 간단하다.

![image](/assets/2018-01-05-terminal-setup-01.png)

다운로드 하고 압출을 풀면(맥에선 다운로드 폴더 밑에 압출을 풀어서 폴더에 넣어둔다) 해당 디렉토리에서 설치 스크립트`install.sh`를 실행하면 된다.

![image](/assets/2018-01-05-terminal-setup-02.png)

프로그래밍과 관련된 앱은 모두 **Ubuntu Mono derivative Powerline** 를 이용하고 있다. 구글의  **Source Code Pro for Powerline**도 좋은데 자간이 좀 넓다. 터미널 설정은 프로파일 설정부터 하고 폰트 설정을 한다. 폰트 설정을 미리 하면, 프로파일 설정 후 다시 해야한다.

![image](/assets/2018-01-05-terminal-setup-03.png)

# 프로파일 설정
터미널의 프로파일은 앱테마라고 생각하면 된다.  아래 같은 디자인으로 터미널을 사용하기 위해서 해당 테마를 설정해야한다.

![image](https://raw.githubusercontent.com/robinbentley/oceanic-next-macos-terminal/master/ss-colors.png)![image](https://raw.githubusercontent.com/robinbentley/oceanic-next-macos-terminal/master/ss-terminal.png)

## Oceanic Next theme for macOS Terminal
[GitHub - robinbentley/oceanic-next-macos-terminal: Port of the Oceanic Next theme for macOS terminal](https://github.com/robinbentley/oceanic-next-macos-terminal)
이번에도 GitHub에서 다운로드 전체 다운로드 한다.
![image](/assets/2018-01-05-terminal-setup-04.png)

## 프로파일에 외부 테마 추가하기
터미널 환경설정에서 프로파일 탭의 왼쪽에 프로파일 목록이 보인다.  아래쪽에 톱니바퀴에서 가져오기를 선택한다. 그리고 다운로드한 것 중 **oceanic-next.terminal**을 선택한다. 그러면 목록 중에 **oceanic-next**가 보인다.  더블 클릭하면 oceanic-next 프로파일이 적용된 터미널이 뜬다. 이제 이 프로파일을 기본으로 하자. 톱니바퀴 옆에 기본 클릭! 이제 oceanic-next에 기본이라고 표시된다.
![image](/assets/2018-01-05-terminal-setup-05.png)
![image](/assets/2018-01-05-terminal-setup-06.png)

# 폰트 설정
터미널 환경설정 오른쪽 중간 정도에 서체가 보인다. 변경을 클릭하면 폰트 선택 창이 열린다. 앞에서 설치한 **Ubuntu Mono derivative Powerline**를 선택하고 폰트크기는 14로. 폰트, 글자 크기는 각자 취향대로 선택한다. 선택해도 아무런 변화가 없다.
![image](/assets/2018-01-05-terminal-setup-07.png)

새 창을 열면 아래 같은 터미널이 열린다.
![image](/assets/2018-01-05-terminal-setup-08.png)