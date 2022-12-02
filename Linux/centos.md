# Linux centOS7 
1. 설치
  - https://devjaewoo.tistory.com/m/30

2. svn 설치
  - https://iamyourfavorite.tistory.com/198
  - # vi /etc/sysconfig/svnserve // svn경로
    - OPTIONS="-r /home/svn" // root 계정으로 svn 저장하는 설정 이걸 설정해주어야 start 사용가능
    - 인터넷에서는 --root /... 이렇게 하던데 왜 안되는지 확인이 필요하다
    
  - # svnadmin create --fs-type fsfs 저장소명  // svn 저장소 생성
  
  - # vi 저장소명/conf/svnserve.conf // svn 설정
    - anon-access  	= none 		// 인증 되지 않은 사용자 접근 거부
    - auth-access  	= write 	// 인증된 사용자 쓰기 권한
    - password-db 	= passwd	// 사용자에 대한 계정정보
    - authz-db 	= authz		// 사용자에 대한 저장소 권한주기. Optional

  - # vi 저장소명/conf/passwd // 사용자 설정
    - user = password	// 계정명 = 비밀번호
    
  - # vi 저장소명/conf/authz // 권한 설정
    - [/]	// 최상위 디렉토리 권한
    - user = rw // neobis사용자에게 rw 권한부여
