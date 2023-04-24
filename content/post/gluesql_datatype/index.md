---
title: "[GlueSQL] 데이터 타입을 추가하며"
description: 
date: 2023-04-11T13:19:22+09:00
image: 
math: 
license: 
hidden: false
comments: true
draft: true
---

## GlueSQL이란?

GlueSQL 이란 Rust로 작성이 되어있는 오픈소스 데이터베이스 프로젝트 입니다. 개인적으로 생각하는 GlueSQL의 매력 포인트는 단연코 AST Builder라고 할 수 있습니다. AST 는 Abstact Syntax Tree 의 약어로 컴파일러에서 널리 사용되는 자료구조입니다. 이는 AST가 프로그램의 구조를 표현하는 프로퍼티이기 때문입니다. AST는 일반적으로  컴파일러의 구문분석에 대한 결과물 입니다. 따라서 프로그래밍언어가 컴파일이 되는 단계에서 구문분석을 거쳐 AST를 생성합니다. GlueSQL 에서는 AST Builder 라고 불리는 쿼리 빌더가 존재합니다. 상용화되어있는 데이터베이스들은 SQL함수만을 지원하기 때문에 ORM 이라고 하는 것을 이용하여 메서드로  데이터베이스를 조작할 수 있습니다. ORM을 사용하는 경우 메서드가 SQL문으로 변환된 후 AST로 변환되는 과정을 거칩니다. 하지만 저희 GlueSQL의 AST Builder는 이름에서부터 알 수 있듯이 AST 를 만들어주는 함수들 입니다. 


## 어떤 기여를 하였는가?

이 기여를 하기 이전 GlueSQL은 막 Unsinged Integer를 추가하기 시작한 시점이었다. 당시 민식님께서 U8 데이터 타입을 추가해 주신 시점이었다. 그 당시만 해도 데이터 타입에 대한 proc macro가 없었기 때문에 하나의 데이터 타입을 추가하기 위해서는 방대한양의 테스트 코드가 필요하였다.

## 배운점
