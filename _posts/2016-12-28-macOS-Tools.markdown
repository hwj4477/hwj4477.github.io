---
layout:     post
title:      macOS Tools
author:     wjhong
tags:    	macOS tool
subtitle:   macOS 개발 관련 툴 소개
category:   Tool
---

# macOS, iMac
개발자로 일을 시작 하면서 부터 계속 맥을 써왔다. <br />
개인적으로 윈도우 응용 프로그램 개발을 위해서가 아니라면 개발자는 무조건 맥을 쓰는게 좋다고 생각한다.(개인적인 생각입니다. 오해 없길..) <br />
유닉스 계열의 OS 와도 친해질 수 있고, 개발을 위한 환경이 기본적으로 준비되어 있다.<br />
또, HomeBrew(패키지 매니저)를 활용해서 개인에게 맞는 개발 환경을 준비해서 새로운 맥에서도 편하게 설정할 수 있다.<br />
개발에 필요한 다양한 App들도 큰 장점이다.

이번에는 macOS 에서 사용할 만한 App(Tool)들을 포스팅 하고자 한다.<br />
이후에 HomeBrew에 대해서도 포스팅 할 생각이다.<br />

여담이지만, Sierra 버전이 나오면서 OS X 에서 macOS로 이름이 바뀌었다.<br />
(덕분에 OS 엑스 라고 읽는 부끄러운 일이 없어질 것 같다......)


# [Sip](https://itunes.apple.com/kr/app/sip/id507257563?mt=12)
![Sip]({{ site.url }}/img/post/tools/sip.jpg)<br />

ColorPicker? 라고 생각하면 된다. 스크린상의 원하는 색상값을 클릭하면 해당 색상값을 클립보드에 복사 해준다.<br />
단순한 기능이지만 매우 편리하다. Android, CGColor, CSS, Java, .Net, Swift, OpenGL... 등의 다양한 형태의 포멧 설정이 가능하다.

필자의 경우 모바일 App 개발 업무를 주로 하는데, 친절히 색상값을 알려주는 디자이너가 없는 상황에 매우 유용하다.<br />
단지 색상값을 찍어보기 위해 무거운 포토샵을 실행할 순 없으니.....

Pro 버전도 있어서 추가적인 기능을 제공하는 듯 한데, 아직 Pro 버전까지는 사용해보지 않았다.<br />
그냥 색상값만 찍어봐도 충분하다.


# [CocoaRestClient](http://mmattozzi.github.io/cocoa-rest-client/)
![CocoaRestClient]({{ site.url }}/img/post/tools/cocoarest.jpg)<br />

HTTP 요청을 테스트해볼 수 있는 클라이언트이다.<br />
이름 처럼 RESTful API를 테스트해볼 수 있도록 메소드 지정이 가능하다.<br />
오픈 소스로 왕성하게 업데이트 중인지는 확실히 모르겠지만, 충분한 기능을 가지고 있다.<br />

개인적으로는 Swagger UI 페이지가 더 편하긴 한거 같다. 그래도 자주는 아니어도 가끔 사용하게 된다.


# [Sequel Pro](https://www.sequelpro.com/)
![Sequel Pro]({{ site.url }}/img/post/tools/sequelpro.jpg)<br />

MySQL 관리 툴이다.<br />
원격으로 DB 서버에 접속해서 데이터베이스를 관리할 수 있다.<br />

아무래도 관계형 데이터베이스랑 매우 친한편은 아니다 보니, 관리해야 할 일이 생기면 툴에 조금 의존하게 되곤 한다.<br />
다른 데이터베이스 관리 툴처럼 쿼리 테스트도 가능하다.

원격 접속 서버 리스트를 편집할 수 있다.<br />
혹시 여러개의 DB 서버를 관리해야 한다면, 더욱 유용할 것 같다.


# [SQLPro for SQLite](https://itunes.apple.com/kr/app/sqlpro-for-sqlite-read-only/id635299994?mt=12)
![SQLPro for SQLite]({{ site.url }}/img/post/tools/sqlpro.jpg)<br />

이번엔 SQLite 관리 툴이다.<br />
매우 심플하게 필요한 기능들을 제공한다.

대부분 데이터 확인 용도로 사용하게 되긴 하지만, 쿼리 테스트도 가능하고 CSV Import/Export 기능도 제공한다.<br />
무료 버전에서는 읽기만 가능하나, 필자의 경우 한시적 무료일때 구매해서 사용중이다.<br />

데이터 확인 용으로 사용하다가, 맘에 든다면 그때 구매하길 추천한다.<br />

무료를 원한다면 오픈소스인 [Sqlitebrowser](http://sqlitebrowser.org/)도 있다.<br />
그러나, 개인적으론 UI 도 깔끔하고 해서 'SQLPro for SQLite'를 추천한다.


# [HotKey App](https://itunes.apple.com/kr/app/hotkey-app/id975890633?mt=12)
![HotKey App]({{ site.url }}/img/post/tools/hotkeyapp.jpg)<br />

개발용 툴이라고 하기엔 조금 다른 App이다. 단축키 사용을 도와주는 유틸이다.<br />
개인적으로 마우스 사용을 좋아하지 않기 때문에, 단축키를 최대한 사용하려고 하는 편이다.<br />
물론, Xcode 스토리보드 편집 하는 경우와 같을땐 많이 사용하긴 한다. 트랙패드 쓰긴 하지만...<br />

단축키를 사용하지 않고 마우스를 통해 특정 기능을 사용하면 화면 우측 상단에 알림을 통해서 단축키를 알려 준다.<br />
해당 기능을 사용하면 알려주는 방식이기 때문에, 알림을 자주본다면 자주사용하는 메뉴이기 때문에 자연스럽게 단축키를 외우게 된다.<br />

개발자, 또는 맥을 처음 접하는 사용자에게 강력 추천해주고 싶은 App이다.
