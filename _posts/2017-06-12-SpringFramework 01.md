---
title: SpringFramework 01~03
layout: post
category: blog
---
#### **01. DI(Dependency Injection, 의존성 주입)**
> 스프링에서의 DI의 의미 : 부품들을 생성하고, 제품을 조립해주는 공정과정을 대신해 주는 라이브러리	
>제품 | 스프링
>----|----
>주문서|설정파일(XML)
>일반적인 순서의 공정|역방향 조립

#### **02.DI 설정**
* XML을 이용한 DI 설정

```xml
<?xml version="1.0" encoding="UTF-8"?>
	
	<!-- <bean>태그 : 생성할 객체 지정-->
	<bean id="빈 식별자" class="생성할 객체의 완전환 클래스 이름">
		<!-- <property >태그 : 프로퍼티 방식 설정 -->
		<property name="프로퍼티 이름">
			<value>프로퍼티 값</value>
		</property>
		
		<property name="프로퍼티 이름" ref="다른 빈 식별자" />
	</bean>

	<bean>
		<!-- <constructor-arg>태그 : 생성자 방식 설정-->
		<constructor-arg id="빈 식별자" class="생성할 객체의 완전한 클래스 이름">
			<value>인자값</value>
		</constructor-arg>
		<constructor-arg>
			<ref bean = "다른 빈 식별자"/>
		</constructor-arg>
	</bean>
</beans>
```

* JAVA코드를 이용한 DI 설정

```java
@Configuration // 클래스를 스프링 설정으로 사용함을 의미
public class Config{

	@Bean // 메서드의 리턴값을 빈 객체로 사용함을 의미
	public User user(){
		return new User("madvirus","qwer"); //생성자에 값 직접 전달
	}
	
	@Bean
	public AuthFailLogger authFailLogger(){
		AuthFailLogger logger = new AuthFailLogger();
		logger.setThreshold(2); //프로퍼티에 값 전달
		return logger;
	}
}
```


#### **03.스프링 컨테이너 종류**
> 스프링은 BeanFactory와 ApplicationContext의 두 가지 타입의 컨테이너를 제공
> ![Alt text](/uploads/beanFac.png)

> BeanFactory : 스프링 설정 파일(applicationContext.xml)에 등록된 빈(bean) 객체를 생성하고 관리하는 가장 기본적인 컨테이너 기능 만 제공
> 
>  ApplicationContext : 트랜잭션 관리나 메시지 기반의 다국어 처리 등 다양한 기능을 지원
>  ![Alt text](/uploads/appContext.png)

#### **04. Spring Bean Life Cycle 관리방법**
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
<bean id="BBean" class = "com.spring.bean.BSimpleClass" init-method="init" destroy-method="destory"/>
```

* 어노테이션 지정

```java
public class BsimpleClass{
	
	@PostContruct
	public void init(){
		BEAN 생성 시 호출
	}
	
	@PreDestory
	public void destroy(){
		BEAN 소멸 시 호출
	}	
}
```

#### **05. Spring Bean 범위(scope)**

* 빈 태그의 스코프 속성 값
>singleton : 스프링 컨테이너에 한개의 bean객체만 존재한다.
>prototype : bean을 사용할 때 마다 객체를 생성한다.
>requesthttp : 요청마다 객체를 생성한다(WebApplicationContext에서만 적용가능)
>sessionhttp : 세션마다 객체를 생성한다(WebApplicationContext에서만 적용가능)
>global-session : 글로벌 http세션에 대해 객체를 생성한다.(포틀릿을 지원하는 Context에서만 적용가능)


* 사용방법

```java
import org.springframework.context.annotation.Scope;

@Bean
@Scope("singleton")
public CoonPool1 pool1(){
	return new ConnPool1();
}
```

```xml
<bean id="pool1" class="net.madvirus.chap03.ConnPool1" Scope="singleton"/>
```



