---
layout:     post
title:      React Navive - React 기본
author:     wjhong
tags:    	ReactNative React
subtitle:   React Native - React 기본, Navigator Sample
category:   ReactNative
---

# React Native
React Native 는 React의 UI 작성 접근 방법을 네이티브 모바일로 확장하는 기능을 제공한다. <br />
가장 큰 특징은 웹뷰를 통해 Web Component 로 화면을 구성하는게 아니라 모바일 Native Component 로 화면을 작성한다는 점이다. <br />

이전의 웹뷰를 통한 UI 작성을 하는 하이브리드 방식과는 다르게, JS 코드만으로 모바일 Native UI 작성이 가능하다. <br />
비슷한 다른 솔루션이 있는지는 모르겠지만, 이런 특징이 매우 놀랍고 큰 장점이라고 생각한다. <br />

React Native 는 React 와 매우 흡사하기 때문에 기본적으로 React의 기본적인 구조에 대한 이해가 필요하다. <br />
아주 기본적인 React 내용을 다루고, Navigator Component 를 활용한 샘플 앱을 작성해 보려고 한다. <br />

필자 역시 React 를 학습하고 있는 단계이기 때문에, React Native 와 함께 좀 더 자세히 개념 정리를 하고자 한다. <br />
아래의 샘플 및 내용 정리는 개인적인으로 이해한 내용을 정리한것 이므로, 정확히는 React Native 공식 문서를 참고 하길 바란다. <br />

참고로, 개인적으로 iOS를 더 선호하기 때문에 iOS 기준으로 테스트를 진행하였다. <br />

<br />

# React 기본 개념

### component

React 에서의 화면 작성은 Component 로 이루어 진다. <br />
아래는 기본적인 Component 클래스 작성의 예시 이다. <br />

``` javascript
import React, {Component} from 'react';
                                        
class Hello extends Component {
    render () {
        return <div>Hello</div>;
    }
}
```

위의 '<div>Hello</div>;' 에 해당하는 부분이 Javascript 코드 내에 XML 스타일의 구문을 작성할 수 있는 JSX 을 활용한 부분이다. <br />
자세한 화면 구성 방식은 React Native 기준으로 Sample 작성해 보겠다. <br />

React Native 에서는 div 가 아닌 Text, View 등의 Component 로 화면을 작성한다. <br />

모바일 Native 앱 기준으로 설명하면, Component 가 UIViewController 의 역할을 할수도 있고, UIViewController 의 화면 내부에 위치하는 특정 이벤트를 처리하는 버튼이 될 수도 있다. <br />


### props


### state

# 참고
- [React Native](https://facebook.github.io/react-native/docs/getting-started.html)
