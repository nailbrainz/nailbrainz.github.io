
fixed C 나 value matching 꼭 말하자

https://m.sosconhistory.net/2015/download/day28/ST3/S_28_1000_%EC%A1%B0%EB%A7%8C%EC%84%9D.pdf

중간 버퍼 크기도 설정 가능

### 커널의 개념 설명
- = 계산그래프는 어떻게 구축하는 거에요?
1. 노드
    - 메인 컨트롤: A72. 호스트. QNX / 계산은 c6x, c7x, r5f등의 타겟코어에서 이루어짐. TI-RTOS가 대기중
    - 호스트 사이드 (A72)에 노드호출 인터페이스 부분이 같이 컴파일되어야 함
    - 타겟 (C6X)사이드에서 계산노드 내용이 TIRTOS와 같이 빌드되고, tirtos 초기화 부분에 계산노드가 등록이 되어야 함
    - 호스트에서 메시지패싱 방식으로, param /data를 노드이름과 같이 넘김 - 타겟 tirtos에서 받아서 계산 후 돌려줌
    - 엣지: 노드 A(LDC)의 출력 이미지를 노드 B가 받는다고 치면, 


### 커널 메모리 (dsti to linker script)
- = 무슨 트러블슈팅을 하셨어요?
- 계산그래프 - 계산용 코어들은 DSP임. 각 dsp의 로컬 메모리는 디바이스 트리에 `reserved-memory`로 잡혀 있음. (reserve memory regions for special usage, excluding it from the usage of Linux kernel and making it available only for a custom device driver. T)
- TI는 .cmd파일에 링커 관련 설정 (http://software-dl.ti.com/ccs/esd/documents/sdto_cgt_Linker-Command-File-Primer.html) 가능. TIRTOS의 링커 설정도 고쳐주어야 함.
- 부팅때 device tree node 로딩


### 임베디드랑 값이 다를 때 어떻게 하는가?
- TI의 경우, x86 리눅스랑 EVM의 계산결과가 가끔 다름. 나는 안해봤으나 윈도우는 같다고 하고, sinf / cosf 등 함수의 구현이 문제임. lut table + taylor approx으로 해결 가능. 예전에 detection decoder를 floating c에서 fixed c 로 바꾸면서 이 방법을 써본 적 있음.


### 유럽연 c66으로 바꿀때 뭘 했지? 함 볼까


### 데이터 패킹

### TI Intrinsics
- 솔직하게 말하자. 다 끝낸 건 아니고 보는 중이라고.
- 내용 추가 요망