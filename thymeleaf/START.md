# thymeleaf

[thymeleaf 공식 사이트](https://www.thymeleaf.org/)   
[스프링 공식 튜토리얼](https://spring.io/guides/gs/serving-web-content/)   
[스프링부트 메뉴얼](https://docs.spring.io/spring-boot/docs/2.3.1.RELEASE/reference/html/spring-boot-features.html#boot-features-spring-mvc-template-engines)

# 시작하기
1. `Gradle` - build.gradle   
```
implementation 'org.springframework.boot:spring-boot-starter-thymeleaf' 
```   
2. `Maven` - pom.xml   
```
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-thymeleaf</artifactId>
</dependency>
```   
> 2. 

> 예시
resources/templates/hello.html

``` html
<!DOCTYPE HTML>
<html xmlns:th="http://www.thymeleaf.org">
<head>
 <title>Hello</title>
 <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
</head>
<body>
 <p th:text="'안녕하세요. ' + ${data}" >안녕하세요. 손님</p>
</body>
</html>
  ```

> 문법
1. 반복과 출력
``` html
<tr th:each="member : ${members}">
 <td th:text="${member.id}"></td>
 <td th:text="${member.name}"></td>
</tr>
```

