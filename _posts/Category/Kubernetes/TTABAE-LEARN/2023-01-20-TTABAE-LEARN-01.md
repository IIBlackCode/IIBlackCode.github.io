---
layout:     BLACKCODE
title:      "Kubernetes [2/36]"
subtitle:   "[따배쿠] 1. Kubernetes (쿠버네티스)소개"
description: "https://www.youtube.com/playlist?list=PLApuRlvrZKohaBHvXAOhUD-RxD0uQ3z0c"
date:       2023-01-20 12:00:00
author:     "MADness"
header-img: "assets/owner/hero/home-bg.jpg"
header-video: "assets/video/metrix.mp4"
thumbnail: /assets/owner/blog/thumbs/thumb01.png
tags: [따배쿠]
category: [Kubernetes]
# comments: false
# share: false
---

<iframe width="560" height="315" 
src="https://www.youtube.com/embed/Sj9Z6-w1VUE?list=PLApuRlvrZKohaBHvXAOhUD-RxD0uQ3z0c" 
title="[따배쿠] 1. Kubernetes (쿠버네티스)소개" 
frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

---

## 컨테이너 이미지 생성 예시
#### 컨테이너 이미지 생성
    - webserver 컨테이너 생성

#### 1. Local 환경에서 docker파일로 컨테이너 빌드 

    docker build -t smlinux/nodeinfo:v1
    docker images

#### 2. docker hub(public, private)로 업로드(push)

    docker push smlinux/nodeinfo:v1

#### 3. 업로드된 Docker 이미지를 사용할 환경에서 Docker 컨테이너 다운로드

    * 도커 이미지 pull
    docker pull smlinux/nodeinfo:v1

    * 도커 생성, 포트포워딩외부 80 > 내부8080
    docker create --name app -p 80:8080 smlinux/nodeinfo:v1
    
    * Docker 실행
    docker start app

---

## 가상머신 VS 컨테이너 구조 비교

Virtual Machine                         | Container
--------------------------------------- | ---------
App A, App B, App C                     | App A, App B, App C, App D, App E, App F
Guest Operation System                  | Docker
Hypervisor : ex) VMWARE, Virtual box    | Host Operation System [Linux, Windows]
Infrastructure (H/W)                    | Infrastructure (H/W)

---

## 차이점
### - 가상머신

    Application이 돌아가기 위한 Guest Operation System이 필요
    App 크기가 100M라고 할 경우
    App A의 크기는 100M + OS의 크기가 필요

### - 컨테이너 : 주 목적 - 배포

    App 크기가 100M라고 할 경우
    100M의 컨테이너를 웹 기반으로 작동시킴, 가상머신보다 가볍고 빠름

---

## 컨테이너 오케스트레이션
    Application들을 전체적으로 웹 서비스에 가장 적합하게 배치해서 운영 해 주는 것
    
    지위자(Control plan)가 Application Container 적절한곳에 배치
    
    EX)1. 하기와 같은 구성에서 Worker node1이 서비스 다운될 경우
    Worker node1 - WEB1, nodeJS
    Worker node2 - WEB1, WEB2
    
    EX)2. 아래와 같이 다른쪽 노드로 옮겨서 컨테이너 서비스를 유지시켜준다.
    Worker node1 - WEB1, nodeJS
    Worker node2 - WEB1, WEB2, nodeJS

    * 이처럼 컨테이너를 옮기기도 하고 필요하면 확장 및 축소
    * Control Plan을 두고 Work Node를 관리해주는 이러한 구조를
    * 컨테이너 오케스트레이션 이라 함


---

## 컨테이너 계층구조

계층 | 종류 | 설명
---- | ---- | ----
Layer6 | Development Workflow<br>Opinionated Containers | OpenShift, Cloud Foundary, Docker Cloud, Deis, Flynn ...
Layer5 | Orchestration/Scheduling Service Model | `Kubernetes`, Docker Swarm, Marathon/Mesos, Nomad, Diego ..
Layer4 | Container Engine | Docker, Rocket, RunC(OCI), Osv, LXC, LXD
Layer3 | Operating System | Ubuntu, RHEL, CoreOS, Unikernels
Layer2 | Virtual Infrastructure | vSphere, EC2, GCP, Azure, OpenStack
Layer1 | Physical Infrastructure | Raw Computer, Network, Storage

---

## K8S 특징
    - 워크로드 분리
    - 어디서나 실행가능 - 온프레미스, 퍼블릭클라우드(AKS, EKS, GKS등)
    - `선언적 API`

---

## 선언적 API
    DevOps
    NoOps