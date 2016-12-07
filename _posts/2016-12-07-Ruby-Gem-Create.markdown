---
layout:     post
title:      Ruby Gem 생성, 배포
author:     wjhong
tags:    	Ruby Gem
subtitle:   루비 잼 만들기
category:   Ruby
---

# Ruby Gem
Gem은 Ruby 패키지를 관리 해주는 기능 제공한다. 사용하기도, 만들기도 쉽고 편리하다. <br />
직접 Gem을 만들고 [rubygems.org](https://rubygems.org/)를 통해 배포하는 과정을 소개하고자 한다.<br />

# Gem 생성, 배포

### 디렉토리 구성

``` shell
bundle gem gem_name

tree gem_name
├── CODE_OF_CONDUCT.md
├── Gemfile
├── LICENSE.txt
├── README.md
├── Rakefile
├── bin
│   ├── console
│   └── setup
├── gem_name.gemspec
├── lib
│   ├── gem_name
│   │   └── version.rb
│   └── gem_name.rb
└── spec
    ├── gem_name_spec.rb
        └── spec_helper.rb
```

번들러를 사용해서 Gem의 기본 디렉토리 구조를 생성할 수 있다. <br />
주로 'lib/' 경로에 소스를 작성하게 된다. <br />

### gemspec

``` ruby
Gem::Specification.new do |spec|
  spec.name          = "gem_name"
  spec.version       = 1.0.0
  spec.authors       = ["hwj4477"]
  spec.email         = ["hwj4477@gmail.com"]

  spec.summary       = %q{TODO: Write a short summary, because Rubygems requires one.}
  spec.description   = %q{TODO: Write a longer description or delete this line.}
  spec.homepage      = "TODO: Put your gem's website or public repo URL here."
  spec.license       = "MIT"
    .
    .
    .
    .
    .
end

```

gem build를 위해 참고하는 spec 파일이다. <br />
gem이 설치되거나 저장소에 push 될때 반영되는 정보로 알맞게 작성해주면 된다. <br />

### build, push

``` shell
gem build gem_name.gemspec

gem push gem_name-1.0.0.gem
```

위의 명령어를 참고해서 빌드하면 'gem_name-1.0.0.gem' 의 형태로 gem 파일이 생성된다. <br >

생성된 gem 파일을 'gem push' 명령어로 배포할 수 있다. <br />
단, [rubygems.org](https://rubygems.org/) 계정이 필요하다. <br />

### rubygems

![RubyGem1]({{ site.url }}/img/post/ruby_gems/rubygem_1.jpg)

[rubygems.org](https://rubygems.org/) 통해 위와 같이 본인의 계정에 루비잼이 업로드 된 것을 확인할 수 있다. <br />
gemspec 의 homepage 에 깃허브 저장소 url 을 등록하면, rubygems.org 의 해당 gem 페이지에 홈페이지 링크와 연결할 수 된다. <br />

### 사용

``` shell
gem install gem_name
```

다른 잼을 사용할때와 동일하게 gem 명령어를 통해 설치하여 바로 사용이 가능하다. <br />

### 참고(ex)
- [github.com : hwj4477/convert-strings-ios-and](https://github.com/hwj4477/convert-strings-ios-and)
- [rubygems.org : hwj4477/convert-strings-ios-and](https://rubygems.org/gems/convert-strings-ios-and)

