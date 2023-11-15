---
title: "[모든 개발자를 위한 HTTP 웹 기본 지식]1.1 인터넷 통신"
description: 
date: 2022-08-16T14:41:42+09:00
image: "thumbnail.png" 
math: 
license: 
hidden: false
comments: true
draft: false
series: ["모든 개발자를 위한 HTTP 웹 기본 지식"]
tags: ["HTTP","김영한"]
categories: "HTTP"
slug: "internet_communication"
---

## 1 인터넷에서 컴퓨터 둘은 어떻게 통신을 할까?

만약 Client 와 Server가 둘이 바로 붙어 있는 상황이라고 가정한다면, 물리적 케이블 연결을 통해 통신을 이어 나갈 수 있다.

만약 Client 와 Server가 멀리 떨어져 있다고 한다면, 우리는 인터넷망을 거쳐 통신을 할 수 있다.  
인터넷망은 생각보다 복잡한 구조로 되어 있다. 인터넷망을 통한 통신은 해저 케이블이나 인공위성과 같은 node라고 불리는 중간 서버들을 거쳐 목적지에 도달한다.  
Message들은 이 복잡한 통신 단계를 거쳐 목적지에 안전하게 도착해야 한다, message들이 어떠한 규칙에 의해서 통신되는지 알기 위해서는 `IP(Internet Protocol)`에 대한 지식이 필요하다.  


> 본 글은 김영한 님의 [모든 개발자를 위한 HTTP 웹 기본 지식](https://www.inflearn.com/course/http-%EC%9B%B9-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC/dashboard)을 보고 정리한 글입니다.
