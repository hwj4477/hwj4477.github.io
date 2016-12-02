---
layout:     post
title:      Ruby on Rails + Swagger UI
author:     wjhong
tags:    	ROR Swagger
subtitle:  	Rails API 서버 Swagger UI 적용
category:   ROR
---

# Ruby on Rails
레일즈는 기본적으로 RESTful 방식을 사용하고 있기 때문에, API 서버를 구성하는데에도 매우 편하다.<br />
Scaffolding 기능 역시 웹 프론트와 친하지 않은 나에겐 매우 편리하고 감사하다.<br />

간단히 레일즈 API 서버에 Swagger UI 적용하는 예제를 정리하고자 한다.<br />
웹서버 개발 및 테스트를 위해 집에 설정 해둔 라즈베리파이에서 테스트 해보았다.<br />

# Swagger 적용

### swagger-docs Gem 설치

``` Ruby
# Gemfile
gem 'swagger-docs'

```
``` shell
bundle install
```

Gemfile 에 위와 같이 'swagger-docs' 잼을 추가한 뒤 번들러로 설치해 준다.

### Swagger Config 파일 생성
<img src="../img/post/rails_swagger/rails_swagger_config.jpg">
정상적으로 설치가 되었으면, config/initializers/ 경로에 설정 파일을 추가해준다.(swagger_docs.rb)<br />
api_file 경로 설정에 주의하자. 해당 경로로 Swagger json 파일이 생성된다.

### Swagger 적용
<img src="../img/post/rails_swagger/rails_swagger_2.jpg">

요청을 처리 해줄 해당 컨트롤러와 메소드에 위와 같이 Swagger 정보를 설정 해준다.<br />
여기서는 API 버전 관리를 위해서 API::V1::UsersController를 별도로 생성했다.<br />
물론 추가해준 Controller로 요청을 처리하기 위해 routes 설정도 함께 해줘야 한다.

### Swagger Docs 생성
``` shell

rake swagger:docs


```

위 명령어를 실행하면 'swagger_docs.rb'에 설정한 경로에 Swagger 문서가 생성된다.<br />
해당 문서에는 위에서 정의한 API 요청 정보가 담겨있다.<br />

위와 동일하게 진행했다면, public/api/ 경로에 문서가 생성된 걸 확인할 수 있다.

### Swagger 페이지 적용
이제 Swagger 프론트 페이지를 경로에 맞게 넣어주면 된다.<br />
나는 swagger-docs 오픈소스 작성자가 제공하는 샘플 내용을 활용했다.<br />
=> [richhollis/swagger-docs-sample](https://github.com/richhollis/swagger-docs-sample)

### 결과
<img src="../img/post/rails_swagger/rails_swagger_result.jpg">


# 참고
- [richhollis/swagger-docs](https://github.com/richhollis/swagger-docs)
- [richhollis/swagger-docs-sample](https://github.com/richhollis/swagger-docs-sample)
