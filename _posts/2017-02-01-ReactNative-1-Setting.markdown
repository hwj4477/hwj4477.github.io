---
layout:     post
title:      React Native - 1
author:     wjhong
tags:    	ReactNative React
subtitle:   React Native - 소개, 환경 설정
category:   ReactNative
---

# 서론
지금도 그렇지만, 2010년도 초중반 한참 하이브리드 앱에 대한 관심과 수요가 많았던 기억이 난다.<br />
여기서 말하는 하이브리드 앱이란, 네이티브 앱의 웹뷰를 통해서 웹앱(웹사이트)의 기능을 제공하는 앱이다.<br />

불과 몇년 전이긴 하지만, 상대적으로 지금보다는 모바일 앱에 대한 이해와 중요도가 상대적으로 낮았던 시기이다 보니 그만큼 개발자도 많지 않았고, 모바일 앱 개발을 위해서는 웹앱 개발에 비해 상대적으로 높은 비용이 필요했다.<br />
또한, 하이브리드 앱의 경우 즉각적으로 해당 웹앱의 변경 내용을 반영할 수 있다는 장점 때문에 네이티브 앱에 비해 유연한 장점을 가지고 있었다.<br />

필자의 경우 이 시기에 iOS/Android 네이티브 앱 개발 업무를 하고 있었다. 위에 언급한 분위기와 궁금증 때문에 하이브리드 앱에 대해 관심을 가지게 되었다.<br />
그래서 폰갭 + 센차터치를 활용한 간단한 프로젝트 진행을 위해, 지인과 함께 개인적인 스터디 활동을 한 적이 있다.<br />

결과적으로는 만족스럽진 못했다. html, javascript, css 등에 익숙한 웹 개발자의 경우라면 다를 수 있겠지만, 비용 대비 결과물이 실망스러웠다.<br />
이럴거면 둘다 따로 만들지......  라는 생각과 함께 과감히 마음을 돌렸던 기억이 있다.<br />

그렇지만, 현재도 모바일 웹으로 퍼블리싱 된 페이지를 통해 웹뷰와 연동하는 작업은 아주 빈번하게 하고있다.<br />
운영 및 비용, 소스 관리 측면에서 iOS/Android  양쪽을 관리한다는건 부담이 되는게 사실이다.<br />
이런 이슈 들로 인해, 멀티플랫폼을 지원하는 모바일 앱 개발 방법에 관한 고민들은 앞으로도 계속 이루어 질거라고 생각한다.<br />

서론이 길었지만, 이러한 이유로 요즘 그중에 많은 관심을 받고 있는 React Native 에 대해 테스트, 학습 해보려고 한다.<br />

개인적으론 아직도 네이티브 앱 개발이 좋다고 생각하는 편이다.<br />
그러나 앞으로 방향이 어떻게 변할지 모르기 때문에 굳이 고집하고 싶지는 않다.<br />
'React Native' 많은 관심을 받고 있는 만큼, 그럴만한 이유가 있을거라 생각한다.<br />


<br />

# React?, React Native
React는 Facebook에서 만들고 있는 뷰(MVC 에서의 View)에 해당하는 부분을 컴포넌트로 만들기 위한 라이브러리이다.<br />

특징으로는 Virtual DOM 이라는 구조체를 가지고 있으며, 해당 구조체의 전후 상태를 비교하여 변경이 필요한 최소한의 요소만 반영한다. (성능상의 이점)<br />
또, JSX(Javasctipy + XML) 라는 확장 마크업 언어를 통해 자바스크립트 코드 안에 XML 스타일의 구문을 작성할 수 있다.<br />

React Native는 위에서 설명한 React의 UI 작성 접근 방법을 모바일로 확장하는 라이브러리이다.<br />
기존의 웹앱(하이브리드앱)에서와 다르게 웹뷰를 통한 인터페이스 구축이 아닌, 네이티브 위젯으로 인터페이스를 구현하는 방식이다. (직접 확인해보진 못했다.) <br />
<br />

# React Native 환경 설정
macOS 환경 기준으로 작성하였다. 어차피 iOS 빌드 및 배포를 위해 Xcode 가 필요하기 때문에 맥은 필수가 아닐까 싶다.<br />
<br />

## 설치
앞서 [Homebrew](http://brew.sh/index_ko.html) 설치가 필요하다.<br />
React Native 문서에서도 Homebrew를 통한 설치를 안내하고 있다.<br />
물론, Xcode 설치도 필요하다.<br />

``` shell
brew install node
brew install watchman
```

위 명령어를 통해 node, watchman 을 설치 한다.<br />
watchman은 파일 변경 추적을 위한 툴이다.<br />

``` shell
npm install -g react-native-cli
```

React Native Command line Interface 설치도 이어서 진행해 준다.<br />
Xcode 설치까지 끝마쳤다면, React Native를 위한 기본 설치는 끝이다.<br />
<br />

## 프로젝트 시작

``` shell
react-native init ReactProject
```

위의 react-native 명령어를 실행해주면, 새로운 프로젝트가 생성된다.<br />
생성된 프로젝트 폴더 내부에는 iOS/Android 프로젝트가 각각 생성되어 있으며, 실제로는 index.ios.js, index.android.js 파일을 통해서 어플리케이션이 동작하게 된다.<br />

직접 Xcode 로 iOS 프로젝트를 실행해보면, 기본 페이지를 확인할 수 있다.<br />

<br />




# 참고
- [React Native](https://facebook.github.io/react-native/docs/getting-started.html)
