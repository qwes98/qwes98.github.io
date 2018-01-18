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

1. 원격 저장소(github)의 새로운 branch를 로컬 환경과 연결시킨다.
```python
git pull origin newbranch
# origin은 원격저장소 이름이고, newbranch는 새로운 branch 이름이다
# 이 작업이 끝나면 origin/newbranch라는 원격 branch가 로컬 환경에 만들어진다
``` 

2. 원격 branch에 새로운 로컬 branch를 연결시킨다.
```python
git branch -f newbranch origin/newbranch
```
