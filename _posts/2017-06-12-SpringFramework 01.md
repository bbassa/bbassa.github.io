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
> ![Alt text](/uploads/beanFac.png)

> BeanFactory : 스프링 설정 파일(applicationContext.xml)에 등록된 빈(bean) 객체를 생성하고 관리하는 가장 기본적인 컨테이너 기능 만 제공
>  ApplicationContext : 트랜잭션 관리나 메시지 기반의 다국어 처리 등 다양한 기능을 지원
>  ![Alt text](/uploads/appContext.png)

## **Chapter 03** 
#### 01. Spring Bean Life Cycle 관리방법
> **InitializingBean** : Interface를 구현하면 Spring Bean생성과 properties의존성 주입 후 콜백 afterPoropertiesSet()을 호출
> **DispoableBean** : Interface를 구현하면 Spring Bean소멸 전 콜백 destroy()를 호출

* 인터페이스 구현
```java
public class SimpleClass implements InitializingBean, DisposableBean{

	public void afterPoropertiesSet() throws Exception{
		BEAN 생성 시 호출
	}

	public void destroy() throws Exception{
		BEAN 소멸 시 호출
	}
}
```
* Bean 정의시 메소드 지정
```xml
<bean id="BBean" class = "com.spring.bean.BSimpleClass" init-method="init" destroy-method="destory"/>```

