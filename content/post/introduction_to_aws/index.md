---
title: "[AWS] AWS 용어 및 개념 정리 "
description: "AWS 를 사용하면서 접하게될 용어 정리" 
date: 2023-11-08T10:44:33+09:00
image: "thumbnail.png"
math: 
license: 
hidden: false
comments: true
draft: true
series: ["DevOps"]
tags: ["DevOps","AWS"]
categories: "DevOps"
slug: "Introduction_to_aws"
---

## AWS란?
AWS는 `Amazon Web Service`의 약자로 아마존 닷컴이 제공하는 클라우드 컴퓨팅 서비스의 모음이다.   
AWS가 제공하는 서비스중에는 `EC2`,`S3`,`RDS` 등이 있다.   
해당 글에서는 `AWS`에서 알아야할 몇가지 용어들을 정리해보겠다.   

### VPC란?
`VPC`는 `Virtual Private Network`로 `AWS`에서 제공하는 가상의 개인 네트워크 서비스이다.   
이를 통해 사용자는 개인의 가상네트워크 환경을 구축하여 AWS의 리소스를 안전하게 실행시킬 수 있다.   
IP 주소범위, 서브넷 생성, 라우트 테이블 및 네트워크 게이트웨이 구성등을 통해 자신이 원하는 네크워크 환경을 자유롭게 구성할 수 있게해준다.   

### Subnet이란?
`Subnet`이란 `VPC`내에서 IP 주소 범위를 나누는 서브넷워크를 말한다.   
`Subnet`을 이용하면 네트워크를 세분화하여 효율적으로 관리할 수 있다.   


### Security Group이란?
`AWS`에서 제공하는 가상 방화벽으로, 인스턴스에 개한 인바운드 및 아웃바운드 트래픽을 제어 한다.   
사용자는 특정 IP주소 또는 IP주소 법위에서 오는 트래픽을 허용하거나 거부할 수 있다.   

### EC2
`EC2`는 `Elastic Compute Cloud` 의 약자로 사용자가 원하는 용량과 시간에 따라 컴퓨팅 파워를 제공하는 서비스 이다.   
사용자는 필요에 따라 가상 서버의 스펙을 선택하고, 서버를 살행하거나 중지할 수 있다.   


### S3
`S3`는 `Simple Storage Service`로 인터넷 기반의 스토리지 서비스로, 사용자는 언제든지 웹에서 원하는 양의 데이터를 저장하고 검색할 수 있다.   
또한, 데이터를 저장하고 검색할 수 있다. 또한, 데이터를 안전하게 보호하기 위한 다양한 기능을 제공한다.   


