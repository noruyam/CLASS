# Git

## commit 초기화 방법
https://korband.tistory.com/45?category=905612   
해당 방법은 프로젝트를 로컬에 받아서 기존 .git을 삭제해버리고 새로운 브랜치로 로컬에 받아놓은 프로젝트를 처음 커밋하는것처럼 하는 방법이다.   
해당 방법처럼하게되면 브랜치가 분리되어 원하는대로 초기화가 되지 않았다.   
기존에 있던 브랜치가 디폴트로 잡혀있었기 때문이었다.   
그래서 다음 방법을 참고하여 브랜치 바꿔서 삭제해버렸다.   
[참고1](https://velog.io/@khh180cm/git-repository-master-%EC%82%AD%EC%A0%9C)   
or   
[참고2](https://wakestand.tistory.com/667)

해당 방법으로 초기화 해버리면 잔디밭이 다 없어져버린다...............
다행히 .git폴더를 백업해놔서 브랜치를 복구시킬수 있었다.
다음 글을 참고하였다.
https://www.freecodecamp.org/korean/news/git-push-to-remote-branch/


## git 최초 등록 방법
[참고](https://kitty-geno.tistory.com/141)
해당 블로그 글 참고하여 git 에 해당 교육 프로젝트를 새로 등록했으나 또 브랜치가 갈려버렸다...
그래서 브랜치 디폴트값을 변경해주고 github에서 생성한 브랜치를 삭제시켰다.
올릴때 브랜치를 바꿔서 올려야하는건지 아니면 프로젝트를 생성할때 레파지토리를 같이 생성해야하는건지 모르겠다.

문제점
1. 로컬에 프로젝트를 먼저 생성하고 github에 올리려고하면 -> 실패
2. github에 먼저 레파지토리를 생성하고, 로컬에 프로젝트를 생성해서 올리면 브랜치가 갈려버림

나중에 공부가 필요할듯하다.

## Git 커밋 취소(reset), 커밋 되돌리기(revert), 덮어쓰기(amend)
[참고1](https://www.lainyzine.com/ko/article/git-reset-and-git-revert-and-git-commit-amend/)
[참고2](https://gmlwjd9405.github.io/2018/05/25/git-add-cancle.html)

커밋을 취소하고 remote에 다시 강제 push하는 작업이 있기 때문에 주의해야한다.

## git 개인 파일 올리기
[참고](https://2vup.com/git-first-commit/)   
블로그 참고하여 개인 파일을 올리다가 레파지토리가 private여서 밑에 보이는 오류가 발생했다.
```
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
```
ssh키가 등록되어있지않아서 발생한 오류이다.
그래서 다음 블로그를 참고하여 ssh 키를 생성하고 등록해준다.   
[참고](https://ifuwanna.tistory.com/304)

`-keygen -t rsa -C “깃허브로그인메일"`

보통 경로는 밑에 경로에 생성된다.

`C:\Users\유저이름\.ssh\id_rsa.pub`


꼭 .pub 파일을 메모장으로 열어 key를 github에 등록해야한다.

https://github.com/settings/keys 로 접속하면 등록할 수 있다.


## git 한 레파지토리에 여러 프로젝트 올리기
[참고](https://jie0025.tistory.com/59)
1. git 설치는 필수적
2. cmd를 열어서
3. 올리고 싶은 프로젝트들이 존재하는 폴더로 이동
4. git init
5. git add ./폴더이름 
폴더이름을 하나씩 add 해주어야한다.
6. git commit -m "message"
7. git remote add origin 레파지토리주소
8. git push -u origin master

정상적으로 올라갔는지 확인하면 끝!인데 해당 블로그를 그대로 복붙해서 올리다가 아래와 같은 오류가 발생했다.

```html
git pull master
fatal: 'master' does not appear to be a git repository
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
```
이유는 위에 7번에서 add해줄때 블로그에서 그대로 복붙해서 오타를 넣어버렸다.   
origine 이라고 add해놓고 8번에서는 origin 으로 push하려 했기 때문에 에러가 발생한것.   

다음 블로그를 참고해서 주소를 해제하고 재연결했다.   
[참고](https://jjunii486.tistory.com/153)

1. git remote -v 
2. git remote remove 1에서나온이름
3. git remote add origin 레파지토리깃주소
4. git push -u origin master
