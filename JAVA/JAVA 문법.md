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
> ```java
> split(String regex)
> ```
> 파라미터로 들어오는 문자열을 기준으로 문자열을 쪼갠다. `String[]`을 리턴한다.

---

> ## replace(), replaceAll(), replaceFirst()
>    
> ```java
> replace(CharSequence target, CharSequence replacement) 
> replaceAll(String regex, String replacement) 
> replaceFirst(String target, String replacement)
> ```
> replace : 모든 target replacement로 치환   
> replaceAll : replace()와 비슷하나, 첫번째 인자로 정규식을 넣는다.   
> replaceFirst : 첫번째 발견되는 target만 치환한다.

> ## StringBuilder (java.lang.StringBuilder)

> 생성자
> StringBuilder sb = new StringBuilder(): 객체 선언
> StringBuilder sb = new StringBuilder("aaa"): 문자열을 바로 넣을 수도 있다.
> 주요 메소드
> ```java
> .append() // 문자열을 추가한다. (sb.append("bbb"), sb.append(4))
> .insert(int offset, String str)// offset 위치에 str을 추가한다. (sb.insert(2, "ccc"))
> .replace(): 첫번째와 두번째 파라미터로 받는 숫자 인덱스에 위치한 문자열을 대체한다. (.replace(3, 6, "ye"))
> .substring(int start, (int end))// 인덱싱. 파라미터가 하나라면 해당 인덱스부터 끝까지, 두개라면 시작점과 끝점-1 까지 인덱싱 (sb.substring(5), sb.substring(3, 7))
> .deleteCharAt(int index)// 인덱스에 위치한 문자 하나를 삭제한다. (sb.deleteCharAt(3)) 
> .delete(int start, int end)// start 부터 end-1 까지의 문자를 삭제한다. (sb.delete(3, sb.length()))
> .toString()// String으로 변환한다. (sb.toString())
> .reverse()// 해당 문자 전체를 뒤집는다. (sb.reverse())
> .setCharAt(int index, String s)// index 위치의 문자를 s로 변경
> .setLength(int len)// 문자열 길이 조정, 현재 문자열보다 길게 조정하면 공백으로 채워짐, 현재 문자열보다 짧게 조정하면 나머지 문자는 삭제
> .trimToSize()// 문자열이 저장된 char[] 배열 사이즈를 현재 문자열 길이와 동일하게 조정, String 클래스의 trim()이 앞 뒤 공백을 제거하는 것과 같이 공백 사이즈를 제공하는 것, 배열의 남는 사이즈는 공백이므로, 문자열 뒷부분의 공백을 모두 제거해준다고 보면 됨
> ```
