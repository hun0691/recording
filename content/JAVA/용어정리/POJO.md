---
title: "POJO 용어정리"
date: 2021-03-17T17:43:39+09:00
draft: true
---

## 1. Pojo

plain old java object

내가 알아본 POJO

  * plain old java object  (오래된 자바 오브젝트)

 POJO 는 다음과 같은것을 하면 안된다

 1. class extends
 2. interface implements
 3. Annotation 사용

 POJO 기반 코드
  1. 재활용 가능하고 반복적인 템플릿이 없는가 , OOP로 설계 되었는가

  2. 테스트에 용이한가


  궁금증
   엔터프라이즈 환경과 많은 기능을 구현함에 있어 100% POJO를 준수하긴 어렵다.
   그렇다면 POJO 기반으로 구축된 프레임웤 , 라이브러리는 어떻게 POJO 지향적으로 쓸수 있을까

   1. JPA
    -> JPA 구현을 위해서 JpaRepository를 상속 받아야 하는데 POJO 기반으로 작성하려면 어떻게 해야 할까 ?


진정한 POJO?

토비의 스프링에서는 진정한 POJO를 아래와 같이 정의했습니다.

그럼 특정 기술규약과 환경에 종속되지 않으면 모두 POJO라고 말할 수 있는가? 많은 개발자가 크게 오해하는 것 중의 하나가 바로 이것이다. ...(중략)... 진정한 POJO란 객체지향적인 원리에 충실하면서, 환경과 기술에 종속되지 않고 필요에 따라 재활용될 수 있는 방식으로 설계된 오브젝트를 말한다.
