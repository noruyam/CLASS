# thymeleaf 란?

### 템플릿 엔진(Template Engine)
- 웹 서비스를 만들 떄에는 서버의 데이터와 정적자원(html, css, image)을 조합해야 한다.
- 서버에서 데이터를 보내 웹 서비스를 만드는 방법에는 크게 2가지가 있다.SPA(Single Page Application)
- 최초 한번 전체페이지를 다 불러오고 응답데이터만 페이지 특정부분 렌더링.SSR(Server Side Rendering)
- 전통적인 웹 애플리케이션 방식. 요청시마다 서버에서 처리한 후 새로고침으로 페이지에 대한 응답.

보통 자바에서 웹 개발시 JSP(Java Server Page)를 이용하여 진행한다.   
JSP를 사용하면 <% %>형태의 스크립트릿을 사용하여 개발한다.   
그러나 이 방식은 스크립트릿과 HTML이 혼재된 상태가 되고 HTML 태그의 반복적인 사요애으로 인해 수정하기 어려운 상황이 된다.   
이러한 상태를 해결할 수 있는 것이 템플릿 엔진이다.

#### 템플릿 엔진이란 HTML(Markup)과 데이터를 결합한 결과물을 만들어 주는 도구이다.   
타임리프는 템플릿 엔진 중 하나로, Spring Boot에서는 JSP가 아닌 Thymeleaf 사용을 권장하고 있다.

[참고](https://myeongdev.tistory.com/20)
