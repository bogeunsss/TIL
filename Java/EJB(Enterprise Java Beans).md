# EJB(Enterprise Java Beans)

> 개념

`EJB(Enterprise Java Beans)`, 기업 환경의 시스템을 구현하기 위한 서버 측 컴포넌트 모델이다. 일반적으로 업무 로직을 가지고 있는 서버 애플리케이션을 EJB라고 한다.

EJB(Enterprise Java Beans)는 독립한 부품이 아닌, 미국 Sun Microsystem사가 제창한 규약이다. EJB는 서버 애플리케이션의 개발을 용이하게 해 다중다양한 Platform과 제품간의 이동성을 실현하기 위하여 비즈니스 로직과 시스템 서비스를 이용하는 로직을 분산해 그 사이의 규약을 정하고 있다.

비즈니스 로직을 탑제한 부품을 `Enterprise Bean`이라고 한다. Database 처리, Transacion 처리등의 시스템 서비스를 이용한 로직을 감추고 있는 부품을 `Container`라고 한다.



> 등장 배경

서버 측에서 애플리케이션을 개발할 경우, 이하와 같은 문제가 있다.

```
종래의 애플리케이션에서 필요로 하는 비즈니스 로직 뿐만 아니라, 시스템 서비스를 이용한 Database 처리와 Transaction 처리의 프로그램이 필요하기 때문에 애플리케이션의 개발에 시간이 많이 소요된다.

각각의 애플리케이션 서버에서는 독자의 API가 제공되고 있기 때문에 각 사의 API를 사용해서 작성한 애플리케이션에는 이동성이 아니고 부품화가 곤란함
```

이같은 문제를 해결하고 서버 애플리케이션의 생산성 향상과 이동성을 실현하기 위해 생겨난 것이 EJB(Enterprise Java Beans)이다.



> EJB의 구성

■ **Enterprise Bean** 

비즈니스 로직을 실장하는 서버 컴포넌트이다.
Enterprise Bean에는 이하의 3가지 모델이 있다.

- <u>세션 빈(Session Bean)</u> : DB 연동이 필요 없음
- <u>엔티티 빈(Entity Bean)</u> 
  - DB의 데이터를 관리하는 객체
  - Insert(삽입), Update(수정), Delete(삭제), Select(조회)
  - DB 관련 쿼리는 자동으로 만들어지고 개발자는 고급 업무 처리에 집중할 수 있음
  - DB가 수정되면 코드 수정 없이 다시 배포(설정 문서 만들어서 복사)
- <u>메시지 구동 빈(Message-driven Bean)</u> : JMS로 빈을 날려줌

일반적으로는 클라이언트가 Session Bean을 불러 Session Bean이 Entity Bean을 부르는 것으로 DB에 접근을 행한다.

■ **Container**

EJB서버와 Enterprise Bean의 중간에 위치해 클라이언트 애플리케이션은 그 컨테이너를 경유해서 Enterprise Bean에 접근한다.
컨테이너가 데이터베이스 처리와 트랜잭션 처리등을 숨기기 위해 개발자와 그것들을 의미하지 않는 애플리케이션을 개발하는 것이 가능하다.

■ **EJB Server**

EJB 서버는 컨테이너를 관리해서 EJB로서 필요한 시스템 레벨의 서비스(데이터베이스 처리, 트랜잭션 처리 등)을 실현한다.

■ **Client application**

EJB에 준거한 클라이언트 애플리케이션이다.
Java Applet, Java Application, Servlet, Java Server Pages(JSP) 베이스의 애플리케이션이 있다.



> 장단점

■ **EJB의 장점**

- <u>인스턴스 풀링</u> : 객체를 미리 생성하여 메모리에 저장하고, 사용 준비 상태에 들어가도록 함. 많은 동시접속자에 대한 안정성을 지원
- <u>트랜잭션 처리</u> : 자동으로 컨테이너가 모든 처리 메소드에 대하여 트랜잭션을 처리해줌. 안정적인 데이터 조작 가능
- <u>퍼시스턴스 관리</u> : Beans의 상태를 메모리에서 사용여부에 따라 자동으로 활성화 / 비활성화를 실행해 관리
- FAT Client를 Thin Client로, n-tier(n 계층) 시스템을 구축할 수 있음
- Weblogic, Webspere 주로 사용. 국내에서는 제우스(Jeus) 사용
- EJB 컴포넌트들이 Loading 되어 활동하는 서버 측 프로그램. 컴포넌트의 생성 / 소멸 / 라이프 사이클 / 보안 / Threading 등의 서비스를 제공

■ **EJB의 단점**

- 객체지향적이지 않음
- 복잡한 프로그래밍 모델
- 특정 환경, 기술에 종속적인 코드
- 컨테이너 안에서만 동작할 수 있는 객체구조
- 자동화된 테스트가 매우 어렵거나 불가능
- 부족한 개발생산성, 이동성(portablity)



> 참고

- **EJB(Enterprise Java Bean) :** https://woongsin94.tistory.com/357
