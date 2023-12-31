# IPC

> Process간의 통신이 필요 할 때 커널이 지원하는 통신 수단
> 

*커널 : OS의 핵심적인 부분, 모든 부분에 기본적인 서비스 제공*

## IPC 종류

### 1. 익명 Pipe

- 한쪽 방향으로만 통신이 가능함
- 송수신 전부 하고 싶은 파이프가 2개 필요
- 간단하다!
- 부모 - 자식 간 프로세스 처럼 명확한 프로세스가 있을 경우 사용한다.

### 2. Named Pipe

- 전혀 모르는 프로세스들 사이의 통신에 주로 사용
- 익명 pipe의 확장 된 상태 어디에나 통신이 가능하다.
- 여전히 단방향 통신

### 3. Message Queue

- pipe → 데이터의 흐름, queue → 메모리 공간
- 여러 프로세스가 데이터를 쉽게 다룸

### 4. shared memory

- 데이터 그 자체를 공유하는 공간
- 프로세스간의 메모리 영역을 공유 해서 사용하도록 하는 공간
- 가장 빠르다!
- 메모리 맵핑까지 들어간다면 → **메모리 맵**으로 사용가능!

### 소켓

- 네트워크 소켓을 활용

이런 IPC 통신에 있어 데이터 동기화 및 보호를 위해 Semaphore, mutex를 사용