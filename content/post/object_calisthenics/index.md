---
title: "[OOP]객체지향 생활 체조 원칙(Object Calisthenics)"
description: 
date: 2022-10-02T00:07:23+09:00
image: 
math: 
license: 
hidden: false
comments: true
draft: true
series: ["OOP"]
tags: ["OOP","Java"]
categories: "OOP"
---

## 왜 이 글을 쓰게 되었는가

자바를 처음 접한 건 말장난 같지만 2016년 자바 섬이었다. Java 섬의 Jakarta 소재의 고등학교 재학 시절 나는 Computer Science라는 과목을 선택하여 공부하였었다.  
Java의 명성에 걸맞게 OOP에 대해 배웠었고 나는 스스로 OOP에 대해 알고 있다고 자부했었다.  
하지만 OOP에 대해 더 공부해 본 결과 내가 객체지향에 대하여 상당히 무지하였던 것을 깨달았다.  
오늘 이 글을 통해 새롭게 알게 된 객체지향 생활 체조 원칙에 대해 적어보려고 한다.

## 객체지향 생활 체조 원칙이란?
### 1. Use only one level of indentation per method
> 메서드 당 하나의 들여 쓰기만 사용한다.
하나의 메서드에서는 오직 한 가지의 일만 담당하도록 하는 것이 좋다. 만약 메서드가 nested 한 구조를 가지고 있다면 이는 여러 단계의 추상화가 이루어지고 있다고 볼 수 있으며 이는 하나 이상의 일을 한다는 뜻이다.  
애플리케이션의 단위가 작아질수록 재사용의 정도가 기하급수적으로 늘어날것이다.

만약 다음과 같은 코드가 존재한다고 한다면,
```java
class Coordinate {
    String Coordinate() {
        StringBuffer buf = new StringBuffer();
        for(int i = 0; i < 10; i++) {
            for(int j = 0; j < 10; j++)
                buf.append(data[i][j]);
                buf.append("\n" );
            }
        return buf.toString();
    }
}
```
```java
```

### 2. Don’t use the else keyword
> else 예약어를 사용하지 않는다.
### 3. Wrap all primitives and strings
> 모든 원시값과 문자열을 포장한다.
### 4. Use only one dot per line
> 한줄에 점을 하나만 찍는다.
### 5. Don’t abbreviate
> 축약하지 않는다.
### 6. Keep all entities small
> 모든 Entity들을 작게 유지한다
### 7. Don’t use any classes with more than two instance variables
> 2개 이상의 인스턴스 변수를 가진 클래스를 쓰지 않는다.
### 8. Use first-class collections
> 일급 Collection을 쓴다.
### 9. Don’t use any getters/setters/properties
> getter/setter/properties를 사용하지 않는다.