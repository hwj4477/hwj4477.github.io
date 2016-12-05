---
layout:     post
title:      Ruby on Rails - Bootstrap
author:     wjhong
tags:    	ROR Bootstrap
subtitle:  	레일즈 부트스트랩 활용
category:   ROR
---

# Ruby on Rails
레일즈를 주로 API서버 용도로 활용하다 보니, 관리자 페이지 작성이 필요하게 되곤 한다.<br />
Scaffolding 기능을 활용해서 자동으로 생성된 페이지에 Bootstrap을 적용해서 관리자 페이지를 작성 해보려고 한다.<br />

# Bootstrap 적용

### Gem 설치

``` Ruby
# Gemfile

gem 'bootstrap-sass'
```

Gemfile 에 위와 같이 'bootstrap-sass' 잼을 추가한 뒤 번들러로 설치해 준다.

### assets 파일 수정

``` javascript
// 경로: /app/assets/javascript/application.js

//= require jquery
//= require jquery_ujs
//= require bootstrap-sprockets
    .
    .
    .

```
application.js 파일에 bootstrap-sprockets 추가 해준다.
<br/><br/>

``` stylesheet
# 경로: /app/assets/stylesheets/application.css.scss

@import "bootstrap-sprockets";
@import "bootstrap";
```
application.css.scss 파일에도 bootstrap-sprockets, bootstrap 추가 해준다

### assets precompile
``` shell
rake assets:precompile
```

위의 명령어로 precompile 하면 적용이 완료된다. <br />

# 결과
![Swagger_Bootstrap_Result2]({{ site.url }}/img/post/rails_bootstrap/rails_bootstrap_2.jpg)
<br />


# 참고
- [twbs/bootstrap-sass](https://github.com/twbs/bootstrap-sass)
