---
layout:     post
title:      Ruby on Rails - Deploy (Apache Passenger)
author:     wjhong
tags:    	ROR Passenger Apache
subtitle:  	레일즈 배포하기
category:   ROR
---

# Phusion Passenger 
Ruby, Python, Node.js 의 웹, Application 서버를 지원한다. <br />
레일즈 배포 시 설치도 매우 간단하고, 성능면에서도 뛰어 나다고 한다. <br />

Apache 설치 등 기본적인 설정 내용은 생략 한다. <br />

# Ruby on Rails - Deploy

### Passegner 설치

``` shell
gem install passenger

passenger-install-apache2-module
```
위와 같이 'passenger' Gem을 설치한 뒤 스크립트를 실행해준다. <br />
매우 간단하다. 이것으로 설치는 끝이다. <br />


### Apache 설정
위의 설정을 마치고 나면 몇가지 설정을 보여준다. 자신의 환경에 맞게 아파치 설정을 수정해 주면 된다. <br />

(ex) apache module

``` shell
LoadModule passenger_module /usr/local/rvm/gems/ruby-2.3.0/gems/passenger-5.0.30/buildout/apache2/mod_passenger.so
    <IfModule mod_passenger.c>
    PassengerRoot /usr/local/rvm/gems/ruby-2.3.0/gems/passenger-5.0.30
    PassengerDefaultRuby /usr/local/rvm/gems/ruby-2.3.0/wrappers/ruby
</IfModule>
```

(ex) virtual host

``` shell
<VirtualHost *:80>
    RailsEnv development
    ServerName yourdomain
    DocumentRoot /var/www/html/myweb/public
    <Directory "/var/www/html/myweb/public">
        AllowOverride None
        Require all granted
    </Directory>
</VirtualHost>
```
<br />

### Production 배포
virtual host 설정의 'RailsEnv development' 를 'RailsEnv production' 으로 수정 한다. <br />
그다음 레일즈 프로젝트의 config/secrets.yml 의 production secret_key_base 를 설정해 주면 된다. <br />
secret_key 는 아래의 명령어로 생성이 가능하다. <br />

``` shell
rails secret
```
<br />


# 참고
- [digitalocean.com/community](https://www.digitalocean.com/community/tutorials/how-to-deploy-a-rails-app-with-passenger-and-apache-on-ubuntu-14-04)
