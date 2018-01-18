---
layout: post
title: Advanced Git
categories: [Git]
excerpt: " "
comments: true
share: true
tags: [Git,Rsa Project]
date: 2018-01-16
---

# **Introduction**
> git은 버전 관리 시스템중 하나로, github와 연동하여 버전 관리 및 협업에 아주 유용하게 사용할 수 있다. 본 포스트에서는 헷갈리는 git의 명령어들을 정리해보고자 한다.
> 목차 네이밍은 [Git Reference](https://git-scm.com/docs)를 기준으로 한다.
> 
> [Ref: Git Documentation](https://git-scm.com/documentation)

----
# **Sharing and Updating Merging**
> git과 github를 연동하여 코드의 백업 및 공유를 통한 협업이 가능하게 해주는 기능이다.

## 새로운 Branch를 Pull 하기
> github에 여러 branch가 있다면 작업하고 싶은 branch를 별도로 pull을 해주어야 로컬 환경에서 작업이 가능하다. 기본적으로는 clone이나 pull을 하면 master branch만 가져오게 된다.

1. 먼저 원격 저장소(github) branch에 대한 정보를 업데이트한다
```python
git remote update
```

2. 원격 저장소의 branch들중 가져올 branch를 확인한다
```python
git branch -r
# 원격 저장소의 branch들을 보여준다
# git branch -a
# 로컬, 원격 저장소의 모든 branch를 보여준다
``` 

3. 원격 branch를 새로운 로컬 branch로 가져온다.
```python
git checkout -t origin/remote-branch-name
# git checkout -t [원격 저장소 이름]/[원격 branch 이름]
# 만약 가져올 branch의 로컬 이름을 바꾸고 싶다면 아래 명령어 사용
# git checkout -b [새로운 로컬 branch 이름] [원격 저장소 이름]/[원격 branch 이름]
```

## 원격 branch로 checkout 하기 
> github에서 가져오지 않은 branch가 있는데, 로컬 저장소에 내려 받기보다는 간단한 확인 및 테스트를 해보고 싶은 경우에 원격 branch로 checkout를 할 수 있다.

1. 원격 branch에 접근한다
```python
git checkout [원격 저장소 이름]/[원격 branch 이름]
# "You are in 'detached HEAD' state"라는 메시지를 볼 수 있다
```

2. 확인 및 테스트가 끝나면 다른 로컬 branch로 이동한다
```python
git checkout [로컬 branch 이름]
# 확인 및 테스트 도중 변경사항이 사라진다
```
