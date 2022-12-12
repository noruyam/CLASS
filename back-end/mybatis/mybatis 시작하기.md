# 
※※해당 글은 xml을 통한 mybatis 설정 글입니다.※※

mybatis 라이브러리를 추가하기 위하여 pom.xml에 다음 dependency를 추가한다.

```
<dependencies>
  <dependency>
     <groupId>org.mybatis</groupId>
     <artifactId>mybatis</artifactId>
     <version>3.5.5</version>
  </dependency>
</dependencies>
```

그리고 오라클 jdbc를 사용하기 위해 ojdbc dependency도 추가해준다.

```
<dependency>
  <groupId>com.oracle.database.jdbc</groupId>
  <artifactId>ojdbc6</artifactId>
  <version>11.2.0.4</version>
</dependency>
```

[https://mybatis.org/mybatis-3/ko/getting-started.html](https://mybatis.org/mybatis-3/ko/getting-started.html)

 [MyBatis – 마이바티스 3 | 시작하기

Copyright © 2009–2021MyBatis.org. .

mybatis.org](https://mybatis.org/mybatis-3/ko/getting-started.html)

위 사이트에서 아래로 조금 스크롤한 다음 '매핑된 sql구문 살펴보기'에서

다음 코드 복사한뒤 config.xml 맨 위에 붙여 넣기

```
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
  PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
  "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
```

mybatis 사용은 가능하게 되었으니 DB에 접속할 수 있도록 설정

이어서 config.xml에 DB정보를 넣어주자

```
<environments default="development">
    <environment id="development">
      <transactionManager type="JDBC"/>
      <dataSource type="POOLED">
        <property name="driver" value="oracle.jdbc.OracleDriver"/>
        <property name="url" value="jdbc:oracle:thin:@접속할 IP주소:서비스명"/>
        <property name="username" value="본인ID"/>
        <property name="password" value="본인PWD"/>
      </dataSource>
    </environment>
</environments>
```

이렇게 하면 우선 DB에 접속은 가능하게 되었다. 

다음은 매핑할 파일을 지정해주어야 한다.

```
 <mappers>
    <mapper resource="co/kr/mono/training/astep02/baseselect/SelectBaseMapper.xml"/>
    <mapper resource="co/kr/mono/training/astep03/select/SelectNVOMapper.xml"/>
 </mappers>
```

위에 보이는 대로 매핑을 하기 위해서 해당 경로에 있는 Mapper.xml를 찾아서 매핑을 하라고 컴퓨터에게 알려줘야 하는 것! 

[##_Image|kage@Q5eZn/btrpLtqe7vH/Mg9QUTBFXaU5Nz0WGKgSN1/img.png|CDM|1.3|{"originWidth":358,"originHeight":139,"style":"alignLeft"}_##]

※ Mapper파일의 경로는 사진과 같은데 이런 식으로 패키지부터 경로를 작성하면 된다.

Mapper를 설정해 주었다면 Mapper.xml 안에 DB에 들어가는 쿼리문을 작성해주어야 하는데

```
<mapper namespace="SelectBaseMapper"> // DAO에서 쓰일 MAPPER의 NAME
	<select id="findMsale" resultType="Msales"> // DAO에서 쓰일 MAPPER안의 쿼리문 ID와 반환형
		SELECT 
			prodid
			,prodnm
			,salecnt
		FROM 
			MSALES
	</select>
</mapper>
```

Mapper.xml는 DB에 쿼리문을 보내주고 데이터를 받아줘야 하는 형태인데 다음과 같이 DAO에서 mapper를 호출하기 위해선 우선 mapper의 namespace를 설정해주어야 한다.

※ 처음 보는 사람도 알아보기 쉽도록 name을 정해주자.

그리고 그 mapper안에 있는 여러 쿼리문 중에 하나의 쿼리를 선택해서 들어가야 하므로

각 쿼리문마다 id값을 정해주어야 한다. (예시에선 "findMsale")

그리고 데이터가 나오게 된다면 반환 타입을 지정해주어야 하므로 resultType를 설정해주어야 한다.

여기서 resultType에 설정된 "Msales"는 별명과 같은데 임의로 설정해주는 것이 아닌 config.xml에서 별명을 지어주어야 사용이 가능하다.

```
<typeAliases>
   <typeAlias alias="Msales" type="co.kr.mono.training.vo.MsalesVO"/>
</typeAliases>
```

위와 같이 VO파일 경로를 지정해주고 해당 파일을 "Msales"라는 별명을 지어주었다. 이로써 resultType에 "Msales"라는 별명을 사용할 수 있게 된 것!

이러면 이제 기본적인 DB 접속은 끝났다.
