---
layout: post
title: Ubuntu Initial Setting
categories: [Ubuntu]
excerpt: " "
comments: true
share: true
tags: [Ubuntu,Setting,Vim,Ros,Kasa Project]
date: 2018-01-20
---

# **Introduction**
> Ubuntu를 초기에 설치했을 때 Project를 위해 필요한 셋팅들을 정리하고자 한다.

----
# **Environment**
> Ubuntu 16.04 LTS

----
# **Setting**
> Ubuntu에 한글설정부터 시작해서 Vim설정, ROS설치, thema설정, 라이브러리 설치등을 진행해보자.

## 한글 설정
> Ubuntu에서 한글을 사용하려면 한글 설정을 해주어야 한다.

1. ibus-hangul을 설치한다
```python
sudo apt-get install ibus ibus-hangul
```

2. ibus-setup-hangul에 들어가 `start in hangul mode`을 체크한다
```python
ibus-setup-hangul
```

3. ibus를 다시 실행시킨다
```python
ibus restart
```

4. System Settings-Text Entry에 들어가 `Korean (Hangul) (IBus)`를 추가하고 Switch key를 설정한다

## Vim 설치 및 환경설정
> Vim을 설치한 후 환경설정을 해보자.

1. apt를 업데이트한다
```
sudo apt-get update
```

2. Vim을 설치한다
```
sudo apt-get install vim
```

3. git을 설치한다
```python
sudo apt-get install git
```

4. Vim Plugin을 설치하기 위해 Vim Vundle을 설치한다
```python
git clone https://github.com/VundleVim/Vundle.vim.git ~/.vim/bundle/Vundle.vim
```

5. .vimrc파일을 자신의 홈 디렉토리에 만들어 [vimrc](https://qwes98.github.io\assets\posts\20180120\vimrc.html) 내용을 복사하고 저장한다

6. Plugin을 설치한다
```python
vim +PluginInstall +qall
```

## ROS 설치
> Robot Operating System인 ROS의 Kinetic 버전을 간단하게 설치해보자. 만약 이 설치방법이 안된다면 밑에 ROS Indigo 설치 방법으로 설치해보자.

* ROS Kinetic 간단 설치
```python
wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_kinetic.sh && chmod 755 ./install_ros_kinetic.sh && bash ./install_ros_kinetic.sh
```

* ROS Indigo 설치

1. ROS Indigo 설치 및 초기화를 진행한다
```python
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 421C365BD9FF1F717815A3895523BAEEB01FA116
sudo apt-get update
sudo apt-get install ros-indigo-desktop-full
rosdep update
sudo rosdep init
```

2. 홈 디렉토리에 있는 .bashrc에 다음 내용을 추가한다
```python
# Set ROS Indigo
source /opt/ros/indigo/setup.bash
source ~/catkin_ws/devel/setup.bash
# Set ROS Network
export ROS_HOSTNAME=localhost
export ROS_MASTER_URI=http://${ROS_HOSTNAME}:11311
# Set ROS alias command
alias cw='cd ~/catkin_ws'
alias cs='cd ~/catkin_ws/src'
alias cm='cd ~/catkin_ws && catkin_make'
```

3. ROS Workspace 초기화를 진행한다
```python
mkdir -p ~/catkin_ws/src && cd ~/catkin_ws/src && catkin_init_workspace
cd ~/catkin_ws && catkin_make
source ~/.bashrc && source devel/setup.bash
```

## Capslock을 Esc로 바꾸기
> Capslock을 Esc로 바꾸어보자.

1. gnome-tweak-tool를 설치한다
```python
sudo apt-get install gnome-tweak-tool
```

2. gnome-tweak-tool을 실행하여 `Typing-Capslock key behavioral-Make Capslock an additional Escape key`로 변경한다
```python
gnome-tweak-tool
```

## Thema 바꾸기
> Ubuntu의 thema를 바꾸어보자.

1. numix에 대한 ppa를 추가하자
```python
sudo add-apt-repository ppa:numix/ppa
```

2. apt를 업데이트한다
```python
sudo apt-get update
```

3. numix를 설치한다
```python
sudo apt-get install numix-gtk-theme numix-icon-theme
```

4. Ubuntu Software Center에 들어가 unity tweak tool 설치 후 실행한다

## Tensorflow & jupyter 설치
> Tensorflow와 jupyter를 설치해보자.
> 만약 tensorflow뿐만 아니라 Keras, Opencv도 설치하고 싶다면 [Anaconda를 이용한 Tensorflow, Keras, Opencv 설치](https://qwes98.github.io/articles/2018-01/install-tensorflow-keras-opencv-using-anaconda)를 참고해서 설치하자.
> 
> GPU 버전 설치는 조금 다르다. [여기](http://www.popit.kr/tensorflow-install-ubuntu16)를 참고하자

1. 관련된 패키지를 설치한다
```python
sudo apt-get install python3-pip python3-dev python-virtualenv python3-matplotlib
``` 

2. 의존성 문제 해결을 위해 가상환경을 구축한다
```python
virtualenv --system-site-packages -p python3 ~/tensorflow
```

3. tensorflow shell을 실행시킨다
```python
source ~/tensorflow/bin/activate
```

4. tensorflow shell((tensorflow)$) 위에서 나머지 설정을 진행한다
```python
#이 부분이 gpu 버전과 다르다
export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-0.9.0-cp35-cp35m-linux_x86_64.whl
pip3 install --upgrade $TF_BINARY_URL
```

5. tensorflow shell 위에서 jupyter를 설치한다
```python
pip3 install jupyter
#jupyter notebook 실행
jupyter notebook
```


## 기타 설치
> 이 외에 사용하면 편리한 패키지들을 설치해보자.

* tmux 설치
```python
#tmux는 터미널 창을 분리해주는 프로그램이다
sudo apt-get install tmux
```

* Java 설치
```python
sudo apt-get update && sudo apt-get install default-jre && sudo apt-get install default-jdk
```
