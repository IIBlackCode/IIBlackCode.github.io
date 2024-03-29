---
layout:     BLACKCODE
title:      "Kubernetes 공식 Docs 주소"
subtitle:   ""
description: ""
date:       2020-01-01 1:10:00
author:     "MADness"
header-img: "assets/owner/hero/home-bg.jpg"
header-video: "assets/video/metrix.mp4"
thumbnail: /assets/owner/blog/thumbs/thumb01.png
tags: [Azure]
category: [Kubernetes]
# comments: false
# share: false
---
# Kubernetes 공식 Docs 주소

## CKA Bookmark
## 1. Auth

[Auth - CSR개념과 Role and RoleBinding 생성](https://kubernetes.io/docs/reference/access-authn-authz/certificate-signing-requests/)

[Auth - CSR - TLS](https://kubernetes.io/docs/tasks/tls/managing-tls-in-a-cluster/)

[Auth - ClusterRole](https://kubernetes.io/docs/reference/access-authn-authz/rbac/#clusterrole-example)

[Auth - RBAC Authorization-exam](https://kubernetes.io/docs/reference/access-authn-authz/rbac/)

[Auth - role](https://kubernetes.io/docs/reference/access-authn-authz/rbac/#role-and-clusterrole)

[Auth - Service Accounts for Pods](https://kubernetes.io/docs/tasks/configure-pod-container/configure-service-account/)

[Auth - user -out myuser.csr -subj CN=myuser](https://kubernetes.io/docs/reference/access-authn-authz/certificate-signing-requests/#normal-user)

## 2. Config

[Configure - Create a ConfigMap](https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/#create-a-configmap)

[Configure - Environment Variable](https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/#define-container-environment-variables-using-configmap-data)

[Configure - Volume Mount](https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/#populate-a-volume-with-data-stored-in-a-configmap)

[Secrets - Create Secret](https://kubernetes.io/docs/tasks/configmap-secret/managing-secret-using-kubectl/)

[Secrets - environment variables](https://kubernetes.io/docs/concepts/configuration/secret/#using-secrets-as-environment-variables)

[Secrets - Volume mount](https://kubernetes.io/docs/concepts/configuration/secret/#using-secrets)

## 3. Controllers

[Controller - CronJob](https://v1-20.docs.kubernetes.io/docs/concepts/workloads/controllers/cron-jobs/#cronjob)

[Controller - DaemonSet](https://kubernetes.io/docs/concepts/workloads/controllers/daemonset/)

[Controller - Jobs](https://kubernetes.io/docs/concepts/workloads/controllers/job/)

[Controller - ReplicaSet](https://kubernetes.io/fr/docs/concepts/workloads/controllers/replicaset/)

[Controller - ReplicationController](https://kubernetes.io/docs/concepts/workloads/controllers/replicationcontroller/)

[Controller - StatefulSet Basics](https://kubernetes.io/docs/tutorials/stateful-application/basic-stateful-set/)

## 4. Deploy

[Application - Deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)

[Application - Horizontal Pod Autoscaler](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale-walkthrough/#create-horizontal-pod-autoscaler)

[HPA(Autoscaling)](https://kubernetes.io/ko/docs/tasks/run-application/horizontal-pod-autoscale-walkthrough/#php-apache-%EC%84%9C%EB%B2%84-%EA%B5%AC%EB%8F%99-%EB%B0%8F-%EB%85%B8%EC%B6%9C)

[nginx deploy - service](https://kubernetes.io/docs/concepts/services-networking/connect-applications-service/#exposing-pods-to-the-cluster)

[Updating a Deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/#updating-a-deployment)

## 5. NetworkPolicies

[Network Policies - ingress_egress](https://kubernetes.io/docs/concepts/services-networking/network-policies/#networkpolicy-resource)

[NetworkPolicy - ingress (Declare Network Policy)](https://kubernetes.io/docs/tasks/administer-cluster/declare-network-policy/)

[Network Policies](https://kubernetes.io/docs/concepts/services-networking/network-policies/)

## 6. Node

[Assign Pods to Nodes using Node Affinity Kubernetes](https://kubernetes.io/docs/tasks/configure-pod-container/assign-pods-nodes-using-node-affinity/)

[nodes](https://kubernetes.io/docs/tasks/configure-pod-container/assign-pods-nodes/)

[테인트(Taints)와 톨러레이션(Tolerations) Kubernetes](https://kubernetes.io/ko/docs/concepts/scheduling-eviction/taint-and-toleration/)

[Drain a Node](https://kubernetes.io/docs/tasks/administer-cluster/safely-drain-node/)

## 7. Pods

[Annotations - template](https://kubernetes.io/docs/concepts/overview/working-with-objects/annotations/)

[Label - Labels and Selector 규칙](https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/)

[Pod - Assign CPU Resources](https://kubernetes.io/docs/tasks/configure-pod-container/assign-cpu-resource/#specify-a-cpu-request-and-a-cpu-limit)

[Pod - basic templates](https://kubernetes.io/docs/concepts/workloads/pods/#pod-templates)

[Pod - Command in Shell](https://kubernetes.io/ko/docs/tasks/inject-data-application/define-command-argument-container/#%EC%85%B8-%EC%95%88%EC%97%90%EC%84%9C-%EC%BB%A4%EB%A7%A8%EB%93%9C-%EC%8B%A4%ED%96%89%ED%95%98%EA%B8%B0)

[Pod - Command](https://kubernetes.io/ko/docs/tasks/inject-data-application/define-command-argument-container/)

[Pod - Environment Variables](https://kubernetes.io/docs/tasks/inject-data-application/define-environment-variable-container/#define-an-environment-variable-for-a-container)

[Pod - Init Containers](https://kubernetes.io/docs/concepts/workloads/pods/init-containers/)

[Pod - multi containers](https://kubernetes.io/docs/tasks/access-application-cluster/communicate-containers-same-pod-shared-volume/#creating-a-pod-that-runs-two-containers)

[Pod - ReadinessProbe LivenessProbe](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/)

[Pod - sidecar container with logging agent](https://kubernetes.io/docs/concepts/cluster-administration/logging/#sidecar-container-with-logging-agent)

[Pod - static Pods](https://kubernetes.io/docs/tasks/configure-pod-container/static-pod/#static-pod-creation)

## 8. SecurityContext

[Security Context - Capabilities](https://kubernetes.io/docs/tasks/configure-pod-container/security-context/#set-capabilities-for-a-container)

[Security Context - privileged](https://kubernetes.io/docs/concepts/security/pod-security-policy/#create-a-policy-and-a-pod)

[Security context - runAsNonRoot - middle](https://kubernetes.io/blog/2016/08/security-best-practices-kubernetes-deployment/)

[Security Context - runAsUser runAsGroup](https://kubernetes.io/docs/tasks/configure-pod-container/security-context/#set-the-security-context-for-a-pod)

## 9. Service

[Service - EndPoint](https://kubernetes.io/docs/concepts/services-networking/service/#services-without-selectors)

[Service - Ingress](https://kubernetes.io/ko/docs/concepts/services-networking/ingress/)

[Service - multi-port](https://kubernetes.io/ko/docs/concepts/services-networking/service/#%EB%A9%80%ED%8B%B0-%ED%8F%AC%ED%8A%B8-%EC%84%9C%EB%B9%84%EC%8A%A4)

[Service - NodePort - LoadBalancer 외 type들](https://kubernetes.io/docs/concepts/services-networking/service/#nodeport)

[Service - Pod DNS](https://kubernetes.io/ko/docs/concepts/services-networking/dns-pod-service/)

[NGINX Ingress Controller 설치](https://kubernetes.github.io/ingress-nginx/deploy/)

## 10. Troubleshooting

[Cluster - etcd backup & restore](https://kubernetes.io/docs/tasks/administer-cluster/configure-upgrade-etcd/#backing-up-an-etcd-cluster)

[Cluster - kubelet config](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/kubelet-integration/#workflow-when-using-kubeadm-init)

[Cluster - Upgrading kubeadm clusters](https://kubernetes.io/docs/tasks/administer-cluster/kubeadm/kubeadm-upgrade/)

## 11. Volumes

[Volumes - StorageClass](https://kubernetes.io/docs/concepts/storage/_print/#the-storageclass-resource)

[Volumes - emptydir](https://kubernetes.io/docs/concepts/storage/volumes/#emptydir)

[Volumes - hostpath](https://kubernetes.io/docs/concepts/storage/volumes/#hostpath)

[Volumes - pod volume set - readonly](https://kubernetes.io/docs/concepts/storage/volumes/#projected)

[Volumes - PV and NFS exam](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistent-volumes)

[Volumes - PV (type: hostpath)](https://kubernetes.io/docs/tasks/configure-pod-container/configure-persistent-volume-storage/#create-a-persistentvolume)

[Volumes - create PV,PVC,POD](https://kubernetes.io/docs/tasks/configure-pod-container/configure-persistent-volume-storage/)

[Volumes - PVC (pod add pvc)](https://kubernetes.io/docs/concepts/storage/_print/#persistentvolumeclaims)

## 12. 기타

[스토리지로 PV를 사용하도록 파드 설정](https://kubernetes.io/ko/docs/tasks/configure-pod-container/configure-persistent-volume-storage/)

[Kubectl Reference Docs](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands)

[JSONPath Support](https://kubernetes.io/docs/reference/kubectl/jsonpath/)

[kubectl Cheat Sheet](https://kubernetes.io/docs/reference/kubectl/cheatsheet/)

[Creating a cluster with kubeadm | Kubernetes](https://kubernetes.io/docs/setup/production-environment/tools/kubeadm/create-cluster-kubeadm/)

[kubeadm 설치하기 | Kubernetes](https://kubernetes.io/ko/docs/setup/production-environment/tools/kubeadm/install-kubeadm/)

[Search Kubernetes](https://kubernetes.io/search/?q=)