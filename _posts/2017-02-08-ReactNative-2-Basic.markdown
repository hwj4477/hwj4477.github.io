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
아래의 샘플 및 내용 정리는 개인적으로 이해한 내용을 정리한것 이므로, 정확히는 React Native 공식 문서를 참고 하길 바란다. <br />

참고로, 개인적으로 iOS를 더 선호하기 때문에 iOS 기준으로 테스트를 진행하였다. <br />

<br />

# React 기본 개념

React Native 를 이해하기에 앞서 React 에 대한 이해가 먼저 필요하다. <br />
그러나, 본 포스팅은 React 를 설명하기 위한 포스팅이 아니므로 아래에 진행할 React Native Sample 작성을 이해할 수 있는 수준으로 최소한만 설명하려고 한다.<br />
<br />

### component

React 에서의 화면 작성은 Component 로 이루어 진다. <br />
아래는 기본적인 Component 클래스 작성의 예시 이다. <br />

``` javascript
import React, {Component} from 'react';
                                        
class Hello extends Component {
    render () {
        return <div>{ this.props.message }</div>;
    }
}
```

위의 '<div>{ this.props.message }</div>;' 에 해당하는 부분이 Javascript 코드 내에 XML 스타일의 구문을 작성할 수 있는 JSX 을 활용한 부분이다. <br />
좀 더 자세한 내용은 React Native 기준으로 Sample 을 작성해 보면서 확인해 볼 생각이다. <br />

React Native 에서는 div 가 아닌 Text, View 등의 Component 로 화면을 작성한다. <br />

모바일 Native 앱 기준으로 설명하면, Component 가 UIViewController 의 역할을 할수도 있고, UIViewController 의 화면 내부에 위치하는 특정 이벤트를 처리하는 버튼이 될 수도 있다. <br />
<br />

### props

props 는 Component 에서 다른 Component 로 변동되지 않는 데이터를 전달할 때 사용된다. <br />

예를 들면 위의 Hello Component 를 아래의 Main Component 에서 사용할 경우, 다음과 같은 방식으로 데이터를 전달한다. <br />

``` javascript
import React, {Component} from 'react';

import Hello from './Hello';

class Main extends Component {
    render () {
        <Hello message='Hello' />
    }
}
```

이렇게 전달된 props 값은 Hello Component 내에서 변동될 수 없다. Component 사용 시 데이터를 전달하는 용도로만 사용된다. <br />

위의 Hello Component 의 { this.props.message } 가 부모 Component 로 부터 전달받은 message 라는 props 값을 사용하고 있는 부분이다. <br />
<br />

### state

state 는 Component 내에서 변동 가능한 데이터를 다룰때 사용한다. <br />
Component Class 내의 constructor(생성자) 내에서 this.state={} 형태로 설정한다. <br />

state 의 값을 변경할때는 this.setState() 메소드를 사용한다. <br />

``` javascript
import React, {Component} from 'react';

import Hello from './Hello';

class Main extends Component {
    constructor(props) {
        super(props);
           
        this.state = {
            title: "State",
            subTitle: "state example"
        };
    }

    render () {
        <Hello message={this.state.title} />
    }
}
```
<br />

# Navigator Sample

React Native 는 모바일 어플리케이션의 화면을 구성하기 위한 라이브러리다. <br />
그렇기 때문에, Application 레벨의 처리는 나중으로 미루고 간단한 화면 구성 및 전환을 테스트 해보려고 한다. <br />

iOS 어플리케이션 작성 시 화면 전환 및 네비게이션 구조 관리를 위해 UINavigationController 를 통해 UIViewController 를 연결, 관리한다. <br />

React Native 에서는 Navigator Component 를 사용해서 UINavigationController 을 구현할 수 있다. <br />
아래 Sample 에서는 NavigatorIOS Component 를 활용했다. <br />

Sample 내용을 간단히 설명하면, Navigator 를 포함한 App Component 를 통해 MainScene <-> SecondScene Component 간 화면 전환 하는 간단한 샘플이다. <br />

<br />

### index.ios.js

``` javascript
import React, { Component, PropTypes } from 'react';
import { AppRegistry } from 'react-native';

import App from './App/App';

class ReactProject extends Component {
  render() {
      return (
            <App />
        );
    }
}

AppRegistry.registerComponent('ReactProject', () => ReactProject);
```

프로젝트 루트 경로에 있는 index.ios.js 소스파일 내용이다. <br />

App Component 를 import 하여 루트가 되는 ReactProject Component 를 작성, AppRegistry 를 통해 등록하는 내용이다. <br />
새로 생성한 프로젝트의 소스와 비교해보면 크게 다르지 않을 것이다. 소스 관리 편의를 위해 App Component 를 추가했다. <br />

AppRegistry 는 App 의 루트 Component 를 지정하여, 어플리케이션 시작을 등록하는 API 이다. <br />

정리하면 위의 소스는 App Component 를 포함하는 ReactProject Component 를 루트로 하는 모바일 어플리케이션을 실행한다. <br />
<br />

### App.js

``` javascript
import React, { Component, PropTypes } from 'react';
import { AppRegistry, StyleSheet, NavigatorIOS } from 'react-native';

import MainScene from './MainScene';

class App extends Component {
  render() {
    return (
        <NavigatorIOS
            initialRoute={{
                component: MainScene,
                title: 'ReactProject'
            }}
            style={{ flex: 1 }}
        />
    );
  }
}

module.exports = App;
```

App Component 는 NavigatorIOS Component 를 포함하고 있다. NavigatorIOS 의 initialRoute에 MainScene Component 를 지정하였다. <br />
UINavigationController 의 rootViewController 를 설정하는 과정이라고 생각할 수 있다. <br />

MainScene.js 소스에서 확인 가능하겠지만, MainScene 내부에서는 props 를 통해 Navigator 에 접근할 수 있다. <br />

유의할 점은, 가장 아래의 module.exports = App; 을 작성해 주어야 외부에서 해당 Component 를 import 하여 사용할 수 있다. <br />
<br />

### MainScene.js

``` javascript
import React, { Component, PropTypes } from 'react'
import { AppRegistry, StyleSheet, View, Text, NavigatorIOS, TouchableHighlight } from 'react-native';

import SecondScene from './SecondScene';

// MainScene
class MainScene extends Component {
  static propTypes = {
    navigator: PropTypes.object.isRequired,
  }

  _onForward = () => {
    this.props.navigator.push({
        title: "SecondScene",
        component: SecondScene
    });
  }

  render() {
    return (
        <View style={{paddingTop: 150, alignItems: 'center' }}>
            <TouchableHighlight onPress={this._onForward}>
                <Text>Next Scene</Text>
            </TouchableHighlight>
        </View>
        )
    }
}

module.exports = MainScene;
```

MainScene Component 는 TouchableHighlight Component 의 onPress 이벤트를 통해 SecondScene 로 화면 전환 하도록 작성되었다. <br />
this.props.navigator 를 통해 Navigator 에 접근하여 push 메소드를 통해 화면을 전환한다. <br />

이 부분이 위에서 말한 props 를 통해 Navigator 에 접근하는 부분이며, UINavigationController 형태와 유사하다. <br />
<br />

### SecondScene.js

``` javascript
mport React, { Component, PropTypes } from 'react'
import { AppRegistry, StyleSheet, View, Text, NavigatorIOS, TouchableHighlight } from 'react-native';

// SecondScene
class SecondScene extends Component {
  constructor(props) {
    super(props)

    this.state = {title: "Change Title"};
  }

  static propTypes = {
    navigator: PropTypes.object.isRequired,
  }

  _onPressed = () => {

    if(this.state.title == "Changed !!!") {

        this.props.navigator.pop();

    } else {

        this.setState({title: "Changed !!!"});
    }
  }

  render() {
    return (
        <View style={{paddingTop: 150, alignItems: 'center' }}>
            <TouchableHighlight onPress={this._onPressed}>
                <Text>{this.state.title}</Text>
            </TouchableHighlight>
        </View>
    );
  }
}

module.exports = SecondScene;
```

SecondScene Component 도 비슷하게 TouchableHighlight Component 의 이벤트를 활용하여 작성 했으며, state 도 활용해 보았다. <br />

역시 SecondScene 에서도 props 를 통해 Navigator 에 접근 하여 push, pop 메소드를 통해 화면 전환이 가능 하다. <br />
<br />

### 결과

![React_Native_Navigator]({{ site.url }}/img/post/react-native/react-navigator.gif)
<br/>

iOS Native 네비게이션 바와 그 동작이 완벽하게 구현된다. <br />

React Native 가 Native Component 를 통해 화면을 구성하는 방식이니 당연한 결과지만, 샘플을 작성해 확인해 보니 생각보다 더 만족 스럽다. <br />

NavigatorIOS Component 를 사용했기 때문에, Android 에서의 테스트는 해보지 못해서 툴바 구성등이 궁금하다. <br />
<br />

# 참고
- [React Native](https://facebook.github.io/react-native/docs/getting-started.html)
