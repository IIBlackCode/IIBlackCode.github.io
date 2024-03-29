---
layout:     BLACKCODE
title:      "Kubernetes [5/36]"
subtitle:   "[따배쿠] 3-1. kubectl 실습 / 실습환경 구성하기"
description: "https://www.youtube.com/playlist?list=PLApuRlvrZKohaBHvXAOhUD-RxD0uQ3z0c"
date:       2023-01-25 01:00:00
author:     "MADness"
header-img: "assets/owner/hero/home-bg.jpg"
header-video: "assets/video/metrix.mp4"
thumbnail: /assets/owner/blog/thumbs/thumb01.png
tags: [따배쿠]
category: [Kubernetes]
# comments: false
# share: false
---

<iframe width="560" height="315" src="https://www.youtube.com/embed/3ChtEuiQ2Yg?list=PLApuRlvrZKohaBHvXAOhUD-RxD0uQ3z0c" title="[따배쿠] 3-1. kubectl 실습 / 실습환경 구성하기" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

    안녕하세요, 이성미 강사입니다!
    어렵게만 느껴지는 쿠버네티스,
    따라하면서 배우면 어느새 지식이 되어 있을 겁니다!

    오늘은 2강에 이어 실습을 위한 환경 구성 및 실습툴을 다뤄 봅니다!
    이 영상을 보기 전 이전 영상을 꼭 시청해 주세요:)

---

    00:00 인트로
    00:11 오늘 배울 내용 소개
    00:56 Review 실습 환경 설정
    04:14 xShell을 이용한 실습 환경 구성
    05:35 kubectl 명령어 설치
    07:24 kubectl이란?
    08:45 kubectl 명령어 구조


# 쿠버네티스로 컨테이너 실행하기
## kubectl 명령어
```
    쿠버네티스에게 요청하는 명령어
```

## kubectl 명령어 기본구조

* kubectl [command] [type] [name] [flags]
    * command : 자원을 실행할 명령어
        * create
        * get
        * delete
        * edit
    
    * type : 자원의 타입
        * node
        * pod
        * service

    * name : 자원의 이름
    * flags : 부가적으로 설정할 옵션
        * --help
        * -o option

## 명령어 예시    
```
    kubectl get pod webserver -o wide
```
## kubectl 명령어 자동완성

- BASH

```    
    source<(kubectl completion bash)
    source<(kubectl completion bash)

    echo "source<(kubectl completion bash)">>~/.bashrc
    echo "source<(kubectlm completion bash)">>~/.bashrc
```

## kubectl commands

```
    kubectl --help
    kubectl command --help

    kubectl run <자원이름> <옵션>
    kubectl create -f obj.yaml
    kubectl apply -f obj.yaml

    kubectl get <자원이름><객체이름>
    kubectl edit <자원이름><객체이름>
    kubectl describe <자원이름><객체이름>

    kubectl delete pod main
```