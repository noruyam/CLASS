# JSTL이란?
- JSP Standard Tag Library의 약자로 JSP 표준 라이브러리이다.
  - JSP에서 자주 사용하는 기능(반복문과 조건문, 데이터 표현 등)을 미리 구현해 놓은 커스텀 태그 라이브러리 모음이다.
  - JSTL은 EL을 사용하여 표현한다.
- Apache 재단에서 진행하는 custom tag library 프로젝트
  - 스크립트 릿으로 작성해야할 로직을 태그로 대신 처리 가능
   

---   

# EL 이란? 
- Expression Language의 약자
- JSP 2.0에서 새롭게 추가된 스크립트 언어
- 기존의 Script tag의 표현식(<%= 정보 %>) tag에서 업그레이드된 버전 ( ${ 정보 } )
- [ 주요 특징 ]
  1. JSP 속성영역 (request,  response, session, application) 저장된 속성 객체의 property를 출력한다
  2. 리터럴 데이터, 다양한 연산결과 출력이 가능하다
  3. JSTL과 연동이 가능하다

[참고](https://creamilk88.tistory.com/117)
