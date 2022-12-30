# HashMap Value 기준으로 정렬하기
[참고](https://velog.io/@cgw0519/Java-HashMap-Value-%EA%B8%B0%EC%A4%80%EC%9C%BC%EB%A1%9C-%EC%A0%95%EB%A0%AC%ED%95%98%EA%B8%B0)

먼저 Collections.sort()를 사용하기 위해서 List 형태로 Map을 가져와야 한다.    
그러므로 Map.entrySet()을 이용하여 아래와 같이 Map의 Entry Set을 List 형태로 저장한다.
```java
Map<String, Integer> map = new HashMap<>();
map.put("a", 3);
map.put("b", 2);
map.put("c", 1);
List<Map.Entry<String, Integer>> entryList = new LinkedList<>(map.entrySet());
```

그리고 이 EntrySet을 정렬하는 방법을 사용한다.

### 1. Entry 내장 함수 사용
먼저 Map.Entry에 있는 comparingByValue() 함수를 사용하여 아래와 같이 정렬할 수 있다.

```java
Map<String, Integer> map = new HashMap<>();
map.put("a", 3);
map.put("b", 2);
map.put("c", 1);
List<Map.Entry<String, Integer>> entryList = new LinkedList<>(map.entrySet());
entryList.sort(Map.Entry.comparingByValue());
for(Map.Entry<String, Integer> entry : entryList){
    System.out.println("key : " + entry.getKey() + ", value : " + entry.getValue());
}

//key : c, value : 1
//key : b, value : 2
//key : a, value : 3
```
---
### 2. comparator 사용
또 다른 방법으로는 comparator 인터페이스를 사용하여 아래와 같이 정렬하는 방법이 있다.

```java
Map<String, Integer> map = new HashMap<>();
map.put("a", 3);
map.put("b", 2);
map.put("c", 1);
List<Map.Entry<String, Integer>> entryList = new LinkedList<>(map.entrySet());
entryList.sort(new Comparator<Map.Entry<String, Integer>>() {
    @Override
    public int compare(Map.Entry<String, Integer> o1, Map.Entry<String, Integer> o2) {
	return o1.getValue() - o2.getValue();
    }
});
for(Map.Entry<String, Integer> entry : entryList){
    System.out.println("key : " + entry.getKey() + ", value : " + entry.getValue());
}

//key : c, value : 1
//key : b, value : 2
//key : a, value : 3
```

또한 Comparator를 이용하므로 아래와 같이 o1과 o2의 순서를 바꾸어 내림차순으로 정렬을 할 수도 있다.

```java
Map<String, Integer> map = new HashMap<>();
map.put("a", 1);
map.put("b", 2);
map.put("c", 3);
List<Map.Entry<String, Integer>> entryList = new LinkedList<>(map.entrySet());
entryList.sort(new Comparator<Map.Entry<String, Integer>>() {
    @Override
    public int compare(Map.Entry<String, Integer> o1, Map.Entry<String, Integer> o2) {
	return o2.getValue() - o1.getValue();
    }
});
for(Map.Entry<String, Integer> entry : entryList){
	System.out.println("key : " + entry.getKey() + ", value : " + entry.getValue());
}

//key : a, value : 3
//key : b, value : 2
//key : c, value : 1
```

### 3. 람다 함수 사용
위에 사용한 comparator를 아래와 같이 람다 함수로 구현할 수도 있다.    
역시 같은 방법으로 내림차순 정렬 역시 가능하다.

```java
Map<String, Integer> map = new HashMap<>();
map.put("a", 3);
map.put("b", 2);
map.put("c", 1);
List<Map.Entry<String, Integer>> entryList = new LinkedList<>(map.entrySet());
entryList.sort(((o1, o2) -> map.get(o1.getKey()) - map.get(o2.getKey())));
for(Map.Entry<String, Integer> entry : entryList){
    System.out.println("key : " + entry.getKey() + ", value : " + entry.getValue());
}

//key : c, value : 1
//key : b, value : 2
//key : a, value : 3
```

Entry의 comparing 함수나 Comparator의 comparing 함수를 사용하는 것이 아닌 override해서 사용하는 상황은 클래스를 만들어서 사용하는 경우이다.    
새로 만든 클래스를 HaspMap의 Value 타입으로 사용하는 경우에 클래스 내부의 멤버 변수를 기준으로 정렬하고자 한다면 아래와 같이 구현할 수 있다 !

```java
 public static class MyClass{
        private int num;
        MyClass(int num){
            this.num = num;
        }
    }
    
    public static void main(String[] args){
        Map<String, MyClass> map = new HashMap<>();
        map.put("a", new MyClass(3));
        map.put("b", new MyClass(2));
        map.put("c", new MyClass(1));
        List<Map.Entry<String, MyClass>> entryList = new LinkedList<>(map.entrySet());
        entryList.sort(((o1, o2) -> o1.getValue().num - o2.getValue().num));
        for(Map.Entry<String, MyClass> entry : entryList){
            System.out.println("key : " + entry.getKey() + ", value : " + entry.getValue().num);
        }
    }
    
//key : c, value : 1
//key : b, value : 2
//key : a, value : 3
```
