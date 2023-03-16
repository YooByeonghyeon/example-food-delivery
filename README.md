![image](https://user-images.githubusercontent.com/487999/79708354-29074a80-82fa-11ea-80df-0db3962fb453.png)

# 예제 - 음식배달

## Event-Storming
![moel](https://user-images.githubusercontent.com/70205519/203257687-38bc9e6d-7b35-4e04-8525-1df16dfec77e.PNG)


## 서비스 시나리오

### 기능적 요구사항
1. 고객이 메뉴를 선택하여 주문한다.
1. 고객이 선택한 메뉴에 대해 결제한다.
1. 주문이 되면 주문 내역이 입점상점주인에게 주문정보가 전달된다.
1. 상점주는 주문을 수락하거나 거절할 수 있다.
1. 상점주는 요리시작때와 완료 시점에 시스템에 상태를 입력한다.
1. 고객은 아직 요리가 시작되지 않은 주문은 취소할 수 있다.
1. 요리가 완료되면 고객의 지역 인근의 라이더들에 의해 배송건 조회가 가능하다.
1. 라이더가 해당 요리를 Pick한 후, 앱을 통해 통보한다.
1. 고객이 주문상태를 중간중간 조회한다.
1. 주문상태가 바뀔 때 마다 카톡으로 알림을 보낸다.
1. 라이더의 배달이 끝나면 배송확인 버튼으로 모든 거래가 완료된다.

### 비기능적 요구사항
1. 장애격리
    1. 상점관리 기능이 수행되지 않더라도 주문은 365일 24시간 받을 수 있어야 한다  Async (event-driven), Eventual Consistency
    1. 결제시스템이 과중되면 사용자를 잠시동안 받지 않고 결제를 잠시후에 하도록 유도한다  Circuit breaker, fallback
1. 성능
    1. 고객이 자주 상점관리에서 확인할 수 있는 배달상태를 주문시스템(프론트엔드)에서 확인할 수 있어야 한다  CQRS
    1. 배달상태가 바뀔때마다 카톡 등으로 알림을 줄 수 있어야 한다  Event driven


## 체크포인트
1. Saga (Pub / Sub)
2. CQRS
3. Compensation / Correlation
    
### Saga(Pub/Sub)
![111](https://user-images.githubusercontent.com/70205519/203258591-92707d0f-fe0d-45e5-9b6f-4c950fff8610.PNG)
![222](https://user-images.githubusercontent.com/70205519/203258602-f696d34b-c7e6-4485-bc98-9643232b28e0.PNG)

### CQRS
![11](https://user-images.githubusercontent.com/70205519/203259654-9caac31c-fc62-4868-bbd0-9e91ea1d95cd.PNG)
![22](https://user-images.githubusercontent.com/70205519/203259705-d157b642-65c8-4b3b-85d1-215184d48f30.PNG)

### Compensation / Correlation
![서킷브레이커](https://user-images.githubusercontent.com/70205519/203258156-4f09181c-96ea-4d43-9442-16b3336df906.PNG)
