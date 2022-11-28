# JSTL

기본적으로 서버가 작동할 때

JAVA > JSTL > HTML > Javascript 순서로 동작한다.
웹 개발을 하다보면 서버에서 넘어온 값을 view에 뿌려줄 때 Javascript와 jstl을 혼용해야 할 때가 많다.

우선 jsp 상단에 해당 태그를 붙여주어야 사용가능
```jsp
<%@taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core"%>
```

잘못된 방법
jquery로 가져온 값을 jstl로 반복문을 돌리려는 건 실행순서상 에러가 발생한다.
```jsp
<c:forEach items="$("#list").val()" var="item1">
list1.push("${item1.name}");
list1.push("${item1.city}");
list1.push("${item1.age}");
</c:forEach>
```

올바른 방법
다만 스크립트가 로드되기 전부터 존재하는 el값은 스크립트에서 조작이 가능하다.
```jsp
var list = '<c:out value="${list}"/>';
```

간단하게 생각하면

- JSTL에선 Javascript값을 받을 수 없다
- Javascript에선 JSTL값을 받을 수 있다
