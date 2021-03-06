# 개발 원칙
## 일반 원칙
### KISS(Keep it Simple Stupid)
    -  대부분의 프로그램은 단순할 때 더 원할히 동작한다.
        -  코드가 짧을 수록 수정이 쉽고, 버그가 적고, 쓰기 쉽다.
        -  최고로 정교한 코드는 단순한 코드에서 나온다.
        -  완벽한 코드는 다른 말로는 더이상 추가할 내용도, 뺄 내용도 없는 코드이다.
    -  쉬운 소스일수록 유지보수에 유리하다.
    -  사실 필요 이상으로 유연하게 개발하는 것은 Over-engineering이라고 볼 수 있다. 누구도 미래를 예측할 수 없고 특정 구간에서 유연한 설계가 필요할 지 판단하는 것은 불가능하다.
    -  쉬운 소스가 확률적으로 더 안정적이고 구현상의 오류가 더 적다.
    -  전략
        1. 상속, 다형성, 동적 바인딩 등 복잡한 객체 지향의 개념의 사용을 최대한 피한다. 위임, 단순 조건문을 최대한 활용하여 개발한다.
        2. 로우 레벨 최적화를 자제한다(ex - 어셈블러, 비트연산 혹은 포인터 등). 성능 최적화보다 정확한 동작이 우선이다.
        3. 복잡한 알고리즘을 고민하는 것 보단 단순 브루트-포스 알고리즘을 사용하는게 쉽다.
        4. 변경 사항이 매우 적은 기능이 추가될 경우 기존 클래스에 추가적인 메소드를 추가하는 것에 우선순위를 두는게 좋다.
### YAGNI(You are not gonna need it)
    - 필요가 생기기 전엔 구현하지 않는다.
        - 내일 필요할 듯한 내용에 대한 코딩은 오늘 끝내야 할 일 또는 현재 이슈에 대한 작업에 대한 능률을 잃게 한다.
        - 코드를 추가시키며 프로그램의 복잡도와 사이즈가 커지게 한다.
    - 진짜 필요한 것만 구현한다. 미래를 예측하지 않는다.
### DTSTTCPW(Do the simplest thing that could possibly work)
    - 문제를 해결하기 위한 가장 단순한 방법을 찾는다.
    - 전략
        1. 최대한 문제를 세분화하라, 세분화한 문제들의 정의는 단순해진다.
        2. 단순한 문제를 해결하기 위한 객체와 함수들은 독립적이고 재사용성이 높아진다.
        3. 명확한 목적을 가진 객체들은 단순하고 이해하기쉽고, 좋은 객체 설계를 가지게 된다.
        4. 아무런 변경 없이 다른 프로젝트에 적용할 수 있는 클래스를 만드는것이 최선이다.
### 관심사 분리
    - 관심사의 분리는 컴퓨터 과학에서 디자인 원칙 중의 하나이다. 각 프로그램은 자신이 맡은 분야에 대해서만 집중할 수 있도록 한다.
    - DB가 오라클에서 mysql로 변한다고 해서 업무 클래스의 변경이 일어나서는 안된다(DataSoruce)
    - 관심사 분리가 잘 이루어진 경우 각 부분은 재사용성이 높아지고, 독립적으로 변화할 수 있게 된다.
    - 요구사항을 최대한 단순화하여 모듈간의 중복이 최소한이 될 수 있게 개발한다.
### Keep Things Dry(Don't repeat yourself)
    - 모든 지식은 프로그램 내에서 단일하고, 어렵지 않고, 신뢰할 수 있게 표현되어야한다.
    - 코드 중복은 유지보수성을 떨어트리고 논리적 모순을 낳는다.
    - 동일 로직의 변경은 동시에 일어나야 한다.
    - DRY가 잘 지켜진 경우, 변경 대상이 아닌 로직은 절때 수정되지 않는다.
    - 전략
        1. 같은 코드를 세번 연속 사용한다면 리팩토링을 시도한다(extract method 등) - rule of three
        2. 모든 지식을 하나로 보관한다(주석보단 문서로, 문서보단 meta 정보로) - 일관성을 유지할 수 있게 노력한다.
### 유지보수를 위한 코드작성
    - SI보다 SM의 비용이 훨씬 크다.
    - 전략
        1. 유지보수하는 개발자의 입장에서 개발한다.
        2. 내 코드를 봐야 할 개발자는 싸이코패스일 수 있다.
        3. 누가 봐도 알 수 있게 코드를 작성한다.
        4. 내가 봤을때 아무 생각 없이 코드를 읽을 수 있어야 한다.
### 성급한 최적화를 피한다
    - 성능에 매우 큰 영향도를 미치지 않는 부분까지 최적화할 필요는 없다. 불필요한 최적화는 디버깅과 유지보수에 부정적인 영향만 끼친다.
    - 전략
        1. 병목 구간이 발견되기 전까진 최적화하지 않는다.
        2. 구현 -> 예외처리 -> 최적화 순서를 따른다.
### 결합도를 줄인다.
    - 모듈/컴포넌트간 결합도를 항상 줄여서 개발한다.
    - 결합도가 증가하면 A class를 수정할 시 B class에서 예상하지 못한 오류가 발생할 수 있게 된다.
    - 전략
        1. 세부 구현사항을 숨기면 숨길수록 결합도는 줄어든다(A class의 구현을 B class가 굳이 알 필요는 없다).
        2. 디미터 법칙을 적용한다.
        3. 모듈간 관계의 복잡도를 최대한 줄이고, 제거한다.
### 디미터 법칙(Law of Demeter)
    - 모르는 사람에게 말을 걸지 않는다.
    - 전략 - 객체가 호출할 수 있는 메소드를 한정시킨다.
        1. 자기 자신이 가진 메소드
        2. 메소드의 파라미터로 넘어온 객체의 메소드
        3. 메소드 내부에서 생성된 객체의 메소드
        4. 메소드가 포함하고 있는 객체의 메소드
        5. 전역 객체
```java
class Demeter {
    private A a;
    
    private void hello() {
        System.out.println("Hello?");
    }

    public void sayHello(B b) {
        C c = new C();
        
        hello(); // 가능
        a.sayBye(); // 가능
        b.sayHi(); // 가능
        c.sayWelcome(); // 가능
        c.getDate().showDate(); // 위반(c.showDate()메소드를 직접 호출하게 수정 c.getDate()시 나온 객체가 VO 혹은 DTO라면 디미터 법칙을 위반하지 않지만, BEAN 객체일 경우 디미터 법칙 위반임 - VO나 DTO일 경우 show는 잘 없으므로 위반일 가능성이 높음)
    }
}
```
### 상속보단 합성을 사용한다
    - 상속을 사용할 경우 클래스간 결합도가 크게 높아진다.
    - 상속은 쉽게 문제를 해결할 수 있게 해주지만 리스코프 치환법칙 위반이다.
    - 전략
        1. is a, has a 를 항상 생각한 후 상속할지, 합성할지 결정한다.
        2. LSP위반 여부를 체크한다.
### IoC(Inversion of Control)
    - 시스템의 제어는 프레임워크가 담당한다.
    - 구현과 서비스의 결합도를 낮춘다.
    - 하나의 모듈은 하나의 목표를 갖게한다.
    - 모듈은 시스템에 의존하지 않고, 설정에 의존하게 한다.
    - 모듈간 교체에 대한 사이드 이펙트를 줄인다.
    - 전략
        1. Factory Pattern
        2. Service Locator Pattern
        3. Dependency Injection
        4. Context Lookup
        5. Template Method Pattern
        6. Strategy Pattern
### 응집도의 최대화
    - 하나의 모듈은 그 설계에 충실하게 구현되어야 한다.
    - 응집도가 낮은 모듈은 모듈에 대한 이해를 어렵게 한다.
    - 응집도가 낮은 모듈의 변경이 있을 시, 다른 모듈에 영향을 미치게 된다.
    - 필요 없는 기능까지 제공하는 모듈은 재사용하기 꺼려진다.
    - 전략
        1. 하나의 모듈이 하나의 책임을 공유하게 한다.
### 리스코프 치환법칙
    - 부모 클래스 객체를 자식 클래스 객체로 변경해도 전체 프로그램의 동작은 일정해야 한다.
    - 부모 클래스의 명세를 벗어나는 자식 클래스는 존재하면 안된다.(자식 클래스 is kind of 부모 클래스)
    - 일반 개념적으로 상속이 가능해 보일지라도, 실제 객체 지향의 관점에서 상속 관계가 아닐 수 있음
### 개방/폐쇄 원칙
    - 확장에 대해서는 개방되어 있지만, 수정에 대해서는 폐쇄되어야 한다.
    - jdbc 드라이버는 DB가 바뀔 때(오라클 - 마리아), 그에 맞는 jdbc 드라이버를 설정하면 실제 자바 소스에서 jdbc를 사용하는 부분의 수정은 일어나지 않음(새로운 DB가 출시되면 그에 맞는 jdbc 드라이버를 구현 - 확장, 자바 소스에서 jdbc를 사용하는 부분의 변경은 없음 - 폐쇄)
### 단일 책임 원칙
    - 객체는 하나의 책임을 갖고 구현된다. 그 책임 이외의 일로 변경되어서는 안된다.
    - 각 클래스가 가지는 관심사를 분리한다.
    - 회원 정보 객체는 회원 정보에 대한 기능으로만 구성되어야 한다.
### 인터페이스 분리 법칙
    - 거대한 하나의 인터페이스 보단 상세하게 분리된 여러 인터페이스의 조합으로 사용하는게 유리하다.
    - 수많은 메소드를 가진 객체가 변경될 때, 객체를 사용하는 클라이언트에서는 작은 인터페이스만 사용하여 변경에 대응할 수 있도록 한다.
### 의존성 주입
    - 고차원의 모듈은 저차원의 모듈에 의존하면 안된다. 이 두 모듈 모두 다른 추상화된 것에 의존 해야 한다.
    - 추상화 된 것은 구체적인 것에 의존하면 안 된다. 구체적인 것이 추상화된 것에 의존해야 한다.
    