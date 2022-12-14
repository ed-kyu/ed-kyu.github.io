---
layout: post
title: ETC Content
description: >
  깃헙 블로그 작성 과정에서 생긴 문제들 정리
sitemap: false
hide_last_modified: true
---

## 깃헙 블로그 생성 과정

### 1. 깃헙 repository 생성

레포명 : <깃헙 아이디>.github.io



### 2. Jekyll 다운 (WSL 이용)

**리눅스** **터미널**에서 ruby를 다운로드 먼저 하고 진행해야 한다.

```shell
sudo apt-get install ruby
```

다운로드 하는데 다음과 같은 에러가 떠서 **apt-get install udpate**를 해주고 진행했다.

```shell
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```



gem 명령어를 사용하려고 하니 이번에는 `Ruby: You don't have write permissions for the /var/lib/gems/2.7.0 directory.` 에러가 발생 => 아래와 같이 환경변수를 추가해서 해결

```shell
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```



[jekyll 사이트](https://jekyllrb-ko.github.io/) 

```shell
gem update
gem install bundler jekyll
```



위 명령어를 입력했더니 다음과 같은 에러가 발생했다.

```shell
Building native extensions. This could take a while...
ERROR:  Error installing jekyll:
        ERROR: Failed to build gem native extension.
```

jekyll 다운로드가 제대로 되지 않아 다음과 같은 명령어로 해결

```shell
sudo apt-get install build-essential
sudo apt install ruby-dev make gcc
sudo apt-get install ruby-dev
```



### 3. Jekyll 시작

```shell
jekyll new ./
만든 깃헙 레포를 clone해서 root 디렉토리에서 진행했는데, 제대로 진행되지가 않았다.
jekyll new ./ --force로 해결
```



### 4. 번들 설치 및 로컬 서버 띄우기

```shell
bundle install
bundle exec jekyll serve
```



### 5. Jekyll 테마 골라서 적용

테마 찾는 사이트 목록

- [http://jekyllthemes.org/](http://jekyllthemes.org/)
- [https://jekyllthemes.io/free](https://jekyllthemes.io/free)
- [http://themes.jekyllrc.org/](http://themes.jekyllrc.org/)
- [https://github.com/topics/jekyll-theme](https://github.com/topics/jekyll-theme)



테마를 다운받고 repo 폴더에 붙여넣기 + `jekyll new ./` + 깃헙에 commit 후 push
