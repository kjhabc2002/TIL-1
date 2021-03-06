## Dagger2 & Koin

DI(Dependency Injection) tool 로 Dagger 2 를 주로 많이 사용 해 왔었다. 공인되어진 그리고 안정성이 입증된 DI tool 로서 이미 많은 개발자분들이 사용 중 인 것으로 알고 있다.   

Dagger 2 의 APT(Annotation Processing Tool) 에 의해 만들어지는 JAVA 코드에 의해 쉽게 DI를 사용 할 수 있다. 하지만 쓰면서 불편함을 느꼇을때도 있었고 그로 인하여 다른 DI tool 을 찾아본 적 이 있었다.  

그러다가 찾은 Koin 에 대해서 알게 되었다. Service locator design pattern 을 기반으로 만들어진 이 DI tool 은 Dagger 와는 다른 방식으로 동작 한다. 그 동작의 다름은 작지만 크게 느껴질 수 밖에 없는 차이점을 갖고 있다. Kotlin 으로 작성된 이 도구는 정말 유용하지만 그에 반해 약점또한 갖고 있다. 이 두가지 도구를 비교 하여 어떤 상황에서 어떤 도구를 사용 하는게 좋을지 고민 해 보려 한다. 

## 1. Dagger 2

Dagger 2 는 APT(KAPT) 에 의해 Annotation 을 기존 코드에 작성 하면 APT에 의해 자동으로 자바 코드를 생성 한다. 개발 중 어노테이션을 작성 시점 에서는 컴파일 이전이지만, 이를 런타임 시점으로 생각 하고 개발 할 수 있게 도와주는 DI 도구 이다. 

- 장점
  - APT 을 이용하여 자동 생성되어지는 자바 코드들로 인해 각 모듈, 컴포넌트만 신경 쓰면 되서 유지, 보수에 강점
  - 안정성. 컴파일 시점에 오류를 알려주기 때문에 런타임 시점에 문제가 발생할 확률이 매우 낮다. 
  - 컴파일 시점에 생성된 코드를 기반으로 동작 하기 때문에 런타임 시 오버헤드가 적다. 

- 단점 
  - 컴파일 시점에 코드를 생성 하기 때문에 컴파일 시 오버헤드가 생길 수 있다. 
  - 러닝커브가 높다. 처음 사용할 때 어려움을 많이 겪을 수 있다.
  - gradle 에 추가 설정이 필요하다. 
  - JAVA 기반으로 구성 되어 코틀린의 장점을 일부 사용 할 수 없음. 
  
위 단점의 경우에는 개발 환경 에 따라서 다르게 느껴질 수 있다. 

### 1.1 Module

### 1.2 Component

### 1.3 Injection

## 2. Koin

 Koin 은 100% Kotlin 으로 구성된 DI tool 으로서 Service locator 디자인 패턴을 기반으로 작성 되었다. 
 
- 장점
  - 낮은 러닝 커브. 
  - 모듈등 코드가 직관적이어서 알기 쉽고 

- 단점
  - Service Locator 디자인 패턴이 갖는 런타임 중 오류 핸들링이 무조건 필수 적 이다. 
    - 런타임 오류 핸들링을 하지 않는 다면 동작중인 어플리케이션에서 예외가 발생 한다. 
  - 

### 2.1 Module

### 2.3 Injection

## 간단 정리

 어노테이션 프로세싱 기반 과 Service Locator 패턴이 각각 가지는 장, 단점은 명확 하다. 그 중 단점에 대해서는 무시할 수 없다. 개인적으론 아래 상황에 맞추어 각각 DI tool 을 선택 하 면 될거 같다. 

- 프로젝트의 크기  
  - 크기가 클 수록 Dagger2 가 좋음. 
- 예상되는 보일러 플레이트 코드의 양 
  - 반복적인 코드의 갯수가 많고 DI 로 인한 런타임 예외 핸들링에 대한 강구가 있다면 Koin 
  - DI 런타임 예외에 대해 모든 핸들링이 어려울 거 같으면 Dagger2
  
 위 예제에서 보았듯이 APT, JAVA 로 구성된 Dagger2 의 경우 보일러 플레이트 코드 는 어쩔 수 없다. 정확한 타입의 인스턴스를 제공 해야 하기 때문 에 Kotlin 과 같은 런타임에 강점을 보이는 inline + reified type 코드 를 사용 할 수 없어 큰 약점이 존재 한다. 하지만 오랜 시간동안 입증된 안정성은 절대 무시할 수 없다. 
 
 Koin 또한 낮은 러닝커브와 간단한 사용, 그리고 Kotlin 의 장점을 사용 할 수 있다는 점에 사용성이 매우 높다고 생각 된다. 하지만 Service locator 디자인 패턴에서 가질 수 있는 약점 인 런타임 중 주입 대상 인스턴스가 존재 하지 않을 경우에 대한 예외 떄문에 아무래도 걱정이 생길 수 있다. 하지만 




