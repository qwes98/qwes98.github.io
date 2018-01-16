---
layout: post
title: Anaconda를 이용한 Tensorflow, Keras, Opencv 설치
categories: [Deep Learning]
excerpt: " "
comments: true
share: true
tags: [Deep Learning,Tensorflow,Keras,Opencv,Anaconda,Kasa Project]
date: 2018-01-14
---

# **Introduction**
> Tensorflow, Keras는 딥 러닝을 위한, Opencv는 컴퓨터 비전을 위한 라이브러리이다. 글쓴이는 [End-to-End Learning](https://arxiv.org/abs/1604.07316)을 위해 이 3가지 라이브러리를 설치하게 되었는데 Anaconda를 이용하면 쉽게 설치할 수 있다는 것을 알게 되어 공유하고자 한다.

----
# **Environment**
> Ubuntu 16.04 LTS

----
# **Install & Build**
> 이제 우분투에 Anaconda를 이용하여 Tensorflow, Keras, Opencv를 한번에 설치해보자.

## Step 1: Anaconda 설치
> Anaconda란 파이썬 기반의 라이브러리(패키지)들을 모아놓아 설치 및 환경 설정들을 쉽게 할 수 있도록 도와주는 개발 플랫폼이다. Anaconda를 사용하면 위의 라이브러리들을 손쉽게 설치할 수 있다.

1. [Anaconda 홈페이지](https://www.anaconda.com/download/#linux)에 들어가서 자신의 플랫폼에 맞는 Python 3.6 version을 다운로드한다

2. Downloads 디렉토리로 들어간다
```
cd ~/Downloads/
```

3. Anaconda 쉘 스크립트(.sh)의 권한을 변경한다
```python
chmod a+x Anaconda3-5.0.1Linux-x86_64.sh
#Warning: Anaconda의 Release 버전, 사용자의 플랫폼에 따라 파일의 이름이 다를 수 있다
```

4. 쉘 스크립트를 실행시킨다
```python
./Anaconda3-5.0.1Linux-x86_64.sh
#Warning: 설치 마지막에 yes를 입력해 주어야 한다. 아래는 설치 마지막 콘솔 output이다
#Output
#...
#installation finished.
#Do you wish the installer to prepend the Anaconda3 install location to PATH in your /home/sammy/.bashrc ? [yes|no]
#[no] >>> 
```

## Step 2: 환경설정 파일 다운로드 및 conda 실행
> git을 통해서 yml 확장자를 가진 환경설정 파일을 받을것이다. 그 후 conda 명령어를 통해 라이브러리의 설치를 진행한다.

1. 환경설정 파일을 포함한 Repository를 받는다
```
git clone https://github.com/naokishibuya/car-behavioral-cloning.git
```

2. Repository 안으로 들어간다
```
cd car-behavioral-cloning/
```

3. 자신의 플랫폼 환경에 따라 conda 명령어를 실행한다
```python
# Use TensorFlow without GPU
conda env create -f environment.yml
# Use TensorFlow with GPU
conda env create -f environment-gpu.yml
```

## Step 3: 가상환경 실행
> 설치는 모두 완료되었다. Tensorflow, Keras, Opencv를 사용하기 위해서는 가상환경을 실행시켜야 한다.

1. 가상환경을 실행시킨다
```
source activate car-behavioral-cloning
```

2. 모든 작업이 끝났다면 가상환경을 종료시킨다
```
source deactivate
```

----
# **Reference**

* [Github of Siraj Raval](https://github.com/llSourcell/How_to_simulate_a_self_driving_car)