---
title: SpringFramework 01 
layout: post
category: blog
---
## **Chapter 01** 


## **Chapter 02** 
#### 01. DI(Dependency Injection, 의존성 주입)
> 스프링에서의 DI의 의미
> - 부품들을 생성하고, 제품을 조립해주는 공정과정을 대신해 주는 라이브러리	
>제품 | 스프링
>----|----
>주문서|설정파일(XML)
>일반적인 순서의 공정|역방향 조립

#### 02.스프링 컨테이너 종류
> 스프링은 BeanFactory와 ApplicationContext의 두 가지 타입의 컨테이너를 제공
> ![BeanFactory와 ApplicationContext의 관계](/uploads/beanFac.PNG)

> BeanFactory : 스프링 설정 파일(applicationContext.xml)에 등록된 빈(bean) 객체를 생성하고 관리하는 가장 기본적인 컨테이너 기능 만 제공
>  ApplicationContext : 트랜잭션 관리나 메시지 기반의 다국어 처리 등 다양한 기능을 지원
>  ![ApplicationContext의 계층구조](/uploads/appContext.PNG)