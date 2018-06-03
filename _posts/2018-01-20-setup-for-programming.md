---
layout: post
title:  "프로그래밍 환경, 제이스의 맥북"
date:   2018-01-20 17:30:00 +0900
programming:   true
categories: programming
tags:   life mac programming
background-image: https://static.pexels.com/photos/374074/pexels-photo-374074.jpeg
---
![image](https://static.pexels.com/photos/374074/pexels-photo-374074.jpeg)

맥이든 PC든 하는 것은 크게 두가지로 구분할 수 있다. 컨텐츠 소비와 생산. 컨텐츠 소비를 위한 환경은 다들 비슷하고 특별한 것은 없다. 컨텐츠를 만들 때는 자신의 취향 영향이 크다. 나도 마찬가지. PC에서 맥으로 바꿀 때도 그런 이유였다. 현재 내가 프로그래밍하는 환경의 가장 기본이 되는 터미널([맥 터미널 설정](/2018-01-05-terminal-setup.html))과 쉘([Z Shell 설치, 그리고 설정](/2018-01-09-zshell.html))은 이미 포스팅 완료. 남은 것들은 한번에 정리한다.

# 깃(Git) 설치
<a href='https://git-scm.com'><img src='https://git-scm.com/images/logo@2x.png' align='left' style='max-width:100; padding-right:10;'></a>
맥에 Git은 기본 설치되있다. 지금 High Sierra를 설치하고나면 2.14.3 버전의 Git이 기본 설치되어 있다. 그냥 써도 되고, 최신 버전으로 업데이트 하려면 Homebrew로 설치하면 된다. [https://git-scm.com](https://git-scm.com)에서 다운로드해서 설치도 가능하다.

```
$ brew install git
```

설치하고 바로 다시 버전을 확인하면 구 버전으로 나온다. 터미널을 새로 열고 확인하면 새버전을 확인할 수 있다.

# 파이썬(Python3) 설치
<a href='https://www.python.org'><img src='https://c1.staticflickr.com/9/8123/8679381967_75cee4e0e9_z.jpg' align='left' style='max-width:100; padding-right:10;'></a>
맥의 기본 파이썬은 2.7.10이다. Python2와 Python3는 호환이 되지 않는다. 문법도 꽤 차이가 난다. 몇년 사이 대부분의 개발자가 Python3를 기본으로 하고 있다. 고민하지 말고, Python3를 설치한다. 설치는 역시 Homebrew로 설치한다. 왜 Python이냐고? 쉽고 편하니까!

```
$ brew install python3
```

# 가상환경(virtualenv) 설치
Python3를 설치하고 나면 기본적으로 맥에는 Python2, Python3가 모두 설치되어 있다. 그런데 이렇게 버전이 섞이면 프로그래밍이 어렵다. 개발 프로젝트 진행시, 추가 설치하는 Module, Library 등의 버전까지도 신경써야 하는 상황이 생기기에, 가상환경을 이용한다. 가상환경을 이용하는 이유야 여러가지겠지만, 편리성, 관리성이 첫번째 이유다. 설치는 파이썬 패키지 관리자인 PIP를 이용한다.

```
$ pip3 install virtualenv
```

## 가상환경 디렉토리 만들기

가상환경별로 디렉토리를 만드는데, 위치는 어디에도 상관없다. 하지만 관리를 고려하면 두가지가 대표적이다. 프로젝트 별로 프로젝트의 루트에 가상환경 디렉토리를 만든다. 또는 사용자의 홈디렉토리에 가상환경을 모아놓을 디렉토리를 만든다. 현재 내 방식은 기본적으론 후자이다. 크게 몇가지 환경이면 대부분 가능한 상황이기 때문이다. 특별한 프로젝트의 경우는 해당 프로젝트 루트에 생성한다.

```
$ mkdir .venv
$ cd .venv
$ python3 -m venv myvenv(가상환경이름) # 가상환경 만들기
$ source  myvenv/bin/activace	 # 가상환경 시작
$ deactivate # 가상환경 끝
```

Python2를 사용하면 virtualenv를 설치해야한다. Python3에는 venv가 포함되어 있다. 기본 포함된 venv와 virtualenv 중 선택하면 된다.

# 에디터 Visual Studio Code 설치
기존에 Atom을 이용했다. [Atom:A hackable text editor for the 21st Century](https://atom.io)가 Visual Studio Code보다 좀 더 무거워서 구형 iMac이 버거워한다. 이제는 Visual Studio Code가 더 익숙하다.

## Visual Studio Code 다운로드 및 설치
<a href='https://code.visualstudio.com'><img src='https://upload.wikimedia.org/wikipedia/commons/thumb/2/2d/Visual_Studio_Code_1.18_icon.svg/2000px-Visual_Studio_Code_1.18_icon.svg.png' align='left' style='max-width:100; padding-right:10;'></a>

[Visual Studio Code - Code Editing. Redefined](https://code.visualstudio.com)에서 다운로드하고 설치하고 실행하면 다음화면을 볼 수 있다.
![image](/assets/2018-01-20-vsc-01.png)

## Extensions : Python 설치

몇가지 확장앱을 설치하고 테스트 중이다. 일단 [Python - Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-python.python)는 기본적으로 설치한다. 그리고 **Predawn Theme Kit**, **file-icons**까지 기본설치한다. 
![image](https://raw.githubusercontent.com/microsoft/vscode-python/master/images/general.gif)

## 터미널에서 실행가능하게 만들기
`<command+shift+p>`를 누르고 **shell command:install ‘code’ command in path**를 입력하면 아래 화면을 볼 수 있다.  클릭하면 설치한다.
![image](/assets/2018-01-20-vsc-02.png)

## Visual Studio Code 설정
설정을 열면 아래처럼 보인다. 수정할 부분에 마우스 포인터를 가져가면 왼쪽에 연필 아이콘이 나타난다. 클릭하면 설정에 복사 버튼이 나타난다. 클릭하면 오른편 사용자 설정에 해당 설정을 Copy & Paste한다. 원하는 값으로 수정한다.
![image](/assets/2018-01-20-vsc-03.png)

아래는 내 설정이다.
```json
{
    // 글꼴 크기(픽셀)를 제어합니다.
    "editor.fontSize": 14,
    // 글꼴 패밀리를 제어합니다.
    "editor.fontFamily": "Ubuntu Mono derivative Powerline, Menlo, Monaco, 'Courier New', monospace",
    // 파일 저장 시 서식을 지정합니다. 포맷터를 사용할 수 있어야 하며, 파일이 자동으로 저장되지 않아야 하고, 편집기가 종료되지 않아야 합니다.
    "editor.formatOnSave": true,
    // 터미널의 글꼴 크기(픽셀)를 제어합니다.
    "terminal.integrated.fontSize": 14,
    // 터미널이 OS X에서 사용하는 셸의 경로입니다.
    "terminal.integrated.shell.osx": "/usr/local/bin/zsh",
    // Specifies the color theme used in the workbench.
    "workbench.colorTheme": "Predawn",
    // Path to folder with a list of Virtual Environments (e.g. ~/.pyenv, ~/Envs, ~/.virtualenvs).
    "python.venvPath": ".venv",
    // Whether to lint Python files using flake8
    "python.linting.flake8Enabled": true,
    // 창의 확대/축소 수준을 조정합니다. 원래 크기는 0이고 각 상한 증분(예: 1) 또는 하한 증분(예: -1)은 20% 더 크거나 더 작게 확대/축소하는 것을 나타냅니다. 10진수를 입력하여 확대/축소 수준을 세부적으로 조정할 수도 있습니다.
    "window.zoomLevel": 1,
}
```
