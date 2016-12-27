---
layout:     post
title:      Let's Encrypt - Apache 적용
author:     wjhong
tags:    	Apache SE
subtitle:   Let's Encrypt 무료 SSL 인증서 설정
category:   SE
---

# Let's Encrypt, SSL
웹 기반의 서비스에서 HTTPS 지원은 점점 필수가 되어가고 있다.<br />
애플의 ATS(App Transport Security)도 내년(2017)부터 필수 적용이 예정되어 있다.(연기된 것 같긴 하지만..)<br />

회사 업무 차원에서라면 문제 없겠지만, 개인 개발자가 운영하는 경우 SSL 인증서를 발급받아 매번 갱신하며 사용한다는 것이 비용/관리 측면에서 많이 부담스러울 수 밖에 없다.

Let's Encrypt는 ISRG(Internet Security Research Group) 인증 기관을 통해 무료로 SSL 인증을 제공한다.<br />

이전 포스팅에서 테스트 했었던, Swagger UI를 적용한 API 서버에 적용해 보려고 한다.<br />


# Let's Encrypt 적용

### 설치

```shell
git clone https://github.com/letsencrypt/letsencrypt
```

letsencrypt 저장소를 원하는 경로에 clone 한다.<br />
인증서 관리는 루트 권한 계정으로 사용할 경우가 대부분이기 때문에 공통 경로에 저장하는 것을 추천한다. (ex: /var/src/)


### 설정

```shell
./letsencrypt-auto --help
```

명령어 확인을 위해 위와 같은 명령어를 실행하면, 필요한 패키지들을 자동으로 설치해 준다.<br /><br />

### Apache 설정

```shell
./letsencrypt-auto --apache
```

아파치의 경우 위 명령어를 통해 인증서 발급 및 설정까지 자동으로 해준다.<br />
인증서 갱신의 경우도 자동화 기능을 제공하는 듯 하나, 아직 확인해보지는 못했다.

도메인과 관리자 이메일 주소를 입력하고 나면 인증서 발급 및 설정이 완료 된다.<br /><br />

### 추가

위의 '--apache' 옵션을 통해 자동화 설정을 하면 아파치 설치 경로의 sites-available, sites-enabled에 해당 웹사이트 설정 파일이 추가된다.<br />

경우에 따라 웹 사이트의 루트 경로를 직접 설정해 줘야 할 수도 있다.<br /><br />

### 결과

![letsencrypt]({{ site.url }}/img/post/letsencrypt/letsencrypt.jpg)
<br />

### 참고
- [letsencrypt](https://letsencrypt.org/)
