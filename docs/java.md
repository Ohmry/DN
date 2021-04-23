# Java
- [Java](#java)
  - [Map 객체 생성 예제](#map-객체-생성-예제)
  - [ArrayList 객체 생성 예제](#arraylist-객체-생성-예제)

## Map 객체 생성 예제
```java
// HashMap생성
HashMap<String,String> map1 = new HashMap<String,String>(); 
// new에서 타입 파라미터 생략가능
HashMap<String,String> map2 = new HashMap<>();              
// map1의 모든 값을 가진 HashMap생성
HashMap<String,String> map3 = new HashMap<>(map1);          
// 초기 용량(capacity)지정
HashMap<String,String> map4 = new HashMap<>(10);            
// 초기 capacity,load factor지정
HashMap<String,String> map5 = new HashMap<>(10, 0.7f);      
// 초기값 지정
HashMap<String,String> map6 = new HashMap<String,String>(){{  
    put("a","b");
}};
```

참고 사이트 : [[Java] 자바 HashMap 사용법 & 예제 총정리 - 코딩팩토리](https://coding-factory.tistory.com/556)

## ArrayList 객체 생성 예제
```java
// 타입 미설정 Object로 선언된다.
ArrayList list = new ArrayList();                       
// 타입설정 Student객체만 사용가능
ArrayList<Student> members = new ArrayList<Student>();  
// 타입설정 int타입만 사용가능
ArrayList<Integer> num = new ArrayList<Integer>();      
// new에서 타입 파라미터 생략가능
ArrayList<Integer> num2 = new ArrayList<>();            
// 초기 용량(capacity)지정
ArrayList<Integer> num3 = new ArrayList<Integer>(10);   
// 생성시 값추가
ArrayList<Integer> list2 = new ArrayList<Integer>(Arrays.asList(1,2,3));
```

참고 사이트 : [[Java] 자바 ArrayList 사용법 & 예제 총정리](https://coding-factory.tistory.com/551)