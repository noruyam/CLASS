# 문법

---

>## substring()
> ```
> substring(int startIndex);
> substring(int startIndex, int endIndex);
> ```
> startIndex는 시작지점의 인덱스 값이고, endIndex는 종료 지점의 인덱스 값이다.   
> 두 방식 모두 return 값으로 `String[]`을 리턴한다.   
---

>## split()
> ```html
> split(String regex)
> ```
> 파라미터로 들어오는 문자열을 기준으로 문자열을 쪼갠다. `String[]`을 리턴한다.


## replace(), replaceAll(), replaceFirst()
   
```
replace(CharSequence target, CharSequence replacement) 
replaceAll(String regex, String replacement) 
replaceFirst(String target, String replacement)
```
replace : 모든 target replacement로 치환   
replaceAll : replace()와 비슷하나, 첫번째 인자로 정규식을 넣는다.   
replaceFirst : 첫번째 발견되는 target만 치환한다.
