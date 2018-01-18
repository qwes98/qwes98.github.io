---
layout: post
title: Lidar Setting
categories: [Sensor]
excerpt: " "
comments: true
share: true
tags: [Lidar,Sensor,Kasa Project]
date: 2018-01-18
---

# **Introduction**
> Lidar는 자율주행에 사용되는 센서들 중 하나로, Lidar를 사용하기 위한 셋팅에 대해 알아보자

----
# **Initial Setting**
> Lidar를 처음 사용할 때 필요한 셋팅이 있다. 여기서는 Sick사의 Lidar를 기준으로 설명한다.

## Lidar의 내부 IP/통신 IP 확인 및 변경
> Lidar는 하드웨어 내부 IP를 가지고 있으면서 외부 통신을 위한 IP도 가지고 있다. 이때 내부 IP와 통신 IP가 서로 달라야 라이다로부터 데이터를 얻는것이 가능하다. 이를 위해 내부 IP/통신 IP를 확인 및 변경할 필요가 있다.

* 내부 IP
  * Sick사의 LMS151 Lidar의 기본 내부 IP는 `192.168.0.1`이다
  * 내부 IP를 바꾸기 위해서 Sick사에서 제공하는 **Sopas**를 사용할 수 있다
  방법: Sopas -> 왼쪽 연필모양 클릭
  * *Hokuyo* Lidar는 처음에 내부 IP가 지정이 안되어 있어 Hokuyo관련 프로그램으로 윈도우에서 설정해주어야 하는것으로 알고있다

* 통신 IP
  * 통신 IP는 내부 IP와 다르게 설정해주어야 하는데 마지막 숫자만 다르면 된다
    예를 들어 내부 IP가 192.168.0.1이라면 이 IP를 제외한 192.168.0.xxx로 통신 IP를 지정해주면 된다
  * Sick사의 Lidar 통신 IP를 변경하는 방법은 **네트워크 설정**을 이용하는 방법과 **Sopas**를 사용하는 방법이 있다
    * 네트워크 설정을 이용하는 방법은 IPv4설정으로 들어가 Static IP를 정해주면 된다
    * Sopas를 이용하는 방법은 Sopas -> 왼쪽 위 Device -> login -> ~_Client/client (id/password) -> 설정

# **ETC**

* Sick's Telegram List manual: Lidar Communication에 관련된 manual (basic setting, raw data form..)
  * sRA LMD: 들어오는 raw data form