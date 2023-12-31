# OSI 7 Layers

### 왜 7개로 나눴는가?

- 통신이 일어나는 과정을 단계별로 구분함으로 추후 수정에 편리
- 서로 다른 하드웨어 및 소프트웨어를 사용하는 시스템 사이에서 월활한 통신을 추구

### 물리 계층

- 케이블, 허브와 같은 물리적 장치
- 단지 0과 1의 전기적 신호로 전송하는 역할만 수행
- 배달원

### 데이터 링크 계층

- 브릿지, 스위치
- 물리 계층으로 안전하게 정보를 전송하게 해준다.
- *MAC* 주소를 통해 통신하며 패킷을 프레임으로 쪼갠다.
- ARP 프로토콜이 여기서 적용된다.
- 배달원이 목적지까지 주소 적기

### 네트워크 계층

- 라우터, IP
- 어디로 갈지 경로를 설정한다.
- 라우터가 주로 경로 선택 및 물리적주소를 IP 주소로 변환
- 경로 뿐만 아니라 흐름 제어, 오류 제어 등도 수행
- ICMP 및 다양한 경로 알고리즘이 여기서 적용된다.
- 배달원에게 물건 주기 전에 집하원에서 주소 설정

### 전송 계층

- 게이트 웨이
- 논리적 연결을 담당한다.
- TCP : 신뢰성, 연결 지향적
- UDP : 비 신뢰성 비 연결성 실시간
    
    > **UDP vs TCP**
    > 
    - 두 프로토콜 모두 패킷을 한 PC → PC 사이의 `IP 프로토콜` 로 구분 되어 있지만 다르다!
    - **TCP의 전송**
        1. P2 님 계세요?
        2. 네~ P1님 보내셔도 되용~
        3. 보낼게요~
        4. 네 잘 왔어요.
    - **UDP의 전송**
        1. P2 보낼게
        2. P2 또 보낼게
    
    → **TCP** 는 신뢰성 있는 전송을 하지만 **UDP**는 신뢰성을 포기하는 대신에 속도를 채택한다.
    
    | TCP | UDP |
    | --- | --- |
    | Connection-oriented protocol(연결지향형 프로토콜) | Connection-less protocol(비 연결지향형 프로토콜) |
    | Connection by byte stream(바이트 스트림을 통한 연결) | Connection by message stream(메세지 스트림을 통한 연결) |
    | Congestion / Flow control(혼잡제어, 흐름제어) | NO Congestion / Flow control(혼잡제어와 흐름제어 지원 X) |
    | Ordered, Lower speed(순서 보장, 상대적으로 느림) | Not ordered, Higer speed(순서 보장되지 않음, 상대적으로 빠름) |
    | Reliable data transmission(신뢰성 있는 데이터 전송 - 안정적) | Unreliable data transmission(데이터 전송 보장 X) |
    | TCP packet : Segment(세그먼트 TCP 패킷) | UDP packet : Datagram(데이터그램 UDP 패킷) |
    | HTTP, Email, File transfer에서 사용 | DNS, Broadcasting(도메인, 실시간 동영상 서비스에서 사용) |
    
    TCP의 자세한 정보는 다음 장에서…
    

### 세션 계층

- API, Socket
- 세션을 구축하고 유지하며 관리한다.
- TCP/IP 세션을 만들고 없애는 책임
- 통신 방법 결정 (Half Duplex인지 Full Duplex인지)
    - Half Duplex : 양방향 통신은 가능하지만 동시 전송은 불가 → 무전기와 같네?
    - Full Duplex : Half Duplex + 동시 전송 → 대역폭을 많이 먹어용’

### 표현 계층

- 수신자가 읽을 수 있도록 JSON, XML 같은 형태로 인코딩 기능을 제공
- 암호화도 여기서 진행

### 응용 계층

- HTTP, DNS
- 일반적인 응용 서비스를 수행
- DB, Mail 등등..