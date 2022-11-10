# DI(dependency Injection)


### DI(dependency Injection) 종속성 주입   
DI란 외부에서 두 객체 간의 관계를 결정해주는 디자인 패턴으로,   
인터페이스를 사이에 둬서 클래스 레벨에서는 의존관계가 고정되지 않도록 하고   
런타임 시에 관계를 동적으로 주입하여 유연성을 확보하고 결합도를 낮출 수 있게 해준다.   
의존관계를 주입해주는 여러가지 방법중 몇가지를 살펴보도록 한다.

#### 1. 생성자 주입 방법
```java
Exam exam = new NewlecExam();
/*
ExamConsole = 인터페이스 
InlineExamConsole = ExamConsole 상속클래스
GridExamConsole = ExamConsole 상속클래스
ExamConsole이라는 중간 인터페이스를 놓고 클래스를 생성하도록 하여 결합력을 낮춤
*/
//ExamConsole console = new InlineExamConsole(exam);
ExamConsole console = new GridExamConsole(exam);
console.print();
```
#### 2. setter 주입방법
```java
Exam exam = new NewlecExam();
ExamConsole console = new GridExamConsole();
console.setExam(exam);
console.print();
```

#### 3. xml에서 bean 등록하여 사용하는 방법
setting.xml에 빈을 등록해준다.   
메이븐 프로젝트로 변경하여 pom.xml에 ApplicationContext을 사용하기위한 dependency를 등록해준다.(https://mvnrepository.com/)   
ApplicationContext 생성할때 bean이 등록된 xml을 통해서 생성해주면 xml에 등록된 bean 이름을 가지고 사용가능해진다.   

```
<!--Exam exam = new NewlecExam();-->
<bean id="exam" class="spring.di.entity.NewlecExam"/>

<!--ExamConsole console = new GridExamConsole(exam);-->
<bean id="console" class="spring.di.ui.GridExamConsole">
<!--console.setExam(exam);-->
<property name="exam"  ref="exam"/>
</bean>
```
```java
ApplicationContext context = new ClassPathXmlApplicationContext("spring/di/setting.xml");
//ExamConsole console = (ExamConsole) context.getBean("console");
ExamConsole console = context.getBean(ExamConsole.class);
console.print();
```
---
