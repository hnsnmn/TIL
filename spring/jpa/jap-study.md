# JPA 그냥 막정리...


## 지연 로딩
* 지연 로딩: 객체가 실제 사용될 때 로딩


## 즉시 로딩
* 즉시 로딩: join sql로 한번에 연관된 객체까지 미리 조회

## Spring Data Rest

### 게시판


```java
public String toString(){
	retrun String.format("%s %s", getFirstName(), getLastName())
}
```


## JPA

### OneToMany

```java
@OneToMany(cascade = CascadeType.ALL, fetch = FetchType.LAZY, mappedBy = "user")
```
 * User 와 Cumstomer를 1:N 관계로 만들기 위해 @OneToMany 에너테이션
 * cascade = CascadeType.ALL을 설정하면 User에서 값이 지속되도록 하는 조작이나 삭제하는 조작 등 User에 가한 조작이 Customer에도 적용 됩니다. 예들들어 user를 삭제하면 관련 customer도 삭제 됩니다.


## Spring

### AOP

### DI

* DI의 목적이 어플리케이션간 결합도를 떨어트리는 것이 목표

### AOP
* 예외 처리, 로깅, 인증, 보안, 트랜잭션와 이에 영향을 받는 객체간의 결합도를 떨어트리는 것이다
* AOP는 횡단관심사를 모듈화 하는 프로그래밍 기법으로 공통적인 기능을 Aspect라 불리는 한곳에 정의한다.

* Logging은 시스템 내에서 거의 모든 경우에 적용하긴 하지만 특정한 비지니스 로직과는 전혀 관련이 없다. 만일 AOP 방식으로 구현한다면 실제 비니지르 로직의 구현을 담당하는 객체는 아무런 로그 관관 ㄲ체 정보가 없고 이 객체의 특정 메소드를 호출

## DDD