# thymeleaf

[thymeleaf 공식 사이트](https://www.thymeleaf.org/)   
[스프링 공식 튜토리얼](https://spring.io/guides/gs/serving-web-content/)   
[스프링부트 메뉴얼](https://docs.spring.io/spring-boot/docs/2.3.1.RELEASE/reference/html/spring-boot-features.html#boot-features-spring-mvc-template-engines)

# 시작하기
1. 라이브러리 추가
   * `Gradle` - build.gradle
    ```
    implementation 'org.springframework.boot:spring-boot-starter-thymeleaf' 
    ```   
   * `Maven` - pom.xml
    ```
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-thymeleaf</artifactId>
    </dependency>
    ```
위 설정을 추가 후 빌드하면 application.properties에 아래 코드가 자동으로 추가된다.
디폴트 설정을 원하지 않는다면 직접 수정해도 된다.


2. thymeleaf를 사용할 html에 다음 태그를 추가
```html
<html xmlns:th="http://www.thymeleaf.org">
```
ex)
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
표현	설명	예제
@{ ... }	URL 링크 표현식	th:href="@{/css/bootstrap.min.css}"
		th:href="@{/{itemId}/edit(itemId=${item.id})}"
| ... |	리터럴 대체	th:text="|Hi ${user.name}!|"
		(= th:text="'Hi '+${user.name}+'!'"
${ ... }	변수	th:text=${user.name}
th:each	반복 출력	<tr th:each="item: ${items}">
		  <td th:text="${item.price}">100</td>
		</tr>
*{ ... }	선택 변수	<tr th:object="${items}">
		  <td th:text="*{price}">100</td>
		</tr>
#{ ... }	메시지. properties 같은 외부 자원에서 코드에 해당하는 문자열 get.	th:text="#{member.register}"
![image](https://user-images.githubusercontent.com/51654048/200482883-a4ad2b04-14ce-408d-b860-690b4ce9e370.png)


1. 반복과 출력

``` html
<tr th:each="member : ${members}">
 <td th:text="${member.id}"></td>
 <td th:text="${member.name}"></td>
</tr>
```

