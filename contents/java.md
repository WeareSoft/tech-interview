# 7. Java

#### :small_orange_diamond:객체지향이란

#### :small_orange_diamond:java 프로그래밍이란

#### :small_orange_diamond:java와 c/c++의 차이점
- java와 c/c++의 가장 큰 차이점은 실행 환경이다.
- java에서의 개발: 컴파일 혹은 컴파일 + jar압축
  - 자바는 링크 과정이 없이 컴파일러가 바로 바이트 코드를 생성
- c/c++에서의 개발: 컴파일 + 링크

> - []()

#### :small_orange_diamond:java 언어의 장단점

> - []()

#### :small_orange_diamond:java의 접근 제어자의 종류와 특징
<!-- ![](/images/access-controller.png){: width="600" height="200"} -->


#### :small_orange_diamond:OOP의 4가지 특징
1. 추상화
    * 구체적인 사물들의 공통적인 특징을 파악해서 이를 하나의 개념(집합)으로 다루는 것
2. 캡슐화
    * 정보 은닉(information hiding): 필요가 없는 정보는 외부에서 접근하지 못하도록 제한하는 것
3. 일반화 관계
    * 여러 개체들이 가진 공통된 특성을 부각시켜 하나의 개념이나 법칙으로 성립시키는 과정
4. 다형성
    * 서로 다른 클래스의 객체가 같은 메시지를 받았을 때 각자의 방식으로 동작하는 능력

> - [https://gmlwjd9405.github.io/2018/07/05/oop-features.html](https://gmlwjd9405.github.io/2018/07/05/oop-features.html)

#### :small_orange_diamond:OOP의 5대 원칙 (SOLID)
* **S**: 단일 책임 원칙(SRP, Single Responsibility Principle)
  * 객체는 단 하나의 책임만 가져야 한다.
* **O**: 개방-폐쇄 원칙(OCP, Open Closed Principle)
  * 기존의 코드를 변경하지 않으면서 기능을 추가할 수 있도록 설계가 되어야 한다.
* **L**: 리스코프 치환 원칙(LSP, Liskov Substitution Principle)
  * 일반화 관계에 대한 이야기며, 자식 클래스는 최소한 자신의 부모 클래스에서 가능한 행위는 수행할 수 있어야 한다.
* **I**: 의존 역전 원칙(DIP, Dependency Inversion Principle)
  * 의존 관계를 맺을 때 변화하기 쉬운 것 또는 자주 변화하는 것보다는 변화하기 어려운 것, 거의 변화가 없는 것에 의존하라는 것이다.
* **D**: 인터페이스 분리 원칙(ISP, Interface Segregation Principle)
  * 인터페이스를 클라이언트에 특화되도록 분리시키라는 설계 원칙이다.

> - [https://gmlwjd9405.github.io/2018/07/05/oop-solid.html](https://gmlwjd9405.github.io/2018/07/05/oop-solid.html)

#### :small_orange_diamond:객체지향 프로그래밍과 절차지향 프로그래밍의 차이

#### :small_orange_diamond:java의 non-static 멤버와 static 멤버의 차이
non-static 멤버
* 공간적 특성: **멤버는 객체마다 별도로 존재한다.**
  * ***인스턴스 멤버*** 라고 부른다.
* 시간적 특성: **객체 생성 시에 멤버가 생성된다.**
  * 객체가 생길 때 멤버도 생성된다.
  * 객체 생성 후 멤버 사용이 가능하다.
  * 객체가 사라지면 멤버도 사라진다.
* 공유의 특성: **공유되지 않는다.**
  * 멤버는 객체 내에 각각의 공간을 유지한다.

static 멤버
* 공간적 특성: **멤버는 클래스당 하나가 생성된다.**
  * 멤버는 객체 내부가 아닌 별도의 공간에 생성된다.
  * ***클래스 멤버*** 라고 부른다.
* 시간적 특성: **클래스 로딩 시에 멤버가 생성된다.**
  * 객체가 생기기 전에 이미 생성된다.
  * 객체가 생기기 전에도 사용이 가능하다. (즉, 객체를 생성하지 않고도 사용할 수 있다.)
  * 객체가 사라져도 멤버는 사라지지 않는다.
  * 멤버는 프로그램이 종료될 때 사라진다.
* 공유의 특성: **동일한 클래스의 모든 객체들에 의해 공유된다.**

> - [https://gmlwjd9405.github.io/2018/08/04/java-static.html](https://gmlwjd9405.github.io/2018/08/04/java-static.html)

#### :small_orange_diamond:java의 final 키워드 (final/finally/finalize)
final 키워드
* 개념: 변수나 메서드 또는 클래스가 '변경 불가능'하도록 만든다.
* 원시(Primitive) 변수에 적용 시
  * 해당 변수의 값은 변경이 불가능하다.
* 참조(Reference) 변수에 적용 시
  * 참조 변수가 힙(heap) 내의 다른 객체를 가리키도록 변경할 수 없다.
* 메서드에 적용 시
  * 해당 메서드를 오버라이드할 수 없다.
* 클래스에 적용 시
  * 해당 클래스의 하위 클래스를 정의할 수 없다.

finally 키워드
* 개념: try/catch 블록이 종료될 때 항상 실행될 코드 블록을 정의하기 위해 사용한다.
* finally는 선택적으로 try 혹은 catch 블록 뒤에 정의할 때 사용한다.
* finally 블록은 예외가 발생하더라도 항상 실행된다.
  * 단, JVM이 try 블록 실행 중에 종료되는 경우는 제외한다.
* finally 블록은 종종 뒷마무리 코드를 작성하는 데 사용된다.
* finally 블록은 try와 catch 블록 다음과, 통제권이 이전으로 다시 돌아가기 전 사이에 실행된다.

finalize() 메서드
* 개념: 쓰레기 수집기(GC, Garbage Collector)가 더 이상의 참조가 존재하지 않는 객체를 메모리에서 삭제하겠다고 결정하는 순간 호출된다.
* Object 클래스의 finalize() 메서드를 오버라이드해서 맞춤별 GC를 정의할 수 있다.
  * `protected void finalize() throws Throwable { // 파일 닫기, 자원 반환 등등 }`

> - [https://gmlwjd9405.github.io/2018/08/06/java-final.html](https://gmlwjd9405.github.io/2018/08/06/java-final.html)

#### :small_orange_diamond:java의 제네릭(Generic)

#### :small_orange_diamond:java의 가비지 컬렉션(Garbage Collection) 처리 방법

#### :small_orange_diamond:객체(Object)란 무엇인가

#### :small_orange_diamond:객체 직렬화(Serialization)와 역직렬화(Deserialization)란 무엇인가

#### :small_orange_diamond:클래스와 인스턴스의 차이(Class vs Instance)

#### :small_orange_diamond:오버로딩과 오버라이딩의 차이(Overloading vs Overriding)
<!-- [](#){name=Overloading-vs-Overriding} -->
* 오버로딩(Overloading)
  * 두 메서드가 같은 이름을 갖고 있으나 인자의 수나 자료형이 다른 경우
  * Ex)
    * `public double computeArea(Circle c) { ... }`
    * `public double computeArea(Circle c1, Circle c2) { ... }`
    * `public double computeArea(Square c) { ... }`
* 오버라이딩(Overriding)
  * 상위 클래스의 메서드와 이름과 용례(signature)가 같은 함수를 하위 클래스에 재정의하는 것
  * 상속 관계에 있는 클래스 간에 같은 이름의 메서드를 정의
  * Ex) Circle에서 printMe() 메서드를 재정의한다.
~~~java
public abstract class Shape {
    public void printMe() { System.out.println("Shape"); }
    public abstract double computeArea();
}
public class Circle extends Shape {
    private double rad = 5;
    @Override // 개발자의 실수를 방지하기 위해 @Override(annotation) 쓰는 것을 권장
    public void printMe() { System.out.println("Circle"); }
    public double computeArea() { return rad * rad * 3.15; }
}
public class Ambiguous extends Shape {
    private double area = 10;
    public double computeArea() { return area; }
}
~~~

> - [https://gmlwjd9405.github.io/2018/08/09/java-overloading-vs-overriding.html](https://gmlwjd9405.github.io/2018/08/09/java-overloading-vs-overriding.html)


#### :small_orange_diamond:Call by Reference와 Call by Value의 차이

#### :small_orange_diamond:인터페이스와 추상 클래스의 차이(Interface vs Abstract Class)

#### :small_orange_diamond:JVM 구조

#### :small_orange_diamond:Java Collection Framework

#### :small_orange_diamond:Wrapper class

#### :small_orange_diamond:Annotation

#### :small_orange_diamond:String, StringBuilder, StringBuffer

#### :small_orange_diamond:동기화와 비동기화의 차이(Syncronous vs Asyncronous)



---

## Reference
> - []()


## :house: [Home](https://github.com/Do-Hee/tech-interview)
