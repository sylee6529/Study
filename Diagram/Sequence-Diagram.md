### 1. 구성요소

| 구성요소 | 표현방법 | 내용 |
| --- | --- | --- |
| 액터 | 사람모양 | 시스템으로부터 서비스를 요청하는 외부 요소 |
| 객체 | 네모상자 | 메세지를 주고받는 객체 |
| 생명선 | 점선 | 객체가 메모리에 존재하는 기간
객체 소멸(X)이 표시된 기간까지 존재함 |
| 실행 상자 |  | 객체가 메시지를 주고 받으며 구동되고 있음을 표현 |
| 메세지 | 화살표 | 객체가 상호 작용을 위해 주고 받는 메시지 (동기식 메시지는 채워진 화살표, 비동기식 메시지는 비워진 화살표) |
| 객체 소멸 | X 표시 | 해당 객체가 더 이상 메모리에 존재하지 않음 |
| 프레임 |  | 다이어그램의 전체 또는 일부를 묶어 표현 |

******************생명 선******************

- 액터나 객체(Object)가 얼마나 오래 존재하는지 나타내는 선

********************실행 상자********************

- 인스턴스가 다른 인스턴스와 상호작용할 때 작성

![생명선](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d091389f-77c8-49e0-96d7-038f87a2e765/Untitled.png)

생명선

![실행 상자](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/0fc4bb01-8546-4bc1-a6ef-31bad7a8140b/Untitled.png)

실행 상자

**********메시지**********

- 인스턴스 간 주고 받은 데이터

| 유형 | 표현 방법 | 내용 |
| --- | --- | --- |
| 동기 메시지 | —————▶️ | 동기적으로 메시지를 전송함 |
| 비동기 메시지 | ——————→ | 비동기적으로 메시지를 전송함 |
| 동기 반환 메시지 | ◀️- - - - - - - -  | 동기적으로 메시지 호출을 반환함 |
| 비동기 반환 메시지 | ← - - - - - - - -  | 비동기적으로 메시지 호출을 반환함 |

********************동기 호출********************

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/14a77da5-5501-4987-9005-5d493baf0ed4/Untitled.png)

************************비동기 호출************************

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b54fa99b-dfac-4b0d-b799-e4442d8dfb73/Untitled.png)

**********************자체 메시지**********************

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/839378e9-e517-425b-8b03-066a751dba83/Untitled.png)

- 참고 URL
    
    https://coding-factory.tistory.com/806