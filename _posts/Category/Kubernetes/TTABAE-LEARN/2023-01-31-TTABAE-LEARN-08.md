---
layout:     BLACKCODE
title:      "Kubernetes [8/36] AKS로 실습"
subtitle:   "[따배쿠] 4-2. 쿠버네티스 아키텍처 - namespace"
description: "https://www.youtube.com/playlist?list=PLApuRlvrZKohaBHvXAOhUD-RxD0uQ3z0c"
date:       2023-01-31 1:10:00
author:     "MADness"
header-img: "assets/owner/hero/home-bg.jpg"
header-video: "assets/video/metrix.mp4"
thumbnail: /assets/owner/blog/thumbs/thumb01.png
tags: [따배쿠]
category: [Kubernetes]
# comments: false
# share: false
---

<iframe width="560" height="315" src="https://www.youtube.com/embed/pfkx8KDAZyk?list=PLApuRlvrZKohaBHvXAOhUD-RxD0uQ3z0c" title="[따배쿠] 4-2. 쿠버네티스 아키텍처 - namespace" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

---

# *** K8S 명령어 실습전 AKS 환경 준비 ***

## VSCODE에서 Azure Potal 접속
1. VSCode에서 명령어 실행
```
Connect-AzAccount
```

2. 계정 선택 및 로그인 진행
![img](https://github.com/IIBlackCode/IIBlackCode.github.io/blob/master/_posts/Category/Kubernetes/img/Connect-AzAccount.PNG?raw=true)

* 아래와 같이 연동작업 

```
PS D:\GIT> Connect-AzAccount
경고: Unable to acquire token for tenant '4aed9820-113d-4f48-9f53-4d91f37ad279' with error 'SharedTokenCacheCredential authentication unavailable. Token acquisition 
failed for user minseo_kim89@megazone.com. Ensure that you have authenticated with a developer tool that supports Azure single sign on.'

Account                   SubscriptionName TenantId                             Environment
-------                   ---------------- --------                             -----------
minseo_kim89@megazone.com kms-limited      xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx AzureCloud
```
3. [AzurePotal] Azure Potal에 접속
    
    1). 상단에 있는 Cloud Shell을 클릭하여 `스토리지 생성`
![img](https://github.com/IIBlackCode/IIBlackCode.github.io/blob/master/_posts/Category/Kubernetes/img/AzureCloudShell.png?raw=true)<br>
    2). 스토리지 만들기 클릭
![img](https://github.com/IIBlackCode/IIBlackCode.github.io/blob/master/_posts/Category/Kubernetes/img/createStorage.PNG?raw=true)<br>
    3). Cloud Shell 진입
![img](https://github.com/IIBlackCode/IIBlackCode.github.io/blob/master/_posts/Category/Kubernetes/img/AccessAzureCloudShell.png?raw=true)

4. VSCODE에서 Azure Cloud Shell 클릭
![img](https://github.com/IIBlackCode/IIBlackCode.github.io/blob/master/_posts/Category/Kubernetes/img/2023-01-25-Kubernetes-05_1.png?raw=true)

5. 상단에 구독 선택
![img](https://github.com/IIBlackCode/IIBlackCode.github.io/blob/master/_posts/Category/Kubernetes/img/2023-01-25-Kubernetes-05_2.png?raw=true)

6. VSCode에서 접속 성공한 모습
![img](https://github.com/IIBlackCode/IIBlackCode.github.io/blob/master/_posts/Category/Kubernetes/img/2023-01-25-Kubernetes-05_3.png?raw=true)

## VSCode 연동작업 완료

---

# yaml 템플릿
- 사람이 쉽게 읽을 수 있는 데이터 직렬화 양식
- 기본 문법
    - 구조화된 데이터를 표현하기 위한 데이터 포맷
    - Python처럼 들여쓰기로 데이터 계층을 표기
    - 들여쓰기를 할 때에는 Tab이 아닌 Space Bar(2칸)를 사용
    - 가독성이 좋아 설정 파일에 적합한 형식
    - Scalar 문법 :  ':'을 기준으로 key:value를 설정
        ```
        name: nginx
        ```
    - 배열 문법 : '-' 문자로 여러 개를 나열
        ```
        ports:
        - containerPort: 80
        - containerPort: 443
        ```
    - 공식 사이트 : http://yaml.org/
    - kubernetes yam example
      $cat nginx-pod.yaml

## yaml 예시코드
```
apiVersion: apps/v1
kind: Pod
parent:
  child1: first child
  key2:
    child-1: kim
  key3:
   - grandchild1:
     name: kim
   - grandchild2:
     name: lee #command line
#comment line
```

# API Version
- alpha -> beta -> stable
- kubernetes Object 정의 시 apiVersion이 필요
- kubernetes가 update하는 API가 있으면 새로운 API가 생성됨

API Object의 종류 및 버전 | --
------------------------ | --
Deployment | apps/v1
Pod | v1
ReplicaSet | apps/v1
ReplicationController | v1
Service | v1
PersistentVolume | v1

```
# 버전을 apps/v1이나 v2로 명시하면 Pod를 찾지못함
apiVersion: v1 
kind: Pod # v1으로 동작중
parent:
  child1: first child
  key2:
    child-1: kim
  key3:
   - grandchild1:
     name: kim
   - grandchild2:
     name: lee #command line
#comment line
```