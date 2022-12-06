# Jenkins

### 1. 설치 - 참고(https://hhseong.tistory.com/198)
해당 블로그처럼 설치하려했으나 본 프로젝트는 jdk 1.8로 진행해야하는 프로젝트였기에 
Jenkins 최신 버전인 2.357은 java8을 지원하지 않아 유효하지 않은 java version 이라며 start가 되지 않았다.

그래서 다시 참고한 블로그 (https://algo79.tistory.com/1162)

보면 jenkins.war를 교체하여 다운그레이드 하려는데 해당 방법으로 다운되지 않아서 
java8을 지원하는 jenkins 2.346-1.rpm 파일을 직접 다운받아서 설치진행하였다.

정상작동된다. 이후는 블로그 참조하여 

