---
layout:     post
title:      Rails + MongoDB
author:     wjhong
tags:    	  Ruby Rails MongoDB
subtitle:   레일즈 몽고디비 연동
category:   Rails
---

# Rails + MongoDB
MongoDB는 문서지향 데이터베이스이다. 뛰어난 확장성과 성능을 가지고 있으며, 대표적인 NoSQL 데이터베이스 이다. <br />
Mongoid를 통해 루비 온 레일즈에서 사용하는 ORM과 비슷한 형태로 사용할 수 있도록 ODM(Object-Document-Mapper) 기능을 제공한다.

# MongoDB 적용

### Mongoid 설치

``` ruby
gem 'mongoid'
```
``` shell
bundle install
```

Gemfile에 mongoid Gem을 추가한 뒤, 번들러로 설치해준다. <br />

### Mongoid 설정

``` shell
rails g mongoid:config
```

위 명령어로 mongoid 설정 파일을 자동으로 생성해준다. <br />
생성 된 설정 파일은 ./config/mongoid.yml 에 위치 하며 필요에 따라 편집하여 사용하면 된다.

### Model 적용

``` ruby
class Person
  include Mongoid::Document
  field :first_name, type: String
  field :middle_name, type: String
  field :last_name, type: String
end
```

MongoDB 모델(Document)의 기본적인 형태다. <br />
기존, 또는 새로 추가할 모델을 위와같이 적용하여 사용하면 된다. <br />

Person.All, Person.save 같은 기본적인 작업은 기존 ORM 형태와 동일하기 때문에 자연스럽게 적용하여 사용할 수 있다.


### 참고(ex)
- [mongoid](https://docs.mongodb.com/ruby-driver/master/mongoid-tutorials-6.0/)
