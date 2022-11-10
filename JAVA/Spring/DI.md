# DI(dependency Injection)


### DI(dependency Injection) 종속성 주입   
DI란 외부에서 두 객체 간의 관계를 결정해주는 디자인 패턴으로, 인터페이스를 사이에 둬서 클래스 레벨에서는 의존관계가 고정되지 않도록 하고 런타임 시에 관계를 동적으로 주입하여 유연성을 확보하고 결합도를 낮출 수 있게 해준다.

```java
public class main() {
    public static void main(String[] args) {
        Exam exam = new NewlecExam();
        /*
        ExamConsole = 인터페이스 InlineExamConsole = ExamConsole 상속클래스
        */

        //ExamConsole console = new InlineExamConsole(exam);
        ExamConsole console = new GridExamConsole(exam);
        console.print();

    }
}
```

---
