## 1. jQuery 사용한다고 선언하기   
제이쿼리를 사용하기 위해서는 제이쿼리 라이브러리를 추가해야 합니다 방법은 여러가지가 있지만 대표적으로 아래의 세 가지 방법을 많이 사용합니다.

```
<!-- 적용방법 1 -->
<script src="js/jquery.js"></script>
<!-- 적용방법 2 : cdn -->
<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
<!-- 적용방법 3 -->
<script src="http://code.jquery.com/jquery-latest.js"></script>
```
첫 번째 방법은 API를 직접 다운받아 사용하는 방법입니다.
파일은 compressed(jquery.js), uncompressed(jquery.min.js) 두 가지가 존재하는데 압축된 것과 안된 것으로 배포할 때는 min파일(compressed)를 사용하는 것이 좋습니다. (용량차이)   
두 번째 방법은 CDN을 이용하는 방법으로 위의 예제에서는 구글의 것을 사용했습니다.   
세 번째 방법은 jquery에서 제공하는 최신 버전의 jQuery url입니다.

## 2. jQuery의 시작
```
$(document).ready(function(){
// process..
});
```
제이쿼리의 시작은 자바스크립트에서의 window.onload와 비슷하게 $(document).ready()에서 시작합니다.   
ready는 일종의 제이쿼리 이벤트로 document 문서가 로드 되었을 때 발생합니다.   
제이쿼리가 자바스크립트보다 더 빨리 실행되는 이유입니다.   
자바스크립트의 window.onload는 text, image, sound등의 모든 내용을 로드 한 뒤 실행되는 반면 제이쿼리의 $(document).ready는 text 문서만 로딩하고 실행됩니다.   
이미지나 사운드는 크기가 큰 만큼 로딩하는데 시간이 더 많이 소요되기 때문입니다.

## 3. jQuery 선택자

#### $() 팩토리함수   
$()함수는 괄호안에 CSS선택자를 정의해서 DOM노드(element)를 반환합니다. 하나의 함수로 여러가지의 종류의 객체를 생성할 수 있는 팩토리함수입니다.

#### jQurey() 팩토리함수
$()함수와 같은 기능을 하지만 타 언어에서 $ 키워드를 사용하는 경우가 있습니다. 이 때 중복을 피하기 위해 지원하는 래퍼 입니다.

```
$(document).ready(function () {
$("div a[target]").css("background", "#aaa");    // [속성]
$("div a[href='http://naver.com']").css("background", "#0ff");    // [속성]
$("div a[href!='http://naver.com']").css("background", "#fab");    // [속성]

// 패턴 : regular expression
$("div[id^='content-']").css("background", "#abc");    // ^ : ~로 시작
$("div[id$='1']").css("background", "#f00");    // $ : ~로 끝

// 특정 단어 포함
$("input[name='한국']").css("background", "yellow");    // 일치
$("input[name*='한국']").css("background", "silver");    // 포함
$("input[name~='한국']").css("background", "cyan");    // 독립
});

$(document).ready(function () {
$("*").css("border", "1px solid #FF0000");     // 문서 전체를 선택
$('span').css("border", "3px dotted blue");     // 요소(element, tag) 선택
$("#content").css("background-color", "cyan");     // id 선택
jQuery(".my").css("border", "5px solid rgb(255, 255, 0)");    // class 선택
$("i > .my").css("font-size", "40px"); // > 는 직계 하위 엘리먼트, " "는 하위 어딘가에 엘리먼트
});
```
제이쿼리의 셀렉터(선택자)는 기본적으로 CSS와 동일합니다.

#### 셀렉터 사용법 설명
- $("p") : element 셀렉터   
- $("#id") : id 셀렉터
- $(".class") :	class 셀렉터   

쌍 따옴표 안에 태그명을 띄어쓰기로 나열하면 : "하위태그 중 어딘가" 라는 의미이고,
 를 통해 나열하면 직속 하위 엘리먼트라는 의미입니다.
"요소1~요소2" 처럼 ~를 사용해서 나열하면 요소2 엘리먼트를 요소1 이후부터 검색해서 선택합니다.

**[]를 사용하면 요소의 속성을 선택할 수 있습니다.**     
또, 속성에는 간단한 정규표현식을 사용할 수 있습니다.

- ^ : 앞의 글자 패턴과 같으면 선택
- $ : 뒤의 글자 패턴과 같으면 선택
- \* : 속성 안에 글자가 포함되어 있다면 선택
- ~ : 속성 안에 글자가 정확히 포함되어 있으면 선택, 중복 불가
- = : 완전히 일치해야 선택

```
$(document).ready(function () {
//var p = document.getElementsByTagName("p");
var p = $('p');
p[0].style.color = "red";    // javascript
p[1].style.color = "blue";
p[2].style.color = "green";

$("p").eq(1).css("color", "aqua");    // jQuery
$("p").eq($("p").index($(".kbs"))).css("color", "yellow");

//$("요소~요소2") : 요소2를 요소 1에서부터 검색
var arr = $("h1~p");
var result = "";
for(var i = 0; i < arr.length; i++) {
//result += arr[i].innerHTML + ", ";    //js
//result += arr[i].innerText + ", ";
//result += $(arr[i]).html() + ", ";    //jq
result += $(arr[i]).text() + ", ";    //jq
}
console.log("result : " + result);

var arr2 = $("p:not(.kbs)");    // 제외

// 실행 중에 요소 추가
//$("b").prepend("<h2>요소 추가(기존요소 앞)</h2>");
$("<h2>요소 추가(기존요소 앞)</h2>").prependTo("b");
$("b").append("<h2>요소 추가(기존요소 뒤)</h2>");
//$("<h2>요소 추가(기존요소 앞)</h2>").appendTo("b");

// 반복
var arr3 = "";
$("li").each(function () {
//arr3 += $(this).html() + " ";
arr3 += $(this).text() + " ";
});
console.log(arr3);

// 사용자 정의 선택자
$('tbody tr').css("background", "#ffaacc");
$('tbody tr:odd').css("background", "#ccddee");    // 홀수
$('tbody tr:even').css("background", "#bbbbbb");    // 짝수
$("tbody tr:eq(1)").css("background", "yellow");
$("tbody tr:gt(3)").css("background", "red");
$("tbody tr:lt(2)").css("background", "blue");
$("tbody tr:contains('tom3')").css("background", "gold");
});
```
사용자 정의 선택자도 있는데 선택자 뒤에 콜론(':')을 붙여 사용합니다. 종류는 다음과 같습니다.

- :eq(index) : 선택된 요소들 중 index에 해당하는 요소
- :odd : 홀수 행 선택
- :even : 짝수 행 선택
- :contains("문자열") : 해당 문자열이 포함된 요소를 선택
- :gt : greater than (>)
- :lt : less than (<)


[참고](https://kyun2.tistory.com/52)
