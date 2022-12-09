# Jenkins

### 1. 설치 - 참고(https://hhseong.tistory.com/198)
해당 블로그처럼 설치하려했으나 본 프로젝트는 jdk 1.8로 진행해야하는 프로젝트였기에 
Jenkins 최신 버전인 2.357은 java8을 지원하지 않아 유효하지 않은 java version 이라며 start가 되지 않았다.
Jenkins 완전 삭제가 필요했다. 

### 완전 삭제 방법
#### 1. jenkins stop   
    systemctl stop jenkins
#### 2. yum 삭제
    yum remove jenkins
#### 3. jenkins 삭제
    rm /etc/init.d/jenkins
    rm -rf /var/lib/jenkins
#### 4. 관련 파일 찾아내어 모두 삭제했다.
    find / -name jenkins

완전 삭제 후 다시 참고한 블로그 (https://algo79.tistory.com/1162)

보면 jenkins.war를 교체하여 다운그레이드 하려는데 해당 방법으로 다운그레이드가 되지 않아서 
java8을 지원하는 jenkins 2.346-1.rpm 파일을 직접 다운받아서 설치진행하였다.

이후는 블로그 참조하여 정상작동됐다.

### 2. svn 연결 - 참고(https://aljjabaegi.tistory.com/634)


