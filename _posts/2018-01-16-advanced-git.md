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

----
# **Stashing and Cleaning**
> 현재 작업하고 있던 사항들을 임시저장하거나 지울 수 있는 기능이다.

## Stashing으로 작업 임시저장하기
> 작업을 하다가 다른 commit이나 branch로 checkout하고싶은 경우가 있다. 이때 commit을 하지 않으면 checkout이 불가능한데, stashing으로 변경사항들을 임시저장 할 수 있다.

1. 현재 작업 내용을 stash한다
```python
git stash save "~"
# Working directory가 깨끗해진다
# 이 경우에는 tracked 파일만 stash된다. untracked 파일까지 stash하고 싶다면 -u 옵션을 추가하자
# 임의의 이름으로 저장하고 싶을때는 git stash 라고 명령하면 된다
```

2. stash한 내용을 불러오기 위해 stash 리스트를 확인한다
```python
git stash list
# stash는 stack형태로 저장되기 때문에, 지금까지 stash한 리스트가 시간순서로 나타난다
```

3. stash한 내용을 불러온다
```python
git stash apply
# 가장 최근 stash한 내용을 불러온다
# git stash apply stash@{2} 라고 하면 stash@{2}에 해당하는 내용을 불러온다
```

4. stash를 적용해도 stash는 리스트에서 없어지지 않는다. 원한다면 stash를 지울 수 있다
```python
git stash drop stash@{0}
# stash@{0}에 해당하는 stash를 지운다
```

참고: stash는 꼭 깨끗한 Working directory나 stash할 때와 같은 브랜치에서 복원해야 하는것은 아니다. 또한 git은 stash를 적용할 때 staged 상태였던 파일들을 자동으로 다시 staged 상태로 만들어주지 않는다.

## 여러 방법으로 Cleaning 하기
> 마지막 커밋을 한 이후의 수정사항을 지우고 싶을 때 여러 방법이 있다. stash를 이용할 수도 있고, checkout을 사용할 수도 있다.

* stash를 사용한 Cleaning
stash를 사용하면 1)`지운 수정사항이 stash list에 백업이 된다는 것`과 2)`untracked 파일까지 지울 수 있다`는 장점이 있다
```python
git stash
# tracked file들만 지워진다 (add 여부에 상관없이)
git stash --all
# untracked file까지 모두 지워진다
```

* checkout를 이용한 Cleaning
checkout을 이용하면 간단하게 tracked 파일의 변경사항을 지울 수 있다는 장점이 있다
```python
git checkout -- <file>
# <file>에 명시된 파일들의 수정사항을 지운다
```

----
# **Undo**
> 커밋을 한 이후 커밋을 수정하거나, 어떤 파일을 add한 이후 다시 unstage 상태로 바꾸고 싶을 때 사용할 수 있는 기능이다.

## 직전 커밋 수정하기
> 커밋을 한 이후 커밋의 내용을 수정하거나, 특정 파일을 커밋에 추가하고 싶을 때 사용할 수 있다

* 커밋 내용 수정
```python
git commit --amemd
# 다시 커밋창이 뜬다
```

* 특정 파일 커밋에 추가하기
```python
# git commit -m "conmit" 처럼 커밋 진행
git add <file>
git commit --amend
```

## Add된 파일 unstage 상태로 바꾸기
> add된 파일 중 다시 unstage 상태로 바꾸고 싶을 때 사용할 수 있다

* unstage 상태로 바꾸기
```python
git reset Head <staged file>
```
