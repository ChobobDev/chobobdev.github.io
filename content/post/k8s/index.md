---
title: "[DevOps] Kubernetes 기본 개념" 
description: "K8s 와 container orchestration"
date: 2023-10-23T20:44:05+09:00
image: "k8s.png" 
math: 
license: 
hidden: false
comments: true
draft: false
series: ["K8s"]
tags: ["K8s","Container","Orchestration"]
categories: "K8s"
slug: "K8s"
---

## Kubernetes란?

`Kubernetes`는 컨테이너 오케스트레이션 (`container orchestration`)을 위한 오픈소스 플랫폼이다.   
이는 클라우드 환경에서 컨테이너화된 애플리케이션의 배포, 스케일링, 그리고 관리를 효율적으로 수행하며, 서비스의 가용성을 높여주는 동시에 복잡한 컨테이너 운영 과정을 간소화해준다.   

## Kubernetes 기본 개념 
### Pod
`pod`란 `K8s`의 가장 작은 배포단위이며, 컨테이너 집합을 나타내는 개념이다.   
같은 Pod 내의 컨테이너들은 동일한 네트워크와 스토리지 공간을 공유하며, 서로 밀접하게 연관된 기능을 수행합니다.   
여러 컨테이너가 한 Pod에서 실행되는 이유는 서비스를 구성하는 여러 컴포넌트가 함께 움직여야 하는 경우를 처리하기 위함이다.   

### Deployment
`Deployment`는 `Pod`의 생성과 스케일링을 관리하고, `Pod`에 대한 업데이트 전략을 지정하는 API 오브젝트이다.   
`Deployment`를 통해 우리는 원하는 상태(desired state)를 정의할 수 있으며, Kubernetes 시스템은 현재 상태를 원하는 상태로 유지하기 위해 작동한다.   
`Deployment`는 `ReplicaSet`을 사용하여 `Pod`들의 복제본(replicas)을 관리한다.   

### Service
`Service`는 로직적인 집합체인 Pod들에 접근할 수 있는 일관된 방법을 제공한다.   
`Service`는 특정 포드 세트와 클라이언트 사이에 추상화 계층을 추가하여, 클라이언트가 직접 포드에 연결하지 않고 서비스를 통해 연결할 수 있게 한다.    
`ClusterIP` (클러스터 내부에서만 접근 가능), `NodePort` (각 노드의 IP와 정적 포트를 통해 외부 접근 가능), `LoadBalancer` (외부 로드 밸런서 제공) 등 다양한 타입의 서비스가 있다.   

### Ingress
`Ingress`는 클러스터 외부에서 내부 서비스로 HTTP와 HTTPS 경로를 노출시켜주어 외부 트래픽 라우팅 역할을 한다.
`Ingress Controller`와 함께 사용되며, 주요 기능으로 로드발란싱, SSL 종료 및 이름 기반 가상 호스팅 등이 있다.   

### Namespace
`Namespace`는 하나의 물리적인 클러스터 안에서 가상의 클러스터, 즉 별도의 독립적인 환경을 제공한다.   
`Namespace`를 사용하면 리소스들을 그룹화하여 특정 유저 또는 팀 간에 분리할 수 있다.   
이를 통해 하나의 클러스터를 여러 사용자나 프로젝트 간에 격리시켜 관리할 수 있다.

### Node
Worker Node는 `Kubernetes` 클러스터에서 실제 작업(즉, 애플리케이션 컨테이너 실행)을 수행하는 서버이다.   
각 노드는 `Kubele`t이라는 에이전트가 실행되며, Master와 통신하고 `Pod`들을 관리한다.   

### Control Plane
`Control Plane`은 Kubernetes 클러스터를 제어하는 구성 요소 집합이다.    
`Control Plane`의 주요 역할은 전체 클러스터의 상태를 관리하고, 사용자와 시스템 상호작용에 응답하는 것이다.    
`Control Plane`은 `API Server`, `Scheduler`, `Controller Manager` 등으로 구성된다.  

# 맺으며
다음 글에서는 위 개념들을 `Kubernetes`와 같은 `container orchestration`툴인 `minikube`를 활용하여 짚어볼 예정이다.   

