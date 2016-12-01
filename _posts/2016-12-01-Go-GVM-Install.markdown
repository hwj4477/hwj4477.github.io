---
layout:     post
title:      GVM(Go Version Manager) 설치
author:     wjhong
tags:    	Go Tools
subtitle:  	GVM 설치를 통한 Go 개발 환경 설정
category:   Go
---

# GVM (Go Version Manager)
프로그래밍 언어인 Go의 버전 관리자다.

그 동안 Go를 [HomeBrew](http://brew.sh/index_ko.html)를 통해 설치해서 사용하고 있었으나, 좀 더 편리한 버전 관리를 위해 GVM을 사용해 보려 한다.<br />
GVM은 Go의 버전 관리 및 버전 별 패키지 관리를 제공한다. 설치 역시 간편하고, GOPATH 설정도 자동으로 해준다.<br />
Ruby의 [RVM](https://rvm.io/)과 비슷한 형식으로 비슷한 기능을 제공한다.

아래 내용은 'macOS' 기준으로 작성되었다.

# 설치

### Install GVM
``` shell
bash < <(curl -s -S -L https://raw.githubusercontent.com/moovweb/gvm/master/binscripts/gvm-installer)
```
위의 명령어를 통해 스크립트를 실행해 주면 바로 설치가 완료된다.

### Install Go
``` shell
gvm install go1.7
```
gvm 명령어를 통해 Go를 설치할 수 있다.

추가로 macOS 에서는 아래의 툴 들을 요구한다.<br />
혹시 위의 명령어로 바로 설치가 안된다면 아래 내용을 확인 후 시도해보면 된다.

``` shell
xcode-select --install
brew update
brew install mercurial
```

### 설치 확인

GOPATH 설정을 따로 하지 않아도 정상적으로 동작하는 걸 확인 할 수 있다. 
``` shell
echo $GOPATH
$HOME/.gvm/pkgsets/go1.7/

---------------------------

gvm list
gvm gos (installed)

   go1.4
=> go1.7
```

# 패키지 관리
GVM은 패키지 관리 기능을 제공한다.<br />
RVM이 Ruby 버전별로 의존성을 가지는 라이브러리(Gem)들을 따로 관리 해주는 것과 비슷하다.

### 생성
``` shell
gvm pkgset create go-global
```

### 확인
``` shell
gvm pkgset list

=> global
   go-global
```
기본으로 global 패키지가 생성되어 지정되어 있다.
위에서 생성한 'go-global' 패키지도 확인 가능하다.

### 설정
``` shell
gvm pkgenv go-global

--------------------------------------------

export GVM_ROOT; GVM_ROOT="/Users/wjhong/.gvm"
export gvm_go_name; gvm_go_name="go1.7"
export gvm_pkgset_name; gvm_pkgset_name="global"
export GOROOT; GOROOT="$GVM_ROOT/gos/go1.7"
export GOPATH; GOPATH="$GVM_ROOT/pkgsets/go1.7/global"
export GVM_OVERLAY_PREFIX; GVM_OVERLAY_PREFIX="${GVM_ROOT}/pkgsets/go1.7/global/overlay"
export PATH; PATH="${GVM_ROOT}/pkgsets/go1.7/global/bin:${GVM_ROOT}/gos/go1.7/bin:${GVM_OVERLAY_PREFIX}/bin:${GVM_ROOT}/bin:${PATH}"
export LD_LIBRARY_PATH; LD_LIBRARY_PATH="${GVM_OVERLAY_PREFIX}/lib:${LD_LIBRARY_PATH}"
export DYLD_LIBRARY_PATH; DYLD_LIBRARY_PATH="${GVM_OVERLAY_PREFIX}/lib:${DYLD_LIBRARY_PATH}"
export PKG_CONFIG_PATH; PKG_CONFIG_PATH="${GVM_OVERLAY_PREFIX}/lib/pkgconfig:${PKG_CONFIG_PATH}"
export gvm_pkgset_name="go-global"
export GOPATH; GOPATH="/Users/wjhong/.gvm/pkgsets/go1.7/go-global:$GOPATH"
export PATH; PATH="/Users/wjhong/.gvm/pkgsets/go1.7/go-global/bin:$PATH"
# Package Set-Specific Overrides
export GVM_OVERLAY_PREFIX; GVM_OVERLAY_PREFIX="${GVM_ROOT}/pkgsets/go1.7/go-global/overlay"
export PATH; PATH="/Users/wjhong/.gvm/pkgsets/go1.7/go-global/bin:${GVM_OVERLAY_PREFIX}/bin:${PATH}"
export LD_LIBRARY_PATH; LD_LIBRARY_PATH="${GVM_OVERLAY_PREFIX}/lib:${LD_LIBRARY_PATH}"
export DYLD_LIBRARY_PATH; DYLD_LIBRARY_PATH="${GVM_OVERLAY_PREFIX}/lib:${DYLD_LIBRARY_PATH}"
export PKG_CONFIG_PATH; PKG_CONFIG_PATH="${GVM_OVERLAY_PREFIX}/lib/pkgconfig:${PKG_CONFIG_PATH}"
```
pkgenv 명령어를 통해 해당 패키지를 설정 할 수 있다.

### 사용
``` shell
gvm pkgset use go-global --default
Now using version go1.7@go-global

---------------------------------------------

echo $GOPATH
$HOME/.gvm/pkgsets/go1.7/global:$HOME/.gvm/pkgsets/go1.7/go-global
```
기본 패키지를 지정하고 나면, GOPATH 에 해당 패키지 경로가 지정 된 걸 확인할 수 있다.<br />
패키지 경로는 Go 버전별, 패키지 이름 별로 나뉘기 때문에 필요에 따라 나누어 관리할 수 있다.

# TODO
- RVM과 비슷하겠거니~~~ 생각하고 있지만, 실제로 버전 업데이트 할 때 마다 불편함은 없는지 확인해 볼 생각
- Go언어를 통한 API서버 구현

# 참고
- [https://github.com/moovweb/gvm](https://github.com/moovweb/gvm)
