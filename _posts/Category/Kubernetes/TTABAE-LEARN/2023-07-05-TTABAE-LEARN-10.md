---
layout:     BLACKCODE
title:      "5-1-2. 쿠버네티스 Pod - Pod 동작 flow"
subtitle:   "5-1-2. 쿠버네티스 Pod - Pod 동작 flow"
description: "https://www.youtube.com/watch?v=0rYt3PcggzA&list=PLApuRlvrZKohaBHvXAOhUD-RxD0uQ3z0c&index=10"
date:       2023-07-05 1:10:00
author:     "MADness"
header-img: "assets/owner/hero/home-bg.jpg"
header-video: "assets/video/metrix.mp4"
thumbnail: /assets/owner/blog/thumbs/thumb01.png
tags: [따배쿠]
category: [Kubernetes]
# comments: false
# share: false
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

# Pod관리하기

- 동작중인 파드 정보 보기
    ```
    kubectl get pods
    kubectl get pods -o wide
    kubectl describe pod <pod의 이름>
    ```

- 동작중인 파드 수정
    ```
    kubectl edit pod <pod명>
    ```

- 동작중인 파드 삭제
    ```
    kubectl delete pod <pod명>
    kubectl delete pod --all
    ```

    - 명령어 실행 결과
    ```
    master@MASTER:~$ kubectl delete pod --all
    pod "multipod" deleted
    pod "nginx-pod" deleted
    pod "web1" deleted
    ```

# QUESTION & ANSWER
1. 현재 namespace에서 동작중인 Pod는 몇 개인가
    ```
    kubectl get pods
    ```

2. 현재 시스템에서 동작중인 Pod 수는?
    ```
    kubectl get pods --all-namespaces
    ```

3. 컨테이너 nginx를 실행하는 nginx-pod라는 이름의 Pod를 생성하시오
    ```
    kubectl run nginx-pod --nginx-
    kubectl run nginx-pod --image=nginx:1.14
    ```

4. 앞에서 생성한 Pod의 image정보를 확인하는 명령은 무엇인가?
    ```
    kubectl describe pod nginx-pod
    ```

5. 앞에서 생성한 nginx-pod는 어느 node에 배치되었나?
    ```
    kubectl describe pod nginx-pod
    ```

6. 앞에서 생성한 Pod에는 몇 개의 컨테이너가 포함되어 있나?
    ```
    kubectl get pods 후 ready의 수
    kubectl describe pod nginx-pod
    ```

7. 앞에서 생성한 Pod의 현재 상태는 어떠한가?
    ```
    kubectl get pods 후 ready의 수
    kubectl describe pod nginx-pod
    ```

8. 새 포드의 컨테이너 상태는 어떻습니까?
    ```
    # describe를 통해 확인
    kubectl describe pod nginx-pod
    ```

9. `kubectl get pods`명령의 출력에서 READY열은 무엇을 의미하나?
    ```
    현제 ready중인 컨테이너/전체
    ```
10. 생성한 pod를 삭제하시오.
    ```
    kubectl delete pod <pod명>
    ```

11. 컨테이너 image `redis123`을 실행하는 pod`redis`를 redis.yaml을 이용해 생성하시오
    1. yaml 파일 생성전 테스트 명령어
        - --dry-run : 실행이 되는지 확인하는 옵션 명령어
        ```
        kubectl run redis --image=redis123 --dry-run -o yaml
        ```

    2. 실행결과
        ```
        root@MASTER:~# kubectl run redis --image=redis123 --dry-run -o yaml
        W0705 05:54:00.756921   67398 helpers.go:553] --dry-run is deprecated and can be replaced with --dry-run=client.
        apiVersion: v1
        kind: Pod
        metadata:
        creationTimestamp: null
        labels:
            run: redis
        name: redis
        spec:
        containers:
        - image: redis123
            name: redis
            resources: {}
        dnsPolicy: ClusterFirst
        restartPolicy: Always
        status: {}
        ```

    3. 옵션을 추가하여 yaml파일 생성
        ```
        kubectl run redis --image=redis123 --dry-run -o yaml > redis.yaml
        ```

    4. vi 편집기로 생성한 yaml파일 수정
        - redis.yaml
        ```
        apiVersion: v1
        kind: Pod
        metadata:
            name: redis
        spec:
        containers:
        - image: redis123
            name: redis
        ```

    5. yaml파일을 통한 pod 생성
        ```
        kubectl create -f redis.yaml
        ```
    6. 생성된 pod 확인
        ```
        root@MASTER:~# kubectl get pods
        NAME    READY   STATUS         RESTARTS   AGE
        redis   0/1     ErrImagePull   0          10s
        ```

12. 앞서 만든 redis pod의 image를 redis로 수정하여 동작시키시오.

    1. 해당 pod의 세부적인 정보 확인
    > kubectl describe pod redis    
    
        ```
        root@MASTER:~# kubectl create redis.yaml
        Error: must specify one of -f and -k

        error: unknown command "redis.yaml"
        See 'kubectl create -h' for help and examples
        root@MASTER:~# kubectl create -f redis.yaml
        pod/redis created
        root@MASTER:~# kubectl get pods
        NAME    READY   STATUS         RESTARTS   AGE
        redis   0/1     ErrImagePull   0          10s
        root@MASTER:~# ^C
        root@MASTER:~# kubectl describe pod redis
        Name:         redis
        Namespace:    default
        Priority:     0
        Node:         node2/10.100.1.6
        Start Time:   Wed, 05 Jul 2023 05:59:06 +0000
        Labels:       <none>
        Annotations:  <none>
        Status:       Pending
        IP:           10.244.2.7
        IPs:
        IP:  10.244.2.7
        Containers:
        redis:
            Container ID:
            Image:          redis123
            Image ID:
            Port:           <none>
            Host Port:      <none>
            State:          Waiting
            Reason:       ImagePullBackOff
            Ready:          False
            Restart Count:  0
            Environment:    <none>
            Mounts:
            /var/run/secrets/kubernetes.io/serviceaccount from default-token-qq2tk (ro)
        Conditions:
        Type              Status
        Initialized       True
        Ready             False
        ContainersReady   False
        PodScheduled      True
        Volumes:
        default-token-qq2tk:
            Type:        Secret (a volume populated by a Secret)
            SecretName:  default-token-qq2tk
            Optional:    false
        QoS Class:       BestEffort
        Node-Selectors:  <none>
        Tolerations:     node.kubernetes.io/not-ready:NoExecute op=Exists for 300s
                        node.kubernetes.io/unreachable:NoExecute op=Exists for 300s
        Events:
        Type     Reason     Age                     From               Message
        ----     ------     ----                    ----               -------
        Normal   Scheduled  9m33s                   default-scheduler  Successfully assigned default/redis to node2
        Normal   Pulling    7m58s (x4 over 9m32s)   kubelet            Pulling image "redis123"
        Warning  Failed     7m55s (x4 over 9m30s)   kubelet            Failed to pull image "redis123": rpc error: code = Unknown desc = Error response from daemon: pull access denied for redis123, repository does not exist or may require 'docker login': denied: requested access to the resource is denied
        Warning  Failed     7m55s (x4 over 9m30s)   kubelet            Error: ErrImagePull
        Warning  Failed     7m33s (x7 over 9m30s)   kubelet            Error: ImagePullBackOff
        Normal   BackOff    4m27s (x20 over 9m30s)  kubelet            Back-off pulling image "redis123"
        ```

    2. 결과 분석
        ```
        Failed to pull image "redis123"
        ```
        컨테이너 다운받는 도중에 문제가 발생했음을 볼 수 있다.

    3. redis Pod를 편집 해 보자
        > kubectl edit pod redis
        
        1. 위의 명령어 실행
            ```
            root@MASTER:~# kubectl edit pod redis
            serviceAccount: default
            serviceAccountName: default
            terminationGracePeriodSeconds: 30
            tolerations:
            - effect: NoExecute
                key: node.kubernetes.io/not-ready
                operator: Exists
                tolerationSeconds: 300
            - effect: NoExecute
                key: node.kubernetes.io/unreachable
                operator: Exists
                tolerationSeconds: 300
            volumes:
            - name: default-token-qq2tk
                secret:
                defaultMode: 420
                secretName: default-token-qq2tk
            status:
            conditions:
            - lastProbeTime: null
                lastTransitionTime: "2023-07-05T05:59:06Z"
                status: "True"
                type: Initialized
            - lastProbeTime: null
                lastTransitionTime: "2023-07-05T05:59:06Z"
                message: 'containers with unready status: [redis]'
                reason: ContainersNotReady
                status: "False"
                type: Ready
            - lastProbeTime: null
                lastTransitionTime: "2023-07-05T05:59:06Z"
                message: 'containers with unready status: [redis]'
                reason: ContainersNotReady
                status: "False"
                type: ContainersReady
            - lastProbeTime: null
                lastTransitionTime: "2023-07-05T05:59:06Z"
                status: "True"
                type: PodScheduled
            containerStatuses:
            - image: redis123
                imageID: ""
                lastState: {}
                name: redis
                ready: false
                restartCount: 0
                started: false
                state:
                waiting:
                    message: Back-off pulling image "redis123"
                    reason: ImagePullBackOff
            hostIP: 10.100.1.6
            phase: Pending
            podIP: 10.244.2.7
            podIPs:
            - ip: 10.244.2.7
            qosClass: BestEffort
            startTime: "2023-07-05T05:59:06Z"
            ```

        2. spec > containers > image의 이름을 수정한다
            - 수정전
            ```
            spec:
              containers:
              - image: redis123
            ```

            - 수정 후
            ```
            spec:
              containers:
              - image: redis
            ```
        3. pod 확인
            ```
            kubectl get pods
            ```

## 정상적으로 수정됨
```
root@MASTER:~# kubectl get pods
NAME    READY   STATUS    RESTARTS   AGE
redis   1/1     Running   0          26m
```