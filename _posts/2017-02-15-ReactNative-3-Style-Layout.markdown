---
layout:     post
title:      React Navive - StyleSheet, Layout
author:     wjhong
tags:    	ReactNative React
subtitle:   React Native - 리액트 레이아웃 작성
category:   ReactNative
---

# React Native StyleSheet, 레이아웃
React Native 의 화면 구성은 Component 의 style props 속성을 설정하는 형태로 되어있다.<br />

Style 설정 형태와 속성명들이 웹 CSS 와 비슷한 듯 하면서도 많이 다르다.<br />
아무래도 Native Component 구성을 위한 속성들이다 보니 다른 속성들이 존재하고, Style 역시 모두 Javascript 로 작성한다. <br />

CSS 와 매칭되는 대부분의 속성들을 가지고 있으며, 카멜 표기법으로 작성되어 있다. <br />

React Native 화면 구성을 테스트 해보면서, 특징적인 부분들을 정리해 보려 한다. <br />

<br />

## 기본 형식
Component 의 style 에 속성을 지정하는 형식이다.<br />
아래와 같이 바로 style 을 설정하거나, StyleSheet 객체를 생성해서 사용할 수도 있다.<br />

``` javascript
import React, { Component } from 'react';
import { AppRegistry, View } from 'react-native';

class SampleView extends Component {
  render() {
      return (
        <View>
            <Text style= { { color: 'red', fontSize: 20 } } />
            <Text style= { styles.textView } />
        </View>
      );
  }
};

const styles = StyleSheet.create({
    textView: {
        color: 'blue',
        fontSize: 15
    },
});

```

<br />

## Size
Android Layout 구성할때 사용하는 DP 개념과 유사하다. <br />
DP 개념을 알고 있다면 쉽게 이해가 가능할 것이다. <br />

화면 밀도와 무관한 크기 형태로 지정한다. <br />
iOS 의 경우에도 Interface Builder 나 소스코드에서 View 작성 시 지정하는 값의 크기대로 화면에 그대로 노출된다. <br />

<View style= `{``{`width: 50, height: 50`}``}` 형태로 단위 없이 값만 설정해주면 된다.<br />

실제로 비교하여 테스트해보진 못했지만, 이런 방식으로 양쪽 플랫폼에서의 화면 구성시 크기 설정에 문제가 없도록 만들어진 것으로 보인다. <br />
<br />

## Flexbox

Android 의 LinearLayout 과 비슷한 개념이다.<br />
LinearLayout 의 orientation, weighSum, weight 속성을 활용한 화면 구성 방식과 비슷하다.<br />

flex 속성을 통해 상위 뷰 기준 비율을 설정하고, flexDirection 속성으로 하위뷰 작성 방향 기준을 설정할 수 있다. <br />

아래의 예시의 경우 위(흰색)/아래(검정색) 배경의 뷰 2개가 1:1 비율로 그려지게 된다.

``` javascript
import React, { Component } from 'react';
import { AppRegistry, View } from 'react-native';

class SampleView extends Component {
  render() {
      return (
        <View style= { { flex: 1, flexDirection: 'column'} } >
            <View style= { { flex: 1, backgroundColor: 'white' } } />
            <View style= { { flex: 1, backgroundColor: 'black' } } />
        </View>
      );
  }
};
```

<br />



# 참고
- [React Native](https://facebook.github.io/react-native/docs/getting-started.html)
