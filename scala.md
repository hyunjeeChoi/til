# 1장 스칼라 소개

## 스칼라의 역사와 목적
 * 함수형 프로그래밍과 정적 타입 시스템을 지원하는 범용 프로그래밍 언어
 * 소스코드는자바 바이트 코드로 컴파일 될 수 있고 결과 실행 코드는 JVM에서 실행
 * 스칼라에 액터 기반 동시성 프레임워크인 매우 강력한 패턴 매칭 기능이 있음
 * 1급 함수와 고차 함수를 지원
 * 스칼라라는 이름은 사용자의 요구에 따라 확장될 수 있게 설계된, 확장 가능하고 FP와 OOP가 혼합된 언어
  - 마틴 오더스키의 설명
 ```
  스칼라를 실험하면서 검증하고자 했던 두 가지 가설
   1. 컴포넌트 소프트웨어의 프로그래밍 언어는 동일한 개념이 큰 부분뿐 아니라 작은 부분을 설명할 수 있다는 점에서 확장 가능해야 한다고 가정. 
    따라서 많은 기본 요소를 추가하기보다 추상화, 합성, 분해 메커니즘에 집중한다. 
   2. 객체지향 프로그래밍과 함수형 프로그래밍을 통합하고 일반화한 프로그래밍 언어가 컴포넌트를 확장할 수 있는 기능을 제공할 수 있다고 가정한다.    
 ```
 
## 스칼라: 확장 가능한 언어
 * 객체지향
  ```
  직접적인 다중 상속을 지원하지 않지만 다중 상속 구조를 달성하기 위해 스칼라의 서브클래싱과 믹싱 기반의 컴포지션을 사용해야 한다.
  ```
 * 함수형
  ```
   - 일등시민과 같은 함수를 취급
   - 해당 기능을 쉽게 사용할 수 있는 문법과 트레이트를 확장하는 객ㅊ를 사용해 달성할 수 있다.
   - 익명함수를 정의하는 간단하고 쉬운 방법을 정의한다.
   - 고차 함수를 지원하고 중첩 함수를 허용한다.
   - 불변 방식은 코들를 작성하는 데 도움을 주고 불변 방식을 사용해 동기화와 동시성으로 쉽게 병렬 처리할 수 있다.
  ```
 * 정적 타입 지원
  ```
   - 중복 타입정보를 제공할 것을 기대하지 않는다. 가장 중요한 것은 다시 반복할 필요조차 없다.
   - 컴파일러가 모든 종류의 검사를 수행하도록 보장한다. 
   - 코드가 실행되기 전에 초기 단계에서 가장 사소한 버그와 에러를 찾거나 해결할 수 있다.
  ```
 * JVM에서 동작
  ```
   - JVM에서 쉽게 실행할 수 있는 바이트 코드로 컴파일된다.
   - 자바에서 스칼라로 쉽게 전환할 수 있고 둘 다 쉽게 통합하거나 안드로이드 어플리케이션에서 스칼라를 사용해 함수형으로 작성할 수도 있다.
   - 스칼라에는 scalac 컴파일 커맨드가 있다.
  ```
 * 자바 코드를 실행 가능
 * 동시 및 동기화 처리 수행 가능
  ```
   - 프로그래밍의 일반적인 패턴과 개념을 간결하고 효과적으로 표현할 수 있는 능력을 얻을 수 있다.
   - 불변방식으로 코드를 작성할 때 도움을 얻는다.
   - 동기화 및 동시성 병렬 처리 코드를 쉽게 작성할 수 있다.
  ```
 ## 스칼라: 자바 프로그래머를 위한 스칼라 
  * 모든 타입은 객체
  ```
   - 주의사항인지 모르겠지만 모든 값이 객체로 보이지만 실제로 일부는 개체가 아니다.
   - 참조 타입과 원시 타입의 차이는 여전히 존재하지만 대부분 해당 타입을 숨긴다.
  ```
  * 타입추론
  ```
   - 컴파일 타임에 타입을 추론하는 것
   - 컴파일 타임에 실행되며 런타임에는 수행되지 않는다.
  ```
  * 스칼라 REPL
  ```
   - 입력한 표현식을 읽고
   - 컴파일러를 사용해 표현식을 평가하고
   - 평가 결과를 출력하고
   - 추가 표현식을 입력할 때까지 기다린다.
   
   - 스칼라 셸에 스칼라 코드를 좀 더 쉽고 간결하게 작성할 수 있게 하는 
  ```
  * 중첩 함수
  ```
   - 내부에서 함수를 정의할 수 있고 해당 함수에 대한 외부 접근이 금지
  ```
  <pre>
<code>
def sum(vector:List[Int]): Int = {
 def helper(acc: Int, remaining:Linst[Int]): Int = remaining match {
  case Nil => acc
  case _   => helper(acc + remaining.head, remaining.tail)
 }
  helper(0, vector)
}
</code>
</pre>
  
  * import 문
  ```
   - 소스 파일의 거의 모든 곳에서 import문을 작성할 수 있다.
   - 스칼라의 _ 는 자바에서 사용하는 * 과 비슷하게 와일드카드로 import문에 사용된다.
   - {}를 사용해 한 라인의 코드에서 동일한 상위 패키지의 import문을 나타낼 수 있다.
   - 스칼라에서 임포트한 패키지의 이름을 변경할 수 있다. 
    > import scala.collection.mutable.{Map => MutableMap}
   - 패키지 간의 충돌이 발생하거나 다른 목적이 발생하면 패키지 멤버를 제외할 수 있다. 
  ```
  * 연사자를 메소드로 사용
  ```
   - 연산자 오버로딩을 지원하지 않는다. 
   - 단일 파라미터를 받는 메소드 호출에 대한 대체 구문은 중위 구문을 사용하는 것이다.
   - 메소드 이름이 : 으로 끝나면 호출은 오른쪽 결합이 된다.
   - 결합은 메소드가 반대 방향으로 호출하지 않고 표현식의 왼쪽 파라미터가 오른쪽 파라미터에서 호출되는 것을 의미한다.
  ```
  * 메소드와 파라미터 목록
  ```
   - 스칼라 메소드는 여러 파라미터 목록을 가질 수 있거나 전혀 갖지 않을 수도 있다.
  ```
  * 메소드 안의 메소드
  ```
   - 스칼라는 너무 큰 메소드를 여러 개의 작은 메소드로 나눌 수 있는 기능을 제공한다.
  ```
  * 스칼라 생성자
  ```
   - 스칼라 클래스의 본문 자체가 생성자라는 점이다.
  ```
  * 정적 메소드 대신 오브젝트
  ```
   - 클래스와 동일한 이름을 가진 오브젝트를 동일한 소스 파일에서 정의하면 해당 오브젝트를 클래스의 컴패니언이라고 한다. 
   - 컴패니언 오브젝트에서 정의한 함수는 자바 클래스의 정적 메소드와 동일하다.
  ```
  * 트레이트
  ```
   - 클래스의 동작을 확장하고 풍부하게 하는 트레이트를 제공
   - 함수의 프로토타입 또는 시그니처를 정의하는 인터페이스와 유사
   - 빌딩 블록과 같은 트레이트를 사용해 클래스의 컴포지션을 구성한다.
   - 서브클래스는 단 하나의 슈퍼클래스만 확장할 수 있다.
  ```
  
  기타
  ----

 ### 1급 함수 - 1급 객체 (First Object, 또는 1급 시민)
  - 1급 객체(First class object)란 다음과 같은 조건을 만족하는 객체
    - 변수나 데이터 구조안에 담을 수 있다.
    - 파라미터로 전달 할 수 있다.
    - 반환값(return value)으로 사용할 수 있다.
    - 할당에 사용된 이름과 관계없이 고유한 구별이 가능하다.
    - 동적으로 프로퍼티 할당이 가능하다.
 `자바스크립트에서 함수(Function)은 객체(Object)이므로 1급 함수로 불린다.`

 ### 고차 함수 (High-Order Function)
   - 람다 계산법에서 만들어진 용어로 아래 조건을 만족하는 함수
   - 함수에 함수를 파라미터로 전달할 수 있다.
   - 함수의 반환값으로 함수를 사용할 수 있다.
   - 고차 함수는 1급 함수의 부분 집합(Subset)이다.

### 정적타입언어, 동적타입언어
   - 정적타입언어는 컴파일 시간에 변수의 타입이 결정 - scala, java
   - 동적타입언어는 런타임에 타입이 결정 - ruby, python 
