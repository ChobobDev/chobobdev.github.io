---
title: "[GlueSQL] 데이터 타입을 추가하며"
description: "오픈소스 기여활동을 회고하며.."
date: 2023-04-11T13:19:22+09:00
image: "ferris.png"
math: 
license: 
hidden: false
comments: true
draft: false
series: ["우당탕탕! 좌충우돌 오픈소스 항해기"]
tags: ["GlueSQL","Rust","오픈소스","회고"]
categories: "GlueSQL"
slug: "gluesql_datatype"
---

## GlueSQL이란?

GlueSQL 이란 Rust로 작성이 되어있는 오픈소스 데이터베이스 프로젝트입니다.
GlueSQL은 레퍼런스 스토리지를 포함한 SQL 데이터베이스이기도 하지만, NoSQL 데이터베이스들이 지원하는 완전히 구조화되지 않은 데이터까지 동일한 SQL 인터페이스를 이용해서 접근할 수 있게 하며 다른 개발자들이 자신이 원하는 환경과 데이터에 SQL을 지원할 수 있게 하는 데이터베이스 프로젝트입니다.
개인적으로 생각하는 GlueSQL의 매력 포인트는 단연코 AST Builder라고 할 수 있습니다.
AST는 Abstact Syntax Tree의 약어로 컴파일러에서 널리 사용되는 자료구조입니다.이는 AST가 프로그램의 구조를 표현하는 프로퍼티이기 때문입니다.
AST는 일반적으로  컴파일러의 구문분석에 대한 결과물입니다. 따라서 프로그래밍언어가 컴파일되는 단계에서 구문분석을 거쳐 AST를 생성합니다.
GLUE SQL 에서는 AST Builder라고 불리는 쿼리 빌더라 존재합니다. 현재 상용화되어 있는 많은 데이터베이스는 SQL 함수만을 지원하기 때문에 ORM 이라고 하는 것을 이용하여 메서드로 데이터베이스를 조작해야 합니다.
ORM을 사용하는 경우 메서드가 SQL문으로 변환된 후 AST로 변환되는 과정을 거치는것이 일반적입니다. 하지만 저희 GlueSQL의 AST Builder는 이름에서부터 알 수 있듯이 AST를 만들어 주는 함수들입니다. 따라서 타  쿼리 빌더가 필요한 AST가 만들어지기까지 걸리는 단계를 하나 생략함으로써 오는 성능 향상이 있다고 생각합니다.
또한 GlueSQL의 AST 빌더는 러스트 함수로 SQL 함수를 실행시킬 수 있으며 각 노드가 FSM 구조를 가지며 다음에 올 수 있는 Node들을 인지하고 있기 때문에 Compile 타임에서 해당 AST Builder로 정의된 SQL 함수가 구조적으로 문제가 없는지 확인할 수 있습니다.
추가로 러스트의 강력한 Compiler의 도움으로 SQL이 익숙하지 않은 사람들에게도 올바른 쿼리를 작성할 수 있도록 도움을 줍니다.

## 어떤 기여를 하였는가?

저는 GlueSQL에 Unsigned Integer 데이터 타입을 추가하는 기여를 하였습니다. 제가 기여를 시작할 당시 GlueSQL에는 U8 데이터 타입만 구현이 되어 있었습니다.
이 기여의 시작점은 단연코 쉽지 않았습니다. 여러 데이터 타입을 포용할 수 있어야 한다면 type casting에 대한 명확한 기준이 있어야 했습니다. 따라서 해당 프로젝트의 콜라보레이터분들과 많은 상의를 거쳐 다음과 같은 type casting기준을 세웠습니다.

>cast right-hand element into left-hand element type in case of arithmetics between INTEGER types

타입이 다른 2개의 정수형의 사칙연산에서는 좌항을 기준으로 캐스팅 하는 것으로 기준을 세운 이후에는 TDD를 지향하는 프로젝트이기 때문에 테스트 케이스들을 작성해 나아가기 시작했습니다.
U16 데이터 타입을 implement 할 당시에는 `proc_macro`가 없었기 때문에 하나의 데이터 타입을 테스트하기 위해서 수많은 양의 테스트 코드를 작성을 해야 했습니다.
이 때문에 테스트 케이스들을 누락시키거나, 세워둔 type casting 기준에 벗어나는 테스트 케이스를 작성한 적도 있습니다.
하지만 다른 개발자분의 도움으로 type casting을 테스트 케이스들을 `proc_macro` 로 모두 대체하여 더 일관성 있고 자동화된 테스트 코드를 유지할 수 있게 되었으며, 놓치는 테스트 케이스가 없어 테스트 커버리지를 증가시킬 수 있었습니다.
`proc_macro`는 러스트의 컴파일 타임에 실행되는 매크로이므로, 런타임에 테스트 케이스를 생성하는 것보다 효율적이라는 장점을 가집니다. 
이를 통해 테스트 케이스 작성 시간을 줄이고, 일관성 있고 반복 가능한 테스트 코드를 생성할 수 있었습니다.

U16 타입을 추가한 이후, 프로젝트 메인테이너분께서 이번 PR에는 나머지 Unsigned Integer들을 한번에 추가해 보자고 제안을 해주셔서 U32, U64, U128 의 데이터 타입들을 한번에 모두 추가하게 되었습니다.
제가 작업을 하고 있던 사이 새로운 데이터 타입들도 추가되어 merge conflict를 해결하던중 U128 부분에서 문제가 발생하였습니다.
기존에 `try_from()` 함수에 잘못 분기를 타고 있던 UUID 데이터 타입을 수정함으로써 U128테스트케이스가 fail 하던 버그를 해결할 수 있었습니다. 


## 배운점

해당 PR을 통해 저는 Unsigned Integer의 중요함을 배웠으며 `proc_macro`가 가지고 오는 좋은점을 알 수 있었습니다.
추가로 U128과 관련한 버그를 수정하면서  RUST_BACKTRACE 를 사용하여 디버깅 하는 방법을 배울 수 있던 좋은 PR 이었습니다. 
해당 PR을 해결하기까지 오랜 시간이 걸린 만큼, 더 큰 기쁨으로 보상을 받은것 같습니다. 
PR을 한단계 한단계 해결해 나아가면서 힘들었었지만, 해당 PR을 포기하지 않고 머지를 시키며 기여를 하는것에 있어 존재하던 두려움이 사라진것 같습니다.
앞으로도 오픈소스에 기여하며 다른 개발자들과 더 많은 상호작용을 하고 싶습니다.

해당 회고의 PR들은 다음과 같습니다.   
[U16 타입 추가](https://github.com/gluesql/gluesql/pull/844)   
[I16 타입에 macro 설정](https://github.com/gluesql/gluesql/pull/940)   
[U128 try_from() 버그 수정 ](https://github.com/gluesql/gluesql/pull/1134)   
[U32, U64 그리고 U128 타입 추가하기](https://github.com/gluesql/gluesql/pull/1019)   
[TryFrom<&Value> for Decimal 유닛 테스트 추가하기](https://github.com/gluesql/gluesql/pull/1139)   