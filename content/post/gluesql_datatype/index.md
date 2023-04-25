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

GlueSQL 이란 Rust로 작성이 되어있는 오픈소스 데이터베이스 프로젝트 입니다. 
GlueSQL은 어디에든 붙일수 있는 데이터 베이스라는 이념아래 개발이되고 있는 큰 포용성을 가진 데이터베이스 입니다. 
개인적으로 생각하는 GlueSQL의 매력 포인트는 단연코 AST Builder라고 할 수 있습니다. 
AST 는 Abstact Syntax Tree 의 약어로 컴파일러에서 널리 사용되는 자료구조입니다.이는 AST가 프로그램의 구조를 표현하는 프로퍼티이기 때문입니다. 
AST는 일반적으로  컴파일러의 구문분석에 대한 결과물 입니다. 따라서 프로그래밍언어가 컴파일이 되는 단계에서 구문분석을 거쳐 AST를 생성합니다. 
GlueSQL 에서는 AST Builder 라고 불리는 쿼리 빌더가 존재합니다. 현재 상용화되어있는 많은 데이터베이스들은 SQL함수만을 지원하기 때문에 ORM 이라고 하는 것을 이용하여 메서드로 데이터베이스를 조작해야 합니다.
ORM을 사용하는 경우 메서드가 SQL문으로 변환된 후 AST로 변환되는 과정을 거치는것이 일반적입니다. 하지만 저희 GlueSQL의 AST Builder는 이름에서부터 알 수 있듯이 AST 를 만들어주는 함수들 입니다. 따라서 타 쿼리빌더가 필요한 AST가 만들어지기까지 걸리는 단계를 하나 생략함으로써 오는 성능 향상이 있다고 생각합니다.
또한 GlueSQL의 AST 빌더는 러스트 함수로 SQL함수를 실행시킬 수 있으며 각 노드들이 FSM 구조를 가지며 다음에 올 수 있는 Node들을 인지하고 있기 때문에 Compile 타임에서 해당 AST Builder로 정의된 SQL 함수가 구조적으로 문제가 없는지 확인할 수 있습니다. 
추가로 러스트의 강력한 Compiler의 도움으로 SQL이 익숙하지않은 사람들에게도 올바른 쿼리를 작성할 수 있도록 도움을 줍니다. 

## 어떤 기여를 하였는가?

저는 GlueSQL에 Unsigned Integer 데이터 타입을 추가하는 기여를 하였습니다. 제가 기여를 시작할 당시 GlueSQL에는 U8 데이터 타입만 구현이 되어 있었습니다.
이 기여의 시작점은 단연코 쉽지 않았습니다. 여러 데이터 타입을 포용할 수 있어야 한다면 type casting에 대한 명확한 기준이 있어야 했습니다. 따라서 해당 프로젝트의 콜라보레이터분들과 많은 상의를 거쳐 다음과 같은 type casting기준을 세웠습니다.

>cast right-hand element into left-hand element type in case of arithmetics between INTEGER types

타입이 다른 2개의 정수형들의 사칙연산에서는 좌항을 기준으로 캐스팅 하는것으로 기준을 세운 이후에는 TDD를 지향하는 프로젝트이기 때문에 테스트 케이스들을 작성해 나아가기 시작했습니다. 
U16 데이터 타입을 implement 할 당시에는 proc macro가 없었기 때문에 하나의 데이터 타입을 테스트 하기 위해서 수많은 양의 테스트 코드를 작성을 해야했습니다. 
이 때문에 테스트 케이스들을 누락시키거나, 세워둔 type casting 기준에 벗어나는 테스트 케이스를 작성한 적 도 있습니다.
하지만 U16 데이터 타입을 작업한 이후 일괄 작업을 



## 배운점
