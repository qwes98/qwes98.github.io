---
layout: post
title: 우분투에서 Udacity Simulator 사용을 위한 환경 구축
categories: [Simulator]
excerpt: " "
comments: true
share: true
tags: [Udacity,Simulator,Environment]
date: 2018-01-14
---

# **Introduction**
> Udacity에서 작년 초 [Self-Driving Car NanoDegree Course](https://www.udacity.com/course/self-driving-car-engineer-nanodegree--nd013)에서 사용한 Simulator이다. 현재는 Github에 **오픈소스**로 공개가 되어 누구든지 사용할 수 있다. [Unity Engine](https://unity3d.com/kr/) 위에서 동작되는 프로그램이므로 Unity 지식이 있다면 자신의 원하는대로 커스터마이즈가 가능하다는 장점이 있다.
> 
> [Ref: Udacity Simulator Github Page](https://github.com/udacity/self-driving-car-sim)

----
# **Environment**
> Ubuntu 16.04 LTS

----
# **Install & Build**
> 이제 우분투에 Unity를 설치하고 Simulator 코드를 받은 후 Build하여 Simulator를 실행시켜보자.

## Step 1: git lfs 설치
> git lfs란 large file handling을 하기 위해 github에서 만든 것으로, git을 통해 대용량 파일들도 효과적으로 관리할 수 있게 해준다. 대용량 파일을 처음에만 등록해 놓으면 그 이후에는 git를 사용하는 방식대로 버전관리가 가능하므로 사용하는 방법도 간단하다고 할 수 있다.
> 
> [Ref: Git LFS(Large file storage) 사용해보기](https://devlog.github.io/git-lfs/2015/12/09/git-lfs.html)

1. [git-lfs release](https://github.com/git-lfs/git-lfs/releases/)에 들어가서 `32bit 컴퓨터라면 Linux 386`을, `64bit 컴퓨터라면 Linux AMD64`를 선택해 다운로드한다

2. 압축을 풀고 Downloads 디렉토리로 들어간다
```
cd ~/Downloads/git-lfs-2.3.4/
# Warning: git-lfs의 최신 Release 버전에 따라 디렉토리 이름은 다를 수 있다
```

3. install.sh을 실행하여 설치를 진행한다
```
sudo ./install.sh
```

## Step 2: Unity 설치
> Unity는 게임 개발을 위한 엔진이다. Udacity Simulator가 Unity로 만들어졌기 때문에 Simulator를 수정하고 빌드하려면 Unity를 설치해야 한다.

1. gdebi를 설치한다
```
sudo apt install gdebi
```

2. Unity 설치파일을 다운로드한다
```
wget http://beta.unity3d.com/download/ee86734cf592/unity-editor_amd64-2017.2.0f3.deb
```

3. 설치를 진행한다
```
sudo gdebi unity-editor_amd64-2017.2.0f3.deb
```

## Step 3: Udacity Simulator 코드 받기
> github로부터 Udacity Simulator 코드를 받아야 한다.

1. git clone을 통해 전체 프로젝트를 받는다
```
git clone https://github.com/udacity/self-driving-car-sim 
```

2. git lfs를 이용하여 대용량 파일을 추가로 받는다
```
cd self-driving-car-sim/
git lfs pull
```

## Step 4: Unity 실행 후 빌드를 통해 실행 파일 만들기
> 이제 Unity를 실행하여 Simulator 프로젝트를 불러온 후 빌드를 진행해보자.

1. Ubuntu 탐색창에서 Unity를 입력 후 실행시킨다

2. 로그인 화면이 나타나는데, 아이디를 만들어 로그인을 진행한다

3. 오른쪽 위에 `Open`버튼을 눌러 Simulator 프로젝트를 불러온다

4. 왼쪽 위에 `File > Build Settings`를 눌러 Build Settings로 들어간다

5. 자신의 컴퓨터에 맞게 Target Platform과 Architecture를 선택한 후 `Build`버튼을 누른다

----
# **Reference**

* [Introduction to Udacity Self-Driving Car Simulator](https://towardsdatascience.com/introduction-to-udacity-self-driving-car-simulator-4d78198d301d) : Simulator 설치 및 사용에 대한 전반적인 내용을 다루고 있다