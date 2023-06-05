### DDD (Domain Driven Design)

- 비즈니스 Domain 별로 나누어 설계하는 방식
- 핵심 목표는 Loosly Coupling, High Cohesion
- Strategic Design과 Tactical Design이 있는데, **우리 프로젝트에서는 Tactical Design만을 적용한다.** (전략적 설계는 x)

- 용어
    - Bounded Context
        - 이에 따라 Model들의 역할과 책임이 달라짐
    - Aggregate
        
        ![image](https://github.com/sylee6529/Study/assets/68765200/eef11e94-6f81-4a31-9602-c8dffe294100)

        
        - Entity들을 대표하는 추상화 객체
        - Entity 간에 직접 소통하는 것이 아니라 Aggregate 간에 커뮤니케이션 하도록 설계한다.
    

****************Tactical Design****************

- 개발을 위한 구체적인 설계도
- Strategic Design 에서 설계한 각 sub domain 별 Domain model을 중심으로 설계한다

- 설계 방식 - Layered Architecture
    
    ![image](https://github.com/sylee6529/Study/assets/68765200/0a08b37d-9580-4618-953f-473b632a1116)
    
    Martin Fowler가 얘기하는 Layer구조
    

![image](https://github.com/sylee6529/Study/assets/68765200/409220f4-01f4-48ff-be08-726689379a5d)

- 크게 3가지로 구분
    - Application Layer: 주로 도메인과 Repository를 바탕으로 실제 서비스(API)를 제공하는 계층
    - Domain Layer: Entity, VO(Value Object)를 활용하여 도메인 로직이 진행되는 계층
    - Infrastructure Layer: 쉽게 말하면 외부와의 통신(ORM, DB, NoSql)을 담당하는 계층
    
    * Entity는 고유 식별자(primary key)를 바탕으로 객체의 정체성 부여
    
    * VO(Value object)는 상태(attribute)를 바탕으로 객체의 정체성 부여
    

- tactical design 결과물
    - UserStory
    - **Sequence diagram**
    - class diagram
    - **data diagram** (erd와 동일)
    - **api 명세서**
    
    (**bold 표시**는 우리 프로젝트에서 진행할 것)
    

- 참고 URL
    
    DDD 핵심만 빠르게 이해하기: https://happycloud-lee.tistory.com/94
    
    DDD란: https://huisam.tistory.com/entry/DDD
