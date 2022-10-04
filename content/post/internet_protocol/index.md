---
title: "[모든 개발자를 위한 HTTP 웹 기본 지식]1.2인터넷 프로토콜(IP)"
description: 
date: 2022-08-17T11:34:53+09:00
image: 
math: 
license: 
hidden: false
comments: true
draft: false
series: ["모든 개발자를 위한 HTTP 웹 기본 지식"]
tags: ["HTTP","Spring","김영한"]
categories: "HTTP"
slug: "internet_protocol"
---

복잡한 인터넷망에서 Message를 보내야 한다면 최소한의 규칙이 있어야 한다. 이 규칙은 인터넷 프로토콜(IP)를 통하여 이루어진다.

## 인터넷 프로토콜 (IP)

### IP 주소 부여

Interent Protocol은 우선 IP 주소를 부여함으로써 시작이 된다. IP 주소가 없다면 IP는 당연하게도 동작할 수 없기 때문에 주소를 부여받아야 한다.

### IP의 역할

인터넷 프로토콜은 지정한 IP 주소로 데이터를 `Packet` 단위로 나누어 전송을 하는 역할을 한다.



### IP Packet

IP Packet에는 보낼 Message 이외에 `Client`의 IP 주소, `Server`의 IP 주소 와 같은 여러 정보들을 함께 포함하고 있다.  
위 정보를 담고 있는 IP `Packet`들은 인터넷망에 던져지며 인터넷 프로토콜의 규약을 따르고 있는 노드들이 목적지까지 `Packet`을 안전하게 전송시킨다.  인터넷망은 매우 복잡하기에 `Client`가 `Packet`을 전송할 때 사용된 path들을 `Server`의 response message가 똑같이 사용하지 않을 수 도 있다.

### IP의 한계

- Internet Protocol은 Packet을 받을 대상이 없거나, 서비스 불능 상태여도 `Packet`을 전송한다.  
  따라서 Interent Protocol은 `비 연결성`이라는 단점을 가지고 있다.
  
- Internet Protocol은 `Packet`이 누락되거나 순서대로 도착하지 않을 수 있다는 `비 신뢰성`이라는 단점을 가지고 있다.  

- Internet Porotocol은 같은 IP 주소를 사용하고 있는 서버와 통신하고 있는 애플리케이션이 여러 개라고 한다면 애플리케이션을 구분할 수 없다.

위와 같은 문제들은 `TCP/UDP`를 통하여 해결될 수 있다.

> 본 글은 김영한 님의 [모든 개발자를 위한 HTTP 웹 기본 지식](https://www.inflearn.com/course/http-%EC%9B%B9-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC/dashboard)을 보고 정리한 글입니다.